# PA Clock Integrity Dashboard

A free, browser-only dashboard that helps practices (and plans) prove **when each step of a prior authorization happened**, so they can meet compressed PA timeframes and defend every determination.

Built by **Mosaic Life Tech, LLC**.

## Why

Under the CMS Interoperability and Prior Authorization Final Rule (CMS-0057-F), impacted payers must decide standard requests within 7 calendar days and expedited requests within 72 hours. They must also give specific denial reasons, publicly report PA metrics, and stand up FHIR-based Prior Authorization APIs by **January 1, 2027**. Providers face a new Electronic Prior Authorization measure in Promoting Interoperability starting with the CY 2027 performance period. Many states set even shorter windows.

A determination is only as defensible as the organization's ability to show the clock. This app tracks the five clock events for every PA:

1. Request received / submitted
2. Information requested (RFI)
3. Response received / sent
4. Decision made
5. Notice sent / received

## Features

| View | What it does |
|---|---|
| **Dashboard** | Open PAs, at-risk and overdue counts, RFI responses due within 48 hours, on-time rate, average turnaround, clock integrity score, administrative denials, a deadline-sorted action queue, and a list of clock gaps |
| **PA log** | Search and filter every case; export to CSV |
| **Case editor** | The five timestamps, each with its system of record, source (system vs. manual/reconstructed), owner and detail. Shows the applied timeframe, due time, RFI due time and reconciliation status. The **audit trail** requires a reason whenever a saved timestamp changes |
| **Clock sheet** | A printable five-timestamp sheet for any case, with an automatic reconciliation check, gap and closure code. Use it for monthly clock audits |
| **Denials & appeals** | Specific denial reason, closure code (clinical vs. administrative), peer-to-peer date, appeal deadline countdown and appeal status |
| **Scorecard** | Approval, denial, on-time, turnaround, RFI rate, administrative denials, overturns and clock gaps, grouped by payer, program, owner or service |
| **ePA readiness** | A 24-item checklist covering clock capture, payer rules, Da Vinci CRD/DTR/PAS and the 2027 ePA milestones, denials and governance |
| **Settings** | Editable timeframes by program (standard, expedited, RFI response window, appeal window, pause during RFI), your name for the audit trail, JSON backup/restore, CSV import/export and sample data |

A **Provider / Payer** toggle switches the event wording and dashboard framing between the two perspectives.

## Privacy

- There is no server, no login and no analytics. Data is saved only in the browser's `localStorage` on the computer where it was entered.
- Use internal case numbers, **not patient names or member IDs**.
- Export a JSON backup regularly. Clearing browser data erases the workspace.
- For multi-user, shared or PHI-bearing use, host it behind your organization's controls or move to a backend that has a BAA.

## Timeframes: confirm before relying on them

Default rules are federal baselines as understood in 2026 and are editable in **Settings**:

| Program | Standard | Expedited | Basis |
|---|---|---|---|
| Medicare Advantage, Medicaid FFS & managed care, CHIP FFS & managed care | 7 calendar days | 72 hours | CMS-0057-F |
| QHP on federally-facilitated exchanges, commercial | 15 days | 72 hours | ERISA/ACA baseline; states vary |

The RFI response window (default 7 days), appeal windows and the "pause during RFI" option vary by state and contract. **Confirm every row for your state and programs.** This tool is an operational aid, not legal advice.

## Deploy on GitHub Pages

1. Create a new repository (for example `pa-clock-integrity`) and upload these files to the root: `index.html`, `app.js`, `styles.css`, `README.md`, `.nojekyll`.
2. Go to **Settings → Pages**, set **Source** to *Deploy from a branch*, and choose `main` / `(root)`.
3. The site will be published at `https://<your-username>.github.io/pa-clock-integrity/`.

To run it locally, open `index.html` in any modern browser. There is no build step and there are no dependencies.

## CSV import

The import accepts the same columns the app exports (`ref`, `payer`, `program`, …, `event1_ts`, `event1_system`, `event1_source`, …). Map an EHR or portal report to those headers to bulk-load cases. A row whose `ref` already exists updates that case.

## Roadmap ideas

- FHIR / Da Vinci PAS import (ClaimResponse timestamps) to remove manual entry
- Shared team workspace with authentication and role-based access
- State rule packs (pre-filled windows by state)
- Email/Teams alerts for at-risk cases

---
© Mosaic Life Tech, LLC. Operational and compliance-tracking aid only; not legal advice.
