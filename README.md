# Paid Media Specialist Portfolio — Clean Attribution (Google Ads + GA4 + GTM) — Sample

This repository contains **portfolio-style documentation** aligned with a Paid Media Specialist role focused on:
- Google Ads + Bing Ads optimization at scale
- “Clean attribution” from keyword → landing page → form → CRM entry
- GA4 + GTM implementation patterns
- Reporting via Looker Studio (or dashboard specs)

> Note: This is a process playbook + technical documentation sample (no client data).

---

## 1) Account Optimization Sprints (Weekly)
**Sprint cadence:** weekly (60–90 min review + action list)  
**Core checks:**
- Budget pacing + spend anomalies
- Search terms hygiene (negatives, intent alignment)
- Landing page alignment (message match)
- Lead quality feedback loop (CRM → campaign)
- Tracking integrity (UTMs/GCLID/params captured)

**Outputs:**
- Sprint notes
- Change log (what changed / why)
- KPI snapshot (CPL, CVR, lead quality indicators)

---

## 2) Clean Attribution Blueprint (Keyword → CRM)
### Data chain
1) User clicks ad (Google Ads/Bing)  
2) Landing page receives params (gclid/msclkid + UTMs)  
3) GA4 records session + events  
4) Form submit triggers GTM event  
5) Hidden fields write params into CRM payload  
6) CRM stores: source/medium/campaign/adgroup/keyword (where possible) + landing URL + timestamp

### Required fields (recommended)
- `gclid` (Google) / `msclkid` (Microsoft)
- `utm_source`, `utm_medium`, `utm_campaign`, `utm_content`, `utm_term`
- `landing_page_url`
- `referrer`
- `lead_id` (CRM)
- `event_time` (ISO)

---

## 3) GA4 Event & Naming Schema (Example)
**Events**
- `page_view`
- `view_content`
- `form_start`
- `form_submit`
- `call_click`
- `book_consult_click`

**Parameters**
- `form_id`
- `page_location`
- `traffic_source`
- `utm_campaign`
- `utm_term`
- `gclid`

**Conversion definition**
- Primary: `form_submit`
- Secondary: `call_click`, `book_consult_click`

---

## 4) GTM Implementation Checklist (High Stakes Accounts)
- Ensure **GA4 config** fires once
- Use **Consent Mode** (if applicable)
- Capture URL parameters on landing
- Write params into hidden fields (form)
- Trigger `form_submit` event reliably (no duplicates)
- Test across browsers + mobile
- Validate in GA4 DebugView + Tag Assistant
- Validate CRM receives params correctly

---

## 5) Lead Quality Loop (Front-end → CRM)
**Daily checks**
- Spike in leads? Confirm source + landing page + keyword intent
- Drop in leads? Confirm form/phone tracking and budgets

**Weekly checks**
- Lead-to-consult rate by campaign
- Disqual reasons (if available)
- Keyword intent mismatches (negatives + ad copy adjustment)

---

## 6) Reporting Spec (Looker Studio)
**Executive view**
- Spend, Leads, CPL, CVR, booked consults (if tracked)

**Attribution view**
- Leads by campaign/adgroup/keyword (when available)
- Landing pages performance
- Device split + geo split

**Data integrity view**
- % leads missing UTMs
- % leads missing gclid/msclkid
- Duplicate event rate
- Form submit vs CRM lead count reconciliation

---

## Tools Mentioned
Google Ads, Microsoft Ads (Bing), Google Tag Manager, GA4, Looker Studio, Zoho CRM# paid-media-attribution-portfolio
