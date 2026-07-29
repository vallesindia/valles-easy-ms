# Valles Management System

A single-file HR, payroll, and ERP web app for **Valles India Tech Services Pvt. Ltd.** — runs entirely in the browser, syncs to Google Drive, and requires no server or database.

Live app: `https://vallesindia.github.io/Valles-easy-ms/`

---

## What it does

| Module | Covers |
|---|---|
| **Staff** | Employee records, CTC-driven salary structuring, salary revision history, Payslips (Old/New Regime + flat-rate Contractor TDS), Compliance filings (TDS/EPFO/ESIC/PT) |
| **Transactions** | Enquiry, Quotation, PO, Proforma Invoice, Invoice, Credit Note, Delivery Note — multi-currency, GST-aware line items, Proforma → GST/Non-GST invoice consolidation for vessel billing |
| **Bills & Expenses** | Vendor bills, Statutory Payments, Salary/Wages, Inter-Bank Transfers — GST, RCM, TDS, PF/PT/ESIC deductions, Tally voucher tracking |
| **Parties** | Clients and sub-contractors directory |
| **Documents** | Registrations, licences, certificates, insurance — with expiry tracking |
| **Settings** | Company profile, statutory rules (PF/PT/tax slabs), Chart of Accounts, backup & data recovery |

## Data & Sync

- All data lives in the browser's local storage and syncs to a Google Drive folder (found by name, not by URL — so redeploying to a new hosting URL doesn't lose your data).
- Attachments (bill scans, documents, compliance files) upload as individual files in Drive, not embedded in the synced data — keeps local storage light.
- Multi-user aware: shows who else is currently active, and warns before overwriting someone else's more recent change to the same record.
- 5 rolling automatic backups in Drive, with per-module "Data Recovery" version history (Settings → Data Recovery).

---

## Deployment (GitHub Pages)

1. Create a public GitHub repository (this one).
2. Upload `index.html` to the repo root.
3. **Settings → Pages** → Source: *Deploy from a branch* → Branch: `main`, folder: `/ (root)` → Save.
4. GitHub will publish it at `https://<your-username>.github.io/<repo-name>/`.

## Google Drive Connection Setup

The app needs a Google OAuth Client ID to talk to Drive:

1. [Google Cloud Console](https://console.cloud.google.com) → APIs & Services → Credentials.
2. Create (or reuse) an **OAuth 2.0 Client ID** of type *Web application*.
3. Under **Authorized JavaScript origins**, add your GitHub Pages domain, e.g. `https://vallesindia.github.io` (domain only, no path — covers every repo hosted under that account).
4. In the app: **Settings → Google Drive Backup & Sync**, paste the Client ID, click **Connect**.

If moving the app to a new hosting URL with existing data already in Drive: just connect as normal — the app finds the existing data folder by name automatically, no manual restore needed.

## Local Development

No build step — it's a single static HTML file. Open `index.html` directly in a browser, or serve the folder with any static file server.

---

*Internal tool — not for public distribution.*
