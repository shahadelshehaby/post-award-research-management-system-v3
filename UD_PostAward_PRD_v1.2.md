# 🏛️ University of Dubai — Post-Award Research Management System (PARMS)
## Product Requirements Document · v1.0

---

> **Document Status:** Draft — For Review  
> **Version:** 1.2  
> **Date:** June 2026  
> **Prepared by:** Research Affairs  
> **Audience:** IT Dept  
> **Classification:** Confidential — Internal Use Only

---

## 📋 Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Problem Statement & Current-State Analysis](#2-problem-statement--current-state-analysis)
3. [Goals & Success Metrics](#3-goals--success-metrics)
4. [Stakeholders & User Roles](#4-stakeholders--user-roles)
5. [System Architecture Overview](#5-system-architecture-overview)
6. [Functional Requirements](#6-functional-requirements)
   - 6.1 [Module 1: Authentication & Profile Management](#61-module-1-authentication--profile-management)
   - 6.2 [Module 2: Project Onboarding & Auto-Fill](#62-module-2-project-onboarding--auto-fill)
   - 6.3 [Module 3: PI & Co-PI Project Management](#63-module-3-pi--co-pi-project-management)
   - 6.4 [Module 4: Purchase Requisition Form (PRF)](#64-module-4-purchase-requisition-form-prf)
   - 6.5 [Module 5: Research Assistant (RA) Hiring Workflow](#65-module-5-research-assistant-ra-hiring-workflow)
   - 6.6 [Module 6: Post-Interview Selection & Onboarding](#66-module-6-post-interview-selection--onboarding)
   - 6.7 [Module 7: PRF Closure & Expenditure Tracking](#67-module-7-prf-closure--expenditure-tracking)
   - 6.8 [Module 8: Smart Timeline & Automated Reminders](#68-module-8-smart-timeline--automated-reminders)
   - 6.9 [Module 9: Dashboards & Analytics](#69-module-9-dashboards--analytics)
7. [Non-Functional Requirements](#7-non-functional-requirements)
8. [Core Data Model](#8-core-data-model)
9. [GitHub Repository Structure](#9-github-repository-structure)
10. [Implementation Roadmap](#10-implementation-roadmap)
11. [UI/UX Design Guidelines](#11-uiux-design-guidelines)
12. [Creative & AI Enhancement Suggestions](#12-creative--ai-enhancement-suggestions)
13. [Risks & Mitigations](#13-risks--mitigations)
14. [Acceptance Criteria for Go-Live](#14-acceptance-criteria-for-go-live)
15. [Glossary](#15-glossary)
16. [Document Sign-Off](#16-document-sign-off)

---

## 1. Executive Summary

The University of Dubai (UD) manages a portfolio of externally funded research projects across four colleges — CEIT, DBS, CoL, and GUCR. Currently, post-award activities including project onboarding, resource procurement, Research Assistant (RA) hiring, budget tracking, and milestone monitoring are managed through a fragmented combination of emails, Excel spreadsheets, and paper forms. This results in missed deadlines, duplicated data entry, lack of accountability, and limited visibility for leadership.

The **Post-Award Research Management System (PARMS)** is a purpose-built, web-based platform that digitises, automates, and intelligently orchestrates the entire post-award lifecycle — from the moment a research award is announced to full project activation and ongoing expenditure monitoring.

> **Strategic Objective:** Centralise all post-award research operations into a single intelligent platform that eliminates manual coordination overhead, enforces institutional timelines, provides real-time budget visibility, and empowers PIs to manage their projects with confidence and compliance.

---

## 2. Problem Statement & Current-State Analysis

### 2.1 Current Workflow Pain Points

- **No central system:** Project data lives in disconnected Excel files managed by individual research officers with no version control or access management.
- **Manual PI notification:** Research Directors must manually email PIs after award announcements, with no formal tracking of whether PIs have acknowledged or acted.
- **Unstructured RA hiring:** RA hiring requests are submitted by email to HR with inconsistent information, causing delays and back-and-forth clarification cycles.
- **No hiring timeline enforcement:** There are no automated reminders to ensure hiring is completed within the expected 2-month window post-award.
- **PRF process opacity:** Faculty have no visibility into the status of their Purchase Requisition Forms once submitted. Procurement has no structured intake.
- **Budget tracking gap:** Actual expenditure against allocated budgets is not visible to PIs, research directors, or finance in real time.
---

## 3. Goals & Success Metrics

### 3.1 Primary Goals

1. Automate project onboarding from Excel upload to PI notification in under 10 minutes.
2. Digitise and enforce the full RA hiring workflow with structured forms, approvals, and notifications.
3. Provide a structured PRF process for equipment, conference attendance, software, travel, and other research expenditure categories.
4. Enforce the institutional post-award timeline through automated smart reminders and escalation alerts.
5. Give PIs, Research Directors, HR, and Procurement real-time visibility into project status, hiring progress, and budget consumption.
6. Maintain a fully auditable, immutable record of all project activities, decisions, and expenditure.

### 3.2 Success Metrics (KPIs)

| KPI | Baseline | Target (12 months post-launch) |
|---|---|---|
| Project onboarding time (award → PI access) | 3–5 working days | ≤ 1 working day |
| Average RA hiring cycle duration | ~90 days | ≤ 60 days |
| RA hiring requests with complete information on first submission | ~40% | ≥ 90% |
| PRF processing time (submission → procurement notification) | 7–14 working days | ≤ 9 working days (across 5 approval stages) |
| Budget visibility (time to get current spend data) | 2–5 days manual | Real-time, self-service |
| Timeline milestone compliance rate | ~50% | ≥ 85% |
| PI satisfaction score with post-award support | N/A | ≥ 4.2 / 5.0 |
| HR notification-to-job-post time | ~2 weeks | ≤ 5 working days |

---

## 4. Stakeholders & User Roles

### 4.1 Stakeholder Map

| Role | Access Level | Primary Responsibilities in PARMS |
|---|---|---|
| **Research Director** | Platform Owner | Upload project Excel file, enter project budget/award date/duration post-upload, oversee all projects across colleges, view executive dashboard, receive milestone alerts, manage system-wide notifications. Approve PRFs at Stage 2. |
| **Principal Investigator (PI)** | Project Lead | Access assigned projects, edit project details, add Co-PIs, submit PRF requests, submit RA hiring requests, follow up with HR, review candidates, confirm joining dates, confirm PRF outcomes at Stage 7. |
| **College Dean** | PRF Approver — Stage 1 | Review and approve PRFs submitted by PIs in their college. First-stage budget awareness check. |
| **VP of Academic Affairs** | PRF Approver — Stage 3 | Academic governance sign-off on PRFs after Research Director approval. |
| **UD President** | PRF Final Approver — Stage 5 | Final institutional approval with digital signature for all PRFs. |
| **Finance Department** | PRF Approver — Stage 4 | Budget availability confirmation; may adjust PRF line-item amounts before Presidential approval. Enter actual amount spent upon purchase completion (based on Procurement's purchase confirmation and invoices). |
| **HR Department** | Hiring Manager | Receive RA hiring requests, manage job posting process, record CV collection and interview scheduling, confirm candidate shortlist review, set and update actual joining dates. |
| **Procurement Department** | Expenditure Owner | Receive President-approved PRFs (Stage 6), manage purchasing process, confirm purchase completion to Finance for spend recording. |
| **System Administrator** | Platform Admin | Manage users, roles, college configurations, notification templates, timeline thresholds, audit logs. |

### 4.2 Role Permissions Matrix

| Action | Research Director | PI | College Dean | VP Academic Affairs | Finance | UD President | HR | Procurement | Admin |
|---|---|---|---|---|---|---|---|---|---|
| Upload project Excel | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |
| View all projects | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |
| Edit own project details | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |
| Add / remove Co-PIs | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |
| Cancel project | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |
| Submit PRF request | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Approve PRF — Stage 1 (Dean) | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Approve PRF — Stage 2 (Research Director) | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Approve PRF — Stage 3 (VP Academic Affairs) | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Approve PRF — Stage 4 (Finance) | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ |
| Approve PRF — Stage 5 (President) | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ |
| Process PRF — Stage 6 (Procurement) | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ |
| Confirm PRF outcome — Stage 7 (PI) | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Enter actual spend (Finance) | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ |
| Submit RA hiring request | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Manage RA hiring process | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ |
| Submit candidate shortlist | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Confirm joining date | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ |
| View budget dashboard | ✅ | ✅ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ✅ |

---

## 5. System Architecture Overview

### 5.1 Technology Stack Recommendations

| Layer | Technology / Approach |
|---|---|
| **Frontend** | React.js (TypeScript) with Tailwind CSS. Responsive design supporting desktop and tablet. Role-based UI rendering. |
| **Backend** | Node.js / Express.js REST API, or Django (Python) — to be confirmed with IT team. |
| **Database** | PostgreSQL — relational model for structured workflow chains, audit logs, and project data. |
| **Authentication** | OAuth 2.0 / SAML 2.0 integration with existing UD Active Directory / Microsoft 365 SSO. MFA enforced for all staff roles. |
| **File Storage** | Azure Blob Storage (or Supabase) for uploaded documents and Excel imports. Version-controlled with access logs. |
| **Email Service** | Microsoft Exchange integration or SendGrid for automated notification emails with deep-link tokens. |
| **Excel Parsing** | Server-side: `xlsx` (SheetJS) or `openpyxl` (Python) for structured column mapping from Research Director's Excel upload. |
| **Digital Signature** | DocuSign API integration (or Adobe Sign) for binding electronic signatures on PRF approvals and hiring confirmations. |
| **Hosting** | Azure Government / on-premise UD data centre per institutional policy. TLS 1.3 in transit, AES-256 at rest. |
| **Version Control** | GitHub (private repository under UD organisation). GitFlow branching strategy. |
| **CI/CD** | GitHub Actions for automated testing, linting, and deployment pipelines. |

### 5.2 High-Level Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                  React SPA (CDN / Azure Static)             │
│           Role-Based UI · Multi-Step Forms · Dashboards     │
└─────────────────┬───────────────────────────────────────────┘
                  │ HTTPS / JWT
┌─────────────────▼───────────────────────────────────────────┐
│              Node.js / Express REST API                     │
│  Auth · Project · PRF · Hiring · Timeline · Notification    │
└────┬────────────┬──────────────────┬───────────────────┬────┘
     │            │                  │                   │
┌────▼──────┐ ┌───▼───────┐ ┌───────▼──────┐ ┌──────────▼────┐
│PostgreSQL │ │Azure Blob │ │  Exchange /  │ │  DocuSign /   │
│(Primary + │ │  Storage  │ │  SendGrid    │ │  Adobe Sign   │
│Read Replica│ │(Documents)│ │  (Email)     │ │  (e-Sig)      │
└───────────┘ └───────────┘ └──────────────┘ └───────────────┘
```

> All tiers are deployed within UD's private VNET with WAF protection. The API layer is stateless with JWT token validation on every request. Database read replicas serve dashboard queries without load on the write primary.

---

## 6. Functional Requirements

---

### 6.1 Module 1: Authentication & Profile Management

#### FR-AUTH-001 — Single Sign-On
All users (UD faculty, staff, and HR/Procurement officers) must authenticate via UD's existing **Microsoft 365 SSO**. No separate password registration. All roles are provisioned by the System Administrator.

#### FR-AUTH-002 — Role-Based Access Control (RBAC)
- Each user is assigned exactly one primary role (see Section 4). Roles determine visible menu items, accessible records, and available actions.
- PIs can only view and manage their own assigned projects.
- HR can see only the RA hiring requests submitted for their processing queue.
- Procurement can see only PRF records assigned to their queue.
- Research Director has read access to all projects across all colleges.
- Admins have full read/write access to all records and configuration tables.

#### FR-AUTH-003 — User Profile Auto-Population
On first login, the system auto-populates the user profile from Active Directory:
- Full Name, Employee ID, College affiliation, Academic rank, Email address.
- User confirms and may supplement with phone number and ORCID (optional).

---

### 6.2 Module 2: Project Onboarding & Auto-Fill

#### FR-PROJ-001 — Excel Upload by Research Director

The Research Director uploads a structured Excel file (`.xlsx`) containing one or more new funded projects. The system parses the file and creates draft project records automatically.

**Required Excel Columns (exact mapping):**

| Column Header | System Field | Validation Rules |
|---|---|---|
| `Project Title` | `project.title` | Required. Max 300 characters. |
| `PI Name` | `project.pi_name` | Required. Must match an Active Directory display name for auto-linking. |
| `PI Email` | `project.pi_email` | Required. Must be a valid UD email (`@ud.ac.ae`) for internal PIs. |
| `PI Affiliation` | `project.pi_affiliation` | Required. Free text; auto-populated from AD if PI Email matches. |
| `Abstract` | `project.abstract` | Required. Min 100 characters. |
| `Category` | `project.category` | Required. ENUM: `Applied Research`, `Basic Research`, `Development`, `Interdisciplinary`. |
| `Primary Focus Area` | `project.focus_area` | Required. Free text (e.g. "Artificial Intelligence", "Renewable Energy"). |
| `College` | `project.college` | Required. ENUM: `CEIT`, `DBS`, `CoL`, `GUCR`. |
| `Allocated Budget (AED)` | `project.allocated_budget` | Required. Numeric. Min AED 1. |
| `Award Date` | `project.award_date` | Required. Date format: `DD/MM/YYYY`. Must not be in the future. |
| `Expected Duration (months)` | `project.duration_months` | Required. Integer. Min 1, Max 60. |

#### FR-PROJ-002 — Upload Validation & Error Handling
- Before importing, the system validates every row against the rules in FR-PROJ-001.
- If any row fails validation, the system displays a **row-by-row error report** with specific field names and the reason for failure. The Research Director must correct and re-upload.
- Successful rows are not blocked by failed rows in a multi-project upload — each row is independently assessed and the Research Director may choose to import valid rows immediately.
- Duplicate detection: if a project with the same `grant_reference` already exists, the system flags a warning and requires explicit confirmation to overwrite or create a new version.

#### FR-PROJ-003 — Project Reference Number Generation
Upon successful import, the system auto-generates a unique project reference in the format:

```
PARMS-[COLLEGE]-[YEAR]-[SEQUENTIAL NUMBER]
Example: PARMS-CEIT-2026-0007
```

This reference is displayed prominently in the system and included in all notification emails related to the project.

#### FR-PROJ-004 — PI Notification on Project Creation
Immediately after a project record is successfully created from the Excel upload:
- The PI receives an **automated email notification** containing:
  - Project title and reference number
  - A summary of auto-filled project fields for their review
  - A **direct deep-link URL** to the project record in PARMS
  - Clear call-to-action: "Review your project details and complete your project profile"
  - Contact details of the Research Director for queries
- The system logs the email dispatch timestamp.
- If the PI has not accessed the project within **3 working days**, an automated reminder email is sent.
- If the PI has still not accessed within **5 working days**, the Research Director receives an alert.

#### FR-PROJ-005 — Project Status Lifecycle

| Status | Description |
|---|---|
| `Onboarding` | Project created from Excel upload; PI has been notified but not yet reviewed the project. |
| `Active` | PI has reviewed and confirmed the project; post-award activities underway. |
| `Pending Hiring` | RA hiring request submitted; awaiting HR action. |
| `Hiring Complete` | RA(s) have joined; project fully staffed. |
| `In Progress` | Project work actively ongoing post-staffing. |
| `Closed` | All PRFs settled, final expenditure recorded, project concluded. |
| `Cancelled` | Project has been cancelled by the Research Director due to a funding withdrawal, institutional decision, or other issue. All open PRFs and hiring requests are automatically terminated. The cancellation reason is mandatory, logged in the audit trail, and visible to the PI and all active approvers. Cancelled projects are retained as read-only records and cannot be reactivated without Admin intervention. |

---

### 6.3 Module 3: PI & Co-PI Project Management

#### FR-PI-001 — Project Detail Review & Edit
Upon accessing their project via the deep-link, the PI is presented with a **pre-filled project profile form** drawn from the Excel upload. The PI may:
- Confirm all fields as correct (read-only confirmation).
- Edit the following fields if corrections are needed: Abstract, Primary Focus Area, PI Affiliation.
- **Note:** Core fields (Title, College, Allocated Budget, Award Date) may only be edited by the Research Director to preserve data integrity.

Any edits made by the PI are tracked with a timestamp and version history, and a notification is sent to the Research Director summarising the changes.

#### FR-PI-002 — Co-PI Management

Co-PI data is extracted directly from the project Excel file uploaded by the Research Director, as part of the initial project onboarding process (FR-PROJ-001). Co-PIs are not manually entered by the PI.

**Excel Columns for Co-PIs (repeating set per Co-PI, up to 5 Co-PIs per project):**

| Column Header | System Field | Validation Rules |
|---|---|---|
| `Co-PI Name (1–5)` | `project.copi[n].name` | Optional. Free text. |
| `Co-PI Email (1–5)` | `project.copi[n].email` | Optional. UD email (`@ud.ac.ae`) for internal; any valid email for external. |
| `Co-PI Affiliation (1–5)` | `project.copi[n].affiliation` | Optional. Free text (institution or college name). |
| `Co-PI Role (1–5)` | `project.copi[n].role` | Optional. ENUM: `Co-Investigator`, `Research Collaborator`, `Academic Advisor`. |

- Upon successful project import, the system auto-links internal Co-PIs (matched by UD email against Active Directory) and grants them project access automatically.
- External Co-PIs (non-`@ud.ac.ae` email) are flagged for the System Administrator to provision a guest account. Once provisioned, the external Co-PI receives a view-access email.
- All Co-PIs receive an automated email notification upon account linking, informing them they have been added to the project.

**Corrections & Updates:**
- The PI (or Research Director) may update a Co-PI's role label or remove a Co-PI from the **"Project Team"** tab after initial import if a correction is needed.
- Removing a Co-PI revokes their access immediately. All prior audit trail entries remain unchanged.
- Adding a new Co-PI not in the original Excel (e.g. a mid-project addition) follows the same Excel-first approach: the Research Director uploads an amended project record, or the System Administrator provisions the new Co-PI directly.

#### FR-PI-003 — Project Documents Repository
Each project has a **dedicated document repository** tab where PIs and may upload:
- Award letter / grant agreement
- Project proposal document
- Ethics approval (if applicable)
- Progress reports
- Other supporting documents (free-form category)

All uploads are versioned. Previous versions are retained and accessible. File types accepted: PDF, DOCX, XLSX, PNG, JPG. Maximum file size: 25 MB per file.

#### FR-PI-004 — Project Notes & Internal Log
Each project has a **Notes** section — a chronological internal log visible only to the project team (PI, Co-PIs, Research Director). PIs can add timestamped free-text notes. This provides an informal coordination space within the platform.

#### FR-PI-005 — Task Delegation (Research Director & PI)

Both the Research Director and PI may **delegate specific tasks or approval actions** to a nominated colleague within PARMS. Delegation is available for the following task types:

| Role | Delegatable Tasks |
|---|---|
| **Research Director** | PRF approvals (Stage 2), project milestone waiver sign-offs, PI access escalation reviews, any task currently pending their action. |
| **PI** | PRF submission initiation, RA hiring request submission, candidate shortlist submission, project detail confirmation. |

**Delegation Rules:**
- The delegating user selects a task (or a category of tasks for a defined period), nominates a delegate from the UD directory, sets an optional expiry date, and provides a mandatory reason (free text, min 20 characters).
- The delegate must be an active PARMS user with a role that is compatible with the task type (e.g. a PI cannot delegate to HR).
- The delegate receives an automated notification informing them of the delegated task(s), including scope, expiry, and a link to the relevant item(s).
- All actions taken by a delegate are recorded in the audit trail as: _"[Action] performed by [Delegate Name] on behalf of [Delegating User]"_ — the original user's accountability is preserved.
- The delegating user may revoke delegation at any time. Active delegations are displayed on the user's profile and on their dashboard in a **"My Delegations"** panel.
- Delegation does **not** transfer ownership of the project or hiring request; it grants temporary action authority only.
- The System Administrator can view and terminate any active delegation.

---

### 6.4 Module 4: Purchase Requisition Form (PRF)

#### FR-PRF-001 — PRF Initiation
PIs may submit a PRF from the **"Requests"** tab on their project page. Each PRF is linked to the parent project and inherits the project reference number.

A PRF reference number is generated in the format:
```
PRF-[PROJECT_REF]-[SEQUENTIAL_NUMBER]
Example: PRF-PARMS-CEIT-2026-0007-003
```

#### FR-PRF-002 — PRF Category Selection

The PI selects one of the following categories when initiating a PRF:

| Category | Description | Key Fields |
|---|---|---|
| **Equipment Purchase** | Lab equipment, computing hardware, instruments, devices. | Item name, Quantity, Unit cost (AED), Supplier name (optional), Technical specification, Justification. |
| **Conference Attendance** | Registration fees and associated travel. | Conference name, Dates, Location, Registration fee (AED), Travel estimate (AED), Accommodation estimate (AED), Acceptance letter upload. |
| **Software / Licenses** | Research software, analytical tools, database subscriptions. | Software name, Vendor, License type (perpetual/annual), Cost (AED), Number of seats, Justification. |
| **Travel & Accommodation** | Research-related travel not linked to a conference. | Destination, Travel dates, Purpose, Travel cost (AED), Accommodation cost (AED), Per diem estimate (AED). |
| **Training & Workshops** | Courses, professional training, workshops for RA or PI. | Training name, Provider, Location/Online, Dates, Fee (AED), Attendee name(s). |
| **Other** | Any research-related expense not covered above. | Description (min 100 characters), Estimated cost (AED), Justification. |

#### FR-PRF-003 — PRF Form Fields (Universal Section)

In addition to category-specific fields, all PRFs capture:

| Field | Description |
|---|---|
| **Requester** | Auto-populated from logged-in user profile. |
| **Project Reference** | Auto-populated from parent project. |
| **College** | Auto-populated from project record. |
| **Date of Request** | Auto-populated: current date. |
| **Estimated Total (AED)** | Auto-calculated from category-specific cost fields. |
| **Budget Available** | System-calculated: `Allocated Budget − Committed Spend − Pending PRFs`. Displayed in real time as fields are filled. |
| **Justification / Purpose** | Mandatory free-text field. Min 50 characters. |
| **Supporting Documents** | File uploads relevant to the request (e.g. quotations, acceptance letters, brochures). Quotation required for any single item ≥ AED 5,000. |
| **Urgency Flag** | Toggle: `Standard` (default) or `Urgent`. Urgent requests display a red badge in the approver queue. Requires justification if flagged Urgent. |

#### FR-PRF-004 — PRF Approval Workflow

PRF requests follow a strict **sequential multi-stage approval chain**. Each stage must be completed before the next is triggered. All approvers have access to the full PRF detail, project budget summary, and the complete audit trail of prior approvals.

| Stage | Approver | SLA Target | Actions Available |
|---|---|---|---|
| **1 — College Dean Review** | Dean of the PI's College (CEIT / DBS / CoL / GUCR) | 2 working days | Approve → Stage 2; Reject with reason; Return to PI for revision; Request additional information. |
| **2 — Research Director Review** | Research Director | 2 working days | Approve → Stage 3; Reject with reason; Return to PI for revision; Request additional documents. |
| **3 — VP of Academic Affairs** | VP of Academic Affairs | 1 working day | Approve → Stage 4; Reject with reason; Return with comments. |
| **4 — Finance Department** | Finance Department | 2 working days | Budget availability check; Approve → Stage 5; Partially approve or adjust amounts with justification; Reject with reason. |
| **5 — UD President** | UD President | 1 working day | **Final Approve** (digital signature captured) → Stage 6; Final Reject. |
| **6 — Procurement Department** | Central Procurement Team | Notified immediately upon Stage 5 approval | Receive PRF; initiate vendor engagement and purchasing process; update purchase status; attach purchase order; confirm purchase completion to Finance for spend recording. |
| **7 — PI Review & Confirmation** | Principal Investigator | 1 working day | Receives automated notification with procurement updates and finalised purchase details; may Accept, Request Modifications, or Add Comments/Clarifications before final PRF closure. |

> **Rationale for multi-stage PRF:** Research expenditure requires academic, budgetary, financial, and executive oversight before procurement execution. The Dean provides college-level budget awareness; the Research Director confirms research fund alignment; the VP provides academic governance sign-off; Finance confirms budget availability and may adjust amounts; the President gives final institutional authority; Procurement executes the purchase; and the PI confirms the outcome reflects their original intent.

#### FR-PRF-004A — Approver Actions (All Stages)

| Action | Description |
|---|---|
| **Approve** | Moves PRF to the next stage. Captures approver name, digital signature, timestamp, and optional comments. |
| **Reject** | Terminates the PRF workflow. PI receives notification with rejection reason. PRF is archived with status `Rejected`. |
| **Return for Revision** | PRF returned to PI with specific comments. PI may update and resubmit, restarting from Stage 1. Full revision history preserved. |
| **Request Information** | Approver posts a clarifying question to the PI without formally returning the form. Thread attached to the PRF record. Does not pause the SLA clock for other stages. |
| **Adjust Amount (Finance only)** | Finance may adjust line-item amounts with a mandatory explanation. Adjusted total is carried forward to Stage 5. |

#### FR-PRF-005 — SLA Monitoring for PRF

- At **50% of SLA elapsed**: automated reminder email sent to the current-stage approver.
- At **100% of SLA elapsed**: second reminder email sent + PRF flagged as **"Urgent"** (red) in the approver's dashboard queue.
- PI receives an automated notification at every stage transition (advance and return).
- Research Director receives a summary notification whenever a PRF in any project they oversee advances past Stage 4.

#### FR-PRF-006 — Budget Guard Rail
If a PRF's estimated total would cause the total committed spend (approved PRFs + this new PRF) to **exceed the allocated budget**, the system:
- Displays an **inline warning banner** to the PI before submission: _"Warning: This request would exceed your remaining project budget by AED X,XXX."_
- Does **not** block submission — the PI may proceed with a mandatory override justification (min 100 characters).
- Flags the PRF with a `⚠️ Over Budget` badge visible to all approvers throughout the chain.

#### FR-PRF-007 — Quotation Attachment
The PI or Procurement may attach vendor quotations directly to the PRF record at any stage. The system tracks whether a quotation is present and **requires at least one quotation for any single line item or total PRF value exceeding AED 5,000**. Missing quotations are flagged as a warning in the approver queue.

#### FR-PRF-008 — PRF Status Tracker

| Status | Description |
|---|---|
| `Draft` | PI has started but not yet submitted the PRF. |
| `Pending Dean` | Submitted; awaiting Stage 1 (Dean) approval. |
| `Pending Research Director` | Dean approved; awaiting Stage 2 (Research Director) approval. |
| `Pending VP Academic Affairs` | Research Director approved; awaiting Stage 3 (VP) approval. |
| `Pending Finance` | VP approved; awaiting Stage 4 (Finance) budget confirmation. |
| `Pending President` | Finance approved; awaiting Stage 5 (President) final approval. |
| `Approved — Sent to Procurement` | President signed; Procurement notified and actively processing. |
| `Pending PI Confirmation` | Procurement has completed purchase; awaiting Stage 7 PI confirmation. |
| `Completed` | PI confirmed; actual spend recorded; PRF fully closed. |
| `Rejected` | Rejected at any stage with reason documented. |
| `Returned for Revision` | Returned to PI for correction or additional information. |

---

### 6.5 Module 5: Research Assistant (RA) Hiring Workflow

#### FR-HIRE-001 — RA Hiring Request Submission by PI

PIs submit RA hiring requests from the **"Hiring"** tab on their project page. A project may have multiple simultaneous or sequential RA hiring requests.

A hiring request reference number is generated:
```
HIRE-[PROJECT_REF]-[SEQUENTIAL_NUMBER]
Example: HIRE-PARMS-CEIT-2026-0007-001
```

**RA Hiring Request Form Fields:**

| Section | Field | Details |
|---|---|---|
| **Position Details** | Job Title | ENUM: `Research Assistant`, `Research Fellow`. |
| | Type of Hiring | ENUM: `Full-Time` |
| | Number of Positions | Integer. Min 1. |
| **Engagement Details** | Proposed Hiring Date | Date picker. Must be within the project timeline. |
| | Contract Period | ENUM: `6 months`, `1 year`, `2 years`, `Project Duration`, `Other (specify)`. |
| **Job Description** | About the Project | Rich-text field |
| | Role Overview | Rich-text field |
| | Key Responsibilities | Rich-text field. Min 200 characters. Bullet points encouraged. |
| | Required Qualifications | Rich-text field. (Educational Background, Technical Skills, Soft Skills) |
| | Preferred Qualifications | Rich-text field. |
| | Why Join Us? | Rich-text field. Min 200 characters. Bullet points encouraged. |
| **Application Details** | Required Documents | Rich-text field. Min 200 characters. Bullet points encouraged. |
| | Expected Start Date | Free-text |
| | Location | Free-text |

#### FR-HIRE-002 — HR Notification on Hiring Request Submission

Immediately upon PI submission of an RA hiring request:
- The HR Department receives an **automated email notification** with:
  - Hiring request reference number
  - Project name and PI name
  - Position title, level, type, and number of positions
  - A **direct deep-link** to the full hiring request in PARMS
  - Expected hiring start date from the PI
- The request appears in the **HR Hiring Queue** dashboard with the submission timestamp.

#### FR-HIRE-003 — HR Workflow Actions

HR manages the hiring process directly within PARMS. The following status transitions and actions are available to HR:

| HR Action | System Effect | Notification Sent To |
|---|---|---|
| **Accept Request & Post Job** | Status → `Job Posted`. HR records: post date, URL of job posting on UD website. | PI notified: "Your RA position has been posted." |
| **Request Clarification** | Status → `Clarification Needed`. Message thread sent to PI. | PI notified with HR's question. |
| **Record CV Collection** | HR logs number of CVs received. Status → `CVs Under Review`. | PI notified: "X CVs received for your RA position." |
| **Schedule Interviews** | HR records interview dates and invites PI to interview panel. | PI receives calendar invite and notification. |
| **Confirm Interviews Complete** | Status → `Interviews Completed`. PI prompted to submit shortlist. | PI notified: "Please submit your candidate shortlist." |

#### FR-HIRE-004 — HR Follow-Up Reminders (PI-Initiated)

PIs may send a formal follow-up reminder to HR from within the system via a **"Send Reminder to HR"** button on the hiring request page. This:
- Logs the reminder timestamp in the audit trail.
- Sends a structured email to HR referencing the hiring request number, days elapsed, and the PI's request for an update.
- Limits: maximum one reminder per 3 working days (to prevent spam; system will display time remaining until next reminder is permitted).

---

### 6.6 Module 6: Post-Interview Selection & Onboarding

#### FR-SELECT-001 — Candidate Shortlist Submission by PI

After HR confirms interviews are complete, the PI accesses the **"Candidate Selection"** tab on the hiring request and submits a structured shortlist.

**Shortlist Submission Rules:**
- PI must submit **exactly 3 candidates** (or fewer only if fewer than 3 candidates were interviewed — PI must provide justification).
- For each candidate, the PI (and/or interview panel) completes a structured **Interview Evaluation Form** aligned with the official UD form (Ref: UD-HRD-TAR-FRM-002). The form captures:

**Section A — Candidate Information (auto-populated where available)**

| Field | Description |
|---|---|
| Candidate Full Name | Text field. |
| Candidate Email | Email field (for HR reference). |
| Interview Date | Date picker. |
| Position Applied For | Auto-populated from the hiring request. |
| Reports To | Auto-populated: PI name. |
| Interviewer(s) | Up to 3 interviewers — name fields; PI is Interviewer 1 by default. |

**Section B — Evaluation Criteria**

Each criterion is rated on a **1–5 scale**: 5 = Exceeds Requirements · 4 = Meets Requirements · 3 = Requires Some Development · 2 = Below Requirements · 1 = Does Not Meet Requirements. The Weighted Score is auto-calculated by the system using the formula: `(Rating ÷ 5) × Weight`.

| Criterion | Weight | Description |
|---|---|---|
| **Educational Background** | 15% | Candidate has the necessary academic qualifications and/or training required for the position. |
| **Work Experience** | 15% | Candidate's prior work experience is relevant to the position. |
| **Technical Skills** | 15% | Candidate demonstrates required technical knowledge and skills to perform successfully in the role. |
| **Teaching Skills** | 15% | Ability to effectively communicate, engage, and support students in classroom and/or online settings. Considers curriculum development, inclusivity, adaptability, and innovative delivery methods. |
| **Research Skills** | 15% | Ability to conduct high-quality research, analyse data, apply appropriate methodologies, and produce impactful publications or outputs. |
| **Generic / Soft Skills** | 15% | Includes confidence, sincerity, openness, communication, teamwork, leadership, problem solving, time management, supervision, and customer/student focus. |
| **Motivation for the Role** | 10% | Demonstrates enthusiasm, commitment, and clear motivation for the position and institution. |

- Each criterion has a **Comments** field (free text, optional) for the interviewer to add qualitative notes.
- The system auto-calculates the **Total Weighted Score (%)** by summing all weighted scores. The minimum passing score is **70%**.

**Section C — Employment Details**

| Field | Description |
|---|---|
| Notice Period | Free text (e.g. "Available immediately"). |
| Time to Join | Free text. |
| Current Salary — Basic / Allowance / Gross | Numeric fields (AED). May be entered as "N/A". |
| Expected Salary — Basic / Allowance / Gross | Numeric fields (AED). |
| Other Compensation / Working Condition Requests | Free text. Optional. |

**Section D — Overall Assessment & Recommendation**

| Field | Description |
|---|---|
| Overall Recommendation | ENUM: `Highly Recommended` · `Recommended` · `Requires Further Clarification` · `Not Recommended`. |
| Final Comments | Rich text. Optional. |
| Interviewer Signatures | Each interviewer listed in Section A must digitally sign the evaluation before submission. |

- PI **designates one candidate as the top choice** using a `⭐ Preferred Candidate` toggle. This designation is visible to HR but does not constitute a binding hiring decision — final hiring authority rests with HR following institutional policy.
- Any candidate whose Total Weighted Score falls below **70%** is automatically flagged with a `⚠️ Below Minimum Score` badge in the HR view. The PI may still include them in the shortlist but must provide a written justification.
- PI may attach the candidate's CV for each shortlisted candidate (PDF, max 5 MB each).

#### FR-SELECT-002 — HR Notification of Candidate Shortlist

Upon PI submission of the shortlist:
- HR receives an automated notification: _"PI [Name] has submitted a candidate shortlist for [Hiring Request Ref]. Review now."_
- The shortlist is visible to HR in the hiring request detail page, including the PI's preferred candidate designation.

#### FR-SELECT-003 — HR Hiring Confirmation & Joining Date

After HR completes the institutional hiring process (offer letter, contract, onboarding paperwork):

- HR updates the hiring request in PARMS by entering the **Actual Joining Date** of the selected RA.
- HR also records: selected candidate's name, contract type confirmed (Full-Time/Part-Time), and contract start/end dates.
- Status changes to `RA Hired — Joining Confirmed`.

#### FR-SELECT-004 — PI & Research Director Notification of Joining Date

Upon HR entering the Actual Joining Date:
- PI receives an **immediate automated notification**: _"Your Research Assistant [Name] is confirmed to join on [Date]. Project reference: [Ref]."_
- Research Director also receives a copy of this notification for portfolio visibility.
- The confirmed joining date is displayed prominently on the project dashboard with a **countdown timer** (e.g., "RA joins in 14 days").

#### FR-SELECT-005 — Project Status Auto-Update
When the first RA joining date is confirmed on a project, the project status automatically transitions from `Pending Hiring` → `Hiring Complete` (if all open hiring requests are filled) or remains `Pending Hiring` if additional positions are still outstanding.

---

### 6.7 Module 7: PRF Closure & Expenditure Tracking

#### FR-EXP-001 — Actual Spend Entry by Finance Department

When Procurement completes a purchase against an approved PRF, the **Finance Department** updates the PRF record in PARMS with the actual expenditure details:

| Field | Description |
|---|---|
| **Actual Amount Spent (AED)** | Numeric field. Required to close the PRF. Entered by Finance based on invoices and purchase confirmation received from Procurement. |
| **Purchase Order Number** | Optional reference for cross-referencing with ERP/finance system. |
| **Vendor / Supplier Name** | Text field. |
| **Date of Purchase** | Date picker. |
| **Proof of Purchase** | File upload: invoice or receipt (PDF, max 10 MB). Required. |
| **Finance Notes** | Free-text field for any relevant notes or budget coding references. |

PRF status changes to `Completed` upon Finance entry of actual spend. The PI receives an automated notification confirming the PRF has been closed with the actual amount recorded.

#### FR-EXP-002 — Budget Reconciliation Display

After each PRF is closed, the project's **Budget Summary** widget (visible to PI, Research Director, and Finance) automatically updates:

```
┌────────────────────────────────────────────────┐
│ PROJECT BUDGET SUMMARY                         │
│                                                │
│  Allocated Budget:          AED 250,000.00     │
│  Total Committed (Active):  AED  42,300.00     │
│  Total Spent (Closed PRFs): AED  85,700.00     │
│  ─────────────────────────────────────────     │
│  Remaining Balance:         AED 122,000.00     │
│                                                │
│  [████████████░░░░░░░░░░░]  51% Utilised       │
└────────────────────────────────────────────────┘
```

- **Allocated Budget:** Fixed from the Excel import.
- **Total Committed:** Sum of all PRFs in status `Approved — Sent to Procurement` or `In Procurement`.
- **Total Spent:** Sum of all `Completed` PRFs (actual amounts).
- **Remaining Balance:** `Allocated Budget − Total Committed − Total Spent`.

#### FR-EXP-003 — Budget Alert Thresholds

The system monitors budget utilisation and sends automated alerts:

| Threshold | Alert Type | Recipients |
|---|---|---|
| 75% of budget committed or spent | `⚠️ Budget Warning` email | PI + Research Director |
| 90% of budget committed or spent | `🔴 Budget Critical` email + in-system banner | PI + Research Director |
| 100% of budget committed or spent | `🚨 Budget Exhausted` email + all new PRFs blocked* | PI + Research Director |

> *PIs may still submit PRFs after 100% utilisation with an override justification, subject to Research Director approval. This is flagged with an `Over Budget` badge and requires explicit acknowledgement.

#### FR-EXP-004 — Expenditure Report Export
PIs and the Research Director may export a **full expenditure report** for any project at any time. The report includes:
- All PRFs (open and closed) with categories, estimated and actual amounts.
- A summary budget table (as displayed in FR-EXP-002).
- Chronological timeline of spend.
- Export formats: PDF (formatted, branded with UD logo) and Excel.

---

### 6.8 Module 8: Smart Timeline & Automated Reminders

#### FR-TL-001 — Institutional Post-Award Timeline

PARMS enforces the following standard post-award milestone timeline. All deadlines are calculated automatically from the project's **Award Date** (as recorded in the Excel upload). Each milestone triggers automated notifications when approaching and overdue.

| # | Milestone | Maximum Duration After Previous Milestone | Calculated Deadline | Description |
|---|---|---|---|---|
| **M1** | Award Announcement | Day 0 | = Award Date | Project created in PARMS; PI notified. |
| **M2** | Hiring Process Initiated | 14 calendar days from M1 | Award Date + 14 days | PI must have submitted at least one RA hiring request OR confirmed no RA is needed for this project. |
| **M3** | Hiring Process Completed | 60 calendar days from M1 (2 months total) | Award Date + 60 days | HR must have confirmed at least one RA joining date, OR PI has confirmed project does not require an RA. |
| **M4** | Project Start | 30 calendar days after M3 | M3 date + 30 days | PI confirms the project has formally started (first research activity begun). |
| **M5** | Progress Checkpoint | 30 calendar days after M4 | M4 date + 30 days | Status update: PI submits a brief progress note (min 200 characters) confirming hiring and project activation status. |
| **M6** | Decision Point | 30 calendar days after M5 | M5 date + 30 days | PI and Research Director jointly review: are corrective actions needed? PI submits a decision note. Research Director signs off. |

#### FR-TL-002 — Milestone Notification Schedule

For each milestone, the following automated notifications are sent:

| Trigger | Recipient(s) | Message Type |
|---|---|---|
| 7 calendar days before milestone deadline | PI | `⏰ Reminder: [Milestone Name] is due in 7 days.` |
| 3 calendar days before milestone deadline | PI | `⚠️ Urgent Reminder: [Milestone Name] is due in 3 days.` |
| 1 calendar day before milestone deadline | PI + Research Director | `🔴 Final Alert: [Milestone Name] is due tomorrow.` |
| Milestone deadline passed without completion | PI + Research Director | `❌ Overdue: [Milestone Name] has passed. Immediate action required.` |
| 7 calendar days after deadline (still incomplete) | PI + Research Director + System Admin | Escalation alert: project flagged for intervention. |

All notification emails include:
- Project title and reference number
- Milestone name and original deadline
- Days elapsed since deadline (if overdue)
- A direct deep-link to the project record in PARMS
- Contact details of the Research Director

#### FR-TL-003 — Timeline Visualisation

Each project detail page includes a **visual horizontal timeline** showing all 6 milestones with the following states:

- ✅ **Completed** (green, with completion date)
- 🔄 **In Progress** (blue, with days remaining)
- ⚠️ **At Risk** (amber, within 3 days of deadline)
- ❌ **Overdue** (red, with days overdue)
- ⬜ **Upcoming** (grey, not yet started)

Clicking any milestone on the timeline opens a detail panel showing: deadline date, completion date (if done), responsible party, associated actions, and notification history.

#### FR-TL-004 — Milestone Bypass / Waiver

The Research Director may mark any milestone as **"Not Applicable"** for a specific project (e.g., M2/M3 if the project does not require RA hiring). This requires:
- A mandatory justification note (min 100 characters).
- The milestone is then displayed as `N/A — Waived` on the timeline and does not trigger further reminders.
- The waiver is recorded in the audit log with the Research Director's identity and timestamp.

---

### 6.9 Module 9: Dashboards & Analytics

#### FR-DASH-001 — PI Dashboard

The PI's home page displays:

**My Projects Panel:**
- Card view of all assigned projects with: title, college badge, status indicator, allocated budget, % budget utilised, and next milestone due date.
- Filter by: College, Status, Year.
- Sort by: Award Date, Budget Size, Milestone Urgency.

**Quick Actions:**
- "New PRF Request" — launches PRF form for a selected project.
- "Submit RA Hiring Request" — launches hiring form.
- "Upload Document" — direct upload to project repository.

**Notifications Centre:**
- Chronological feed of all system notifications for the PI's projects.
- Filter: Unread Only, PRF Updates, Hiring Updates, Milestone Alerts.

**Budget At-a-Glance:**
- Compact budget bars for each project showing utilised vs. remaining.

#### FR-DASH-002 — Research Director Dashboard

**Portfolio Overview Panel:**
- Total active projects across all colleges (CEIT, DBS, CoL, GUCR).
- Projects by status (Onboarding, Active, Pending Hiring, Hiring Complete, In Progress, Closed).
- Total allocated budget across portfolio vs. total committed spend vs. total actual spend.

**Interactive Charts:**
- Projects by college (pie chart).
- Budget utilisation by project (horizontal bar chart, sorted by % utilised).
- Milestone compliance rate by college (stacked bar chart).
- Monthly PRF submission volume (line chart, last 12 months).

**Milestone Alerts Panel:**
- List of all overdue or at-risk milestones across all projects.
- Colour-coded: Red = overdue, Amber = at risk.
- One-click to navigate to the relevant project.

**PRF Approval Queue:**
- All PRFs pending Research Director approval (Stage 2), sorted by submission date.
- SLA colour coding: 🟢 Within SLA · 🟡 50–100% elapsed · 🔴 Overdue.
- Bulk approve functionality for standard requests (with individual override option).

**Pending Director Input Banner:**
- Prominently displays any projects awaiting the Research Director's budget/timeline entry following Excel upload.

**Export:** Full portfolio report as PDF or Excel at any time.

#### FR-DASH-003 — College Dean Dashboard

**PRF Approval Queue (Stage 1):**
- All PRFs pending Dean approval from PIs in their college, sorted by submission date.
- SLA colour coding: 🟢 Within SLA · 🟡 50–100% elapsed · 🔴 Overdue.
- Displays: PRF reference, PI name, category, estimated amount, urgency flag, budget remaining on project.

**College PRF Summary:**
- Total value of PRFs in flight (by stage) for the college in the current academic year.

#### FR-DASH-004 — VP of Academic Affairs Dashboard

**PRF Approval Queue (Stage 3):**
- All PRFs pending VP approval (post-Research Director sign-off), sorted by submission date.
- SLA colour coding, urgency flags, and one-click approve/return actions.

**Cross-College PRF Overview:**
- Summary of all PRFs in the approval chain by college and stage, for governance visibility.

#### FR-DASH-004A — Finance Department Dashboard

**PRF Approval Queue (Stage 4):**
- All PRFs pending Finance budget confirmation, sorted by submission date.
- Displays: estimated amount, project allocated budget, remaining balance, % utilised, over-budget flag.
- Finance may approve at stated amount or submit an adjusted amount with justification.

**Budget Commitment Summary:**
- Total committed spend across all projects, by college, for the current academic year.
- Comparison of approved vs. actual expenditure (from closed PRFs).

#### FR-DASH-004B — UD President Dashboard

**PRF Approval Queue (Stage 5):**
- All PRFs awaiting Presidential final approval and digital signature.
- Shows full approval history from all prior stages.
- One-click approve (with digital signature capture) or reject.

**Executive Portfolio Overview:**
- Total research expenditure approved YTD, by college.
- Count of active projects, open PRFs, and pending approvals at each stage.

#### FR-DASH-005 — HR Dashboard

**Hiring Requests Queue:**
- All open RA hiring requests across all projects, sorted by submission date.
- Filters: College, Status, Position Level, Contract Type.
- SLA indicator per request (based on M3 project milestone deadline).

**Status Summary:**
- Counts by status: New Requests, Job Posted, CVs Under Review, Interviews Scheduled, Awaiting PI Shortlist, Offer Pending, Hired.

**Overdue Hiring Tracker:**
- Projects where M3 (Hiring Complete) deadline is approaching or overdue, with days remaining/overdue.

#### FR-DASH-006 — Procurement Dashboard

**Active PRF Queue:**
- All PRFs in status `Approved — Sent to Procurement` (Stage 6 — President-approved).
- Grouped by college and project.
- Displays: PRF reference, category, estimated amount, Finance-confirmed amount, submission date, urgency flag.

**Pending PI Confirmation:**
- PRFs where purchase is complete and awaiting Stage 7 PI confirmation.

**Completed PRFs:**
- Searchable archive of closed PRFs with actual vs. estimated spend comparison.

**Budget Commitment Summary:**
- Total value of PRFs currently in procurement, by college.

#### FR-DASH-007 — System Administrator Panel

- **User management:** Add/edit/deactivate users, assign/change roles, manage external Co-PI guest accounts.
- **Workflow configuration:** Edit SLA thresholds, milestone durations, notification templates, budget alert thresholds.
- **Audit log viewer:** Searchable, filterable, and exportable log of all system events (who, what, when, old value, new value).
- **Excel template management:** Download and update the official project import template.
- **System health monitor:** Email delivery status, failed notifications, database backup status.

---

## 7. Non-Functional Requirements

### 7.1 Performance

- Page load time ≤ **2 seconds** for all primary views on a standard university network (100 Mbps).
- Dashboard data refresh ≤ **5 seconds**.
- Excel file processing (import, validation, project creation): ≤ **30 seconds** for up to 50 projects in a single file.
- Form auto-save completes within **1 second** of field blur.
- System supports minimum **150 concurrent users** without degradation.

### 7.2 Security & Compliance

- All data encrypted in transit (**TLS 1.3**) and at rest (**AES-256**).
- Role-based data isolation: PIs cannot access other PIs' projects.
- All file uploads scanned for malware before storage.
- Session timeout: **30 minutes** inactivity for all authenticated users. Warning shown at 25 minutes.
- Complete audit log retained for minimum **7 years**.
- Compliant with UAE data protection regulations (Federal Decree-Law No. 45 of 2021) and UD's Information Security Policy.
- OWASP Top 10 vulnerabilities addressed and verified by penetration testing prior to launch.

### 7.3 Availability & Reliability

- Target uptime: **99.5%** (excluding scheduled maintenance windows).
- Scheduled maintenance: Fridays 02:00–04:00 GST with minimum 48 hours advance notice to all users.
- Automated daily database backups with 30-day retention and tested restore procedure.
- Disaster recovery: **RTO ≤ 4 hours**, **RPO ≤ 1 hour**.

### 7.4 Usability & Accessibility

- Responsive design: fully functional on desktop (≥ 1024px) and tablet (768–1023px). Mobile: read-only status checking and notification review.
- **Arabic language support:** all UI text and email templates available in Arabic. RTL layout supported.
- **WCAG 2.1 Level AA** accessibility compliance.
- Inline contextual help text (`?` tooltip) for every form field.
- Progress indicator on all multi-section forms showing completion percentage.
- Browser support: Chrome, Firefox, Safari, and Edge (latest 2 versions).

### 7.5 Integrations

| Integration | Purpose | Phase |
|---|---|---|
| **Microsoft 365 / Active Directory** | SSO authentication, user profile auto-population, calendar invites for interview scheduling. | Phase 1 |
| **Email (Exchange / SMTP / SendGrid)** | All automated notification emails with deep-link tokens. | Phase 1 |
| **DocuSign / Adobe Sign** | Binding e-signatures for PRF approvals and hiring confirmations. | Phase 2 |
| **UD Website / HR Job Portal** *(future)* | Auto-push approved RA job postings to the UD careers page. | Phase 4 |
| **UD ERP / Finance System** *(future)* | Real-time budget availability and PO issuance integration. | Phase 5 |

---

## 8. Core Data Model

### 8.1 Key Entities

| Entity | Key Attributes |
|---|---|
| `users` | id, employee_id, full_name, email, role (ENUM), college_id, is_active, is_external, account_expiry (for guests), created_at, last_login |
| `colleges` | id, name, code (ENUM: CEIT/DBS/CoL/GUCR), dean_name |
| `projects` | id, reference_number, title, pi_user_id, college_id, abstract, category (ENUM), focus_area, allocated_budget, award_date, duration_months, funder_name, grant_reference, status (ENUM), created_by_user_id, created_at, updated_at |
| `project_copis` | id, project_id, user_id (nullable for external), external_name, external_institution, external_email, external_country, role_label (ENUM), added_by_user_id, added_at, removed_at |
| `project_documents` | id, project_id, document_type (ENUM), file_name, storage_path, version_number, uploaded_by, uploaded_at |
| `project_notes` | id, project_id, author_user_id, note_text, created_at |
| `prf_requests` | id, reference_number, project_id, requester_user_id, category (ENUM), justification, estimated_total (AED), actual_total (AED, nullable), urgency_flag (ENUM), status (ENUM), items (JSONB array of line items), over_budget_justification, created_at, updated_at |
| `prf_approvals` | id, prf_id, stage (ENUM), approver_user_id, action (ENUM: APPROVED/REJECTED/RETURNED), comment, signature_reference, timestamp |
| `prf_documents` | id, prf_id, document_type (ENUM), file_name, storage_path, uploaded_by, uploaded_at |
| `hiring_requests` | id, reference_number, project_id, pi_user_id, job_title (ENUM), level (ENUM), type (ENUM), num_positions, proposed_hiring_date, contract_period (ENUM), salary_band_aed, responsibilities, required_qualifications, preferred_qualifications, skills (JSONB array), language_requirements (JSONB), project_description, status (ENUM), created_at, updated_at |
| `hr_actions` | id, hiring_request_id, hr_user_id, action_type (ENUM), notes, job_post_url, num_cvs_received, interview_dates (JSONB), timestamp |
| `candidate_shortlists` | id, hiring_request_id, submitted_by_user_id, submitted_at, candidates (JSONB array: name, email, score, strengths, concerns, recommendation, is_preferred, cv_path) |
| `hiring_confirmations` | id, hiring_request_id, confirmed_by_user_id, selected_candidate_name, actual_joining_date, contract_start_date, contract_end_date, contract_type (ENUM), confirmed_at |
| `milestones` | id, project_id, milestone_number (1–6), milestone_name, deadline_date, completed_at, completed_by_user_id, completion_note, is_waived, waiver_justification, waiver_by_user_id, waiver_at |
| `notifications` | id, user_id, notification_type, entity_type, entity_id, message, is_read, created_at, email_sent_at |
| `audit_logs` | id, actor_user_id, action_type, entity_type, entity_id, old_value (JSONB), new_value (JSONB), ip_address, timestamp |

### 8.2 Key ENUMs

```sql
-- Project Status
CREATE TYPE project_status AS ENUM (
  'onboarding', 'active', 'pending_hiring', 'hiring_complete', 'in_progress', 'closed'
);

-- PRF Category
CREATE TYPE prf_category AS ENUM (
  'equipment', 'conference', 'software_license', 'travel_accommodation', 'training_workshop', 'other'
);

-- PRF Status
CREATE TYPE prf_status AS ENUM (
  'draft', 'pending_research_director', 'approved_sent_to_procurement',
  'in_procurement', 'completed', 'rejected', 'returned_for_revision'
);

-- Hiring Request Status
CREATE TYPE hiring_status AS ENUM (
  'submitted', 'clarification_needed', 'job_posted', 'cvs_under_review',
  'interviews_scheduled', 'interviews_completed', 'awaiting_shortlist',
  'shortlist_submitted', 'offer_pending', 'hired', 'cancelled'
);

-- Milestone Status (computed)
CREATE TYPE milestone_status AS ENUM (
  'upcoming', 'in_progress', 'at_risk', 'overdue', 'completed', 'not_applicable'
);
```

---

## 9. GitHub Repository Structure

### 9.1 Repository

```
github.com/university-of-dubai/post-award-research-management-system
```

### 9.2 Directory Layout

```
post-award-research-management-system/
│
├── README.md                          ← Project overview
├── docs/
│   ├── PRD.md                         ← This document
│   ├── architecture/
│   │   ├── system-diagram.png
│   │   └── database-erd.png
│   ├── api/
│   │   └── openapi.yaml               ← OpenAPI 3.0 specification
│   └── wireframes/
│
├── frontend/                          ← React (TypeScript) application
│   ├── public/
│   ├── src/
│   │   ├── components/                ← Reusable UI components
│   │   ├── pages/
│   │   │   ├── Auth/                  ← SSO login, profile setup
│   │   │   ├── Dashboard/             ← PI / Research Director / HR / Procurement
│   │   │   ├── Projects/              ← Project list, detail, documents, notes
│   │   │   ├── PRF/                   ← PRF creation, status tracker
│   │   │   ├── Hiring/                ← RA hiring request, shortlist, confirmation
│   │   │   ├── Timeline/              ← Milestone tracker view
│   │   │   └── Admin/                 ← System admin panel
│   │   ├── hooks/
│   │   ├── store/                     ← State management (Redux / Zustand)
│   │   ├── services/                  ← API call functions
│   │   ├── types/                     ← TypeScript interfaces
│   │   └── utils/
│   ├── tailwind.config.js
│   └── package.json
│
├── backend/                           ← Node.js / Express API
│   ├── src/
│   │   ├── routes/
│   │   ├── controllers/
│   │   ├── models/
│   │   ├── middleware/
│   │   │   ├── auth.middleware.ts
│   │   │   ├── rbac.middleware.ts
│   │   │   └── audit.middleware.ts
│   │   ├── services/
│   │   │   ├── projectImport.service.ts    ← Excel parsing & project creation
│   │   │   ├── prf.service.ts
│   │   │   ├── hiring.service.ts
│   │   │   ├── milestone.service.ts        ← Timeline computation & alerts
│   │   │   ├── budget.service.ts           ← Budget calculations & guards
│   │   │   ├── notification.service.ts
│   │   │   └── audit.service.ts
│   │   └── utils/
│   │       └── excelMapper.ts              ← Column-to-field mapping logic
│   └── package.json
│
├── database/
│   ├── migrations/                    ← Numbered SQL migration files
│   ├── seeds/                         ← Dev/test seed scripts
│   └── erd.png
│
├── infrastructure/
│   ├── terraform/                     ← Azure IaC scripts
│   └── nginx/
│
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md
│   │   ├── feature_request.md
│   │   └── security_vulnerability.md
│   └── workflows/
│       ├── lint.yml
│       ├── test.yml
│       ├── deploy-staging.yml
│       └── deploy-production.yml
│
├── tests/
│   ├── unit/
│   ├── integration/
│   └── e2e/                           ← Playwright end-to-end tests
│
└── scripts/
    ├── import-excel.js                ← CLI tool for bulk project import
    ├── seed-roles.js
    └── generate-test-data.js
```

### 9.3 Branching Strategy (GitFlow)

| Branch | Purpose |
|---|---|
| `main` | Production-ready code only. Protected — requires 2 approvals + passing CI before merge. |
| `develop` | Integration branch. All feature branches merge here first. |
| `feature/[ticket-id]-[description]` | Individual features. e.g. `feature/PARMS-42-excel-import` |
| `hotfix/[description]` | Critical production bug fixes. Branch from `main`, merge back to both `main` and `develop`. |
| `release/[version]` | Release preparation. Version bumps, changelogs, final QA. |

---

## 10. Implementation Roadmap

| Phase | Scope | Duration | Key Deliverables |
|---|---|---|---|
| **Phase 0** — Discovery | Requirements validation, stakeholder interviews, data model design, UX wireframes, Excel template finalisation, tech stack confirmation, ERD. | 3 weeks | Approved wireframes, ERD, finalised Excel template, signed-off PRD. |
| **Phase 1** — Foundation | SSO integration, user management (all 6 roles), database schema, Excel upload + validation + project creation, PI notification emails, project detail view, Co-PI management (internal). | 6 weeks | Working authentication, project import, PI notified on project creation, Co-PI add/remove. |
| **Phase 2** — PRF Module | PRF creation (all 6 categories), Research Director approval workflow, Procurement queue, budget calculation and guard rails, budget alert emails, PRF status tracker. | 5 weeks | End-to-end PRF workflow. Budget summary visible to PI and Research Director. |
| **Phase 3** — Hiring Workflow | RA hiring request form, HR notification and queue, HR workflow actions, PI follow-up reminders, candidate shortlist submission, HR joining date confirmation, PI/Research Director joining date notification. | 6 weeks | End-to-end RA hiring workflow. All notifications functional. |
| **Phase 4** — Timeline Engine | Milestone computation from Award Date, automated reminder schedule (7-day / 3-day / 1-day / overdue / escalation), timeline visualisation on project page, milestone waiver by Research Director. | 4 weeks | Smart timeline active on all projects. All reminder emails functional. |
| **Phase 5** — Dashboards & Analytics | PI dashboard, Research Director dashboard, HR dashboard, Procurement dashboard, Admin panel, export (PDF/Excel), expenditure report. | 4 weeks | All role dashboards live. Export functions working. |
| **Phase 6** — External Co-PI & Guest Access | Guest account provisioning workflow, external Co-PI access via email/password, time-limited token management. | 2 weeks | External Co-PI accounts fully functional. |
| **Phase 7** — UAT & Launch | User Acceptance Testing, bug fixes, performance tuning, penetration test, Arabic localisation, go-live. | 4 weeks | Production-ready system. User training completed across all colleges. |
| **Phase 8** — Post-Launch | Monitoring, feedback integration, UD website job portal push (auto-posting), ERP/Finance integration planning. | Ongoing | v1.1 enhancement releases. Integration roadmap. |

> **Total estimated timeline (Phases 0–7):** approximately **8–9 months** from project kick-off.
> **Assumed team:** 1 Project Manager · 2 Frontend Developers · 2 Backend Developers · 1 DevOps / QA Engineer.

---

## 11. UI/UX Design Guidelines

### 11.1 Design Principles

| Principle | Description |
|---|---|
| **Clarity first** | Every screen has one primary action. Status is always visible. No hidden or ambiguous buttons. |
| **Role-tailored interfaces** | Each user role sees only what is relevant to them. No information overload. Dashboards are purpose-built per role, not a generic view with filters. |
| **Trust through transparency** | PIs should never wonder "what is happening with my project?" The timeline, PRF tracker, and hiring status are always one click away. |
| **Smart defaults** | Auto-populate everything that can be computed. Reduce manual typing to the minimum. |
| **Proactive, not reactive** | The system surfaces upcoming deadlines, budget risks, and process bottlenecks before they become problems. |
| **Institutional identity** | Primary: UD Navy Blue `#1B3A6B`. Accent: UD Gold `#C8972A`. Professional aesthetic aligned with UD branding guidelines. |

### 11.2 Key Screens

1. Login page (SSO redirect; no password field for internal users)
2. PI Home Dashboard (project cards, budget bars, notification feed, quick actions)
3. Project Detail Page (multi-tab: Overview · Team · PRF Requests · Hiring · Documents · Notes · Timeline)
4. Project Onboarding Form (pre-filled from Excel; PI confirms or edits, with field-level version tracking)
5. Co-PI Management Tab (search UD directory, add external, remove, view current team)
6. PRF Creation Wizard (category selection → category-specific fields → review → submit)
7. PRF Status Tracker (per-project list of all PRFs with status badges and SLA indicators)
8. RA Hiring Request Form (multi-section: Position · Engagement · Job Description · Project Context)
9. Candidate Shortlist Submission (3-candidate structured form with preferred candidate toggle)
10. Timeline View (horizontal milestone tracker with status colours and click-to-detail)
11. Research Director Dashboard (portfolio overview, charts, alerts, PRF queue)
12. HR Hiring Queue (filterable list of all open hiring requests, SLA indicators)
13. Procurement PRF Queue (filterable PRF list, actual spend entry modal)
14. System Administrator Panel (users, config, audit log, templates)
15. Expenditure Report (project-level, with budget chart and PRF breakdown table)

### 11.3 Notification Email Template Standards

All system emails must include:
- UD logo and branded header (Navy `#1B3A6B`)
- Clear subject line with project reference and action required
- A concise 2–3 sentence summary of why the email was sent
- A prominent **CTA button** with a direct deep-link to the relevant record
- Footer: Research Affairs contact details · Unsubscribe from non-critical reminders (optional)
- Arabic version available via a language toggle link in the footer

---

## 12. Creative & AI Enhancement Suggestions

> These features go beyond digitising the current manual process and are recommended to make PARMS a strategic asset for research management at UD.

### 12.1 🤖 AI-Assisted Job Description Generator
When a PI fills in the RA hiring form, an **"AI Draft JD" button** sends the research area, required skills, and project description to an AI language model. The system returns a professionally formatted job description draft that the PI may edit and accept. This reduces PI effort significantly and produces more compelling job postings that attract better candidates.

### 12.2 📊 Budget Forecast Widget
For each project, a forward-looking widget estimates **projected end-of-project spend** based on:
- Current committed + spent amounts
- Average monthly spend rate
- Remaining PRFs in draft state
The widget flags if the project is on track to under-spend (a risk for funder compliance) or over-spend. PIs can use this to plan procurement timing strategically.

### 12.3 🔔 Smart Reminder Personalisation
Instead of generic system emails, the reminder engine analyses each PI's behaviour:
- PIs who typically act within 1 day receive fewer reminders.
- PIs who have a history of acting only after escalation receive an earlier first reminder.
- HR officers who are currently processing a high volume of requests receive a consolidated digest rather than individual emails.

### 12.4 📋 Progress Checkpoint Templates
At Milestone M5 (Progress Checkpoint), rather than a blank free-text field, the system provides a **structured progress report template** with guided questions:
- Is the RA actively engaged? (Yes / No / Partially)
- Have initial project activities commenced? (Yes / No)
- Any blocking issues to report? (Free text)
- Budget utilisation on track? (Auto-populated with current figure)
- Any expected changes to project scope? (Yes / No + free text)
This produces consistent, comparable checkpoint reports across all projects — valuable for Research Director oversight and funder reporting.

### 12.5 🔗 QR Code on Project Approval Records
Exported expenditure reports and project summary PDFs include a **QR code** linking directly to the live project record in PARMS. This allows funding bodies or internal auditors to instantly verify project status without requesting a login.

### 12.6 📅 Microsoft Outlook Calendar Integration
- When an RA joining date is confirmed, a calendar event is automatically pushed to the PI's Outlook calendar: _"[RA Name] joins the team today — [Project Title]"_.
- Interview scheduling prompts HR to send calendar invites to PI interview panel members directly from within PARMS.
- Milestone deadlines optionally syncable to PI's Outlook calendar (opt-in per user preference).

### 12.7 📈 Research Portfolio Analytics (Research Director)
A dedicated **Research Intelligence** view (accessible to the Research Director) aggregates cross-project data into a strategic dashboard:
- Research activity by college and focus area over time.
- RA headcount by college (current and projected).
- Average time-to-hire across projects and colleges (benchmark for HR performance).
- Budget utilisation rates by funder category.
- This view directly feeds into UD's KHDA reporting and QS ranking submissions.

### 12.8 🔄 Smart Delegation for Research Director
The Research Director may configure an **auto-delegation rule** for PRF approvals:
> _"If I do not act within 1 working day, automatically delegate to [named deputy]."_
This prevents the PRF workflow from stalling during the Research Director's travel, leave, or high-workload periods.

### 12.9 📄 Auto-Generated Annual Post-Award Report
At the end of each academic year, PARMS **auto-generates a formatted PDF report**: "University of Dubai Annual Research Post-Award Report" containing:
- All active and closed projects by college
- Total research expenditure
- RA hiring statistics (positions created, filled, average time-to-hire)
- Milestone compliance rates
- PRF summary by category
This currently takes the research office several days to compile manually.

---

## 13. Risks & Mitigations

| Risk | Likelihood / Impact | Mitigation |
|---|---|---|
| Excel column naming inconsistencies across research officers | High / High | Provide a locked, versioned Excel template (including Co-PI columns). Enforce strict column header validation on upload. Provide a "Template Download" button in the UI. |
| PRF approval chain bottlenecks (7 stages — senior approver unavailability) | High / High | SLA monitoring with escalation at each stage. Smart delegation rules configurable per approver (FR-PI-005). Management dashboard makes per-stage bottlenecks visible. |
| Budget data accuracy (actual spend not entered promptly by Finance) | High / High | Automated reminder to Finance 5 working days after Procurement confirms purchase completion. Finance KPI dashboard shows open PRFs awaiting spend closure. |
| Low PI engagement with the system post-launch | Medium / High | PI walkthrough workshop at launch. Short video tutorials (under 3 minutes each). Designate a PARMS champion per college. First 3 months: parallel email notifications still sent, directing PIs to the system. |
| HR resistance to new workflow (disrupts existing practices) | Medium / Medium | Involve HR in UAT. Design the HR queue to be simpler than their current email inbox process, not more complex. Dedicated HR training session. |
| Active Directory / SSO integration delays | Medium / Medium | Begin SSO integration in Phase 0. Maintain email/password fallback for Phase 1 UAT. |
| Scope creep from stakeholders mid-build | High / Medium | Strict change control process. New features logged in GitHub Issues and deferred to Phase 8 unless critical. |
| Delegation misuse or unauthorised task transfer | Low / Medium | Delegation scope is task-specific; delegating user's identity is always preserved in the audit trail. Admin can view and revoke any active delegation. |
| External Co-PI access management complexity | Low / Medium | Guest accounts are time-limited and auto-expired. Admin receives 30-day advance expiry notice to renew or close. |
| Security breach or data leak | Low / High | Penetration testing pre-launch, MFA enforcement, role-based data isolation, WAF, monthly security reviews. |
| DocuSign / Adobe Sign licensing cost exceeds budget | Low / Medium | Evaluate open-source e-signature alternatives (e.g. Documenso) as contingency. |

---

## 14. Acceptance Criteria for Go-Live

The following criteria must all be met before production deployment:

- [ ] Research Director can upload an Excel file and have project records auto-created with correct field mapping, including Co-PI data extracted automatically.
- [ ] Validation errors in the Excel upload are reported row-by-row with specific field-level detail.
- [ ] PI receives an automated email notification with a deep-link immediately upon project creation.
- [ ] Internal Co-PIs are auto-linked from Active Directory and notified; external Co-PIs are flagged for Admin provisioning.
- [ ] PI can log in, review project details, confirm or edit permitted fields.
- [ ] Research Director can cancel a project with a mandatory reason; all open PRFs and hiring requests are terminated and PI is notified.
- [ ] Cancelled project is retained as read-only and a cancellation reason is recorded in the audit log.
- [ ] PI can submit a PRF across all 6 categories with the correct fields and validation.
- [ ] Budget guard rail displays a warning when a PRF would exceed the remaining budget.
- [ ] PRF routes correctly through all 7 stages: Dean → Research Director → VP Academic Affairs → Finance → UD President → Procurement → PI confirmation.
- [ ] Each PRF stage approver receives a notification with a direct deep-link when the PRF reaches their stage.
- [ ] Finance can adjust PRF line-item amounts; adjusted total is carried forward to the President stage.
- [ ] President approval captures a digital signature and immediately triggers Procurement notification (Stage 6).
- [ ] Finance enters actual amount spent after Procurement confirms purchase completion; project budget summary updates automatically.
- [ ] PI can confirm the PRF outcome at Stage 7, triggering final PRF closure.
- [ ] SLA reminders fire at 50% and 100% elapsed for each stage approver.
- [ ] PRF rejected at any stage terminates the chain and notifies the PI with the rejection reason.
- [ ] PI can submit an RA hiring request with all required fields.
- [ ] HR receives an automated notification upon hiring request submission and the request appears in the HR queue.
- [ ] PI can send a follow-up reminder to HR (with 3-working-day rate limit enforced).
- [ ] PI can submit a candidate shortlist using the UD Interview Evaluation Form fields (7 weighted criteria, employment details, overall recommendation).
- [ ] System auto-calculates Total Weighted Score per candidate; candidates below 70% are flagged with a warning badge.
- [ ] All interviewer digital signatures are captured before the shortlist can be submitted.
- [ ] HR can set an actual joining date, triggering notifications to PI and Research Director.
- [ ] Research Director and PI can create, view, and revoke delegations; delegated actions are recorded in the audit trail with "on behalf of" attribution.
- [ ] All 6 milestones are correctly calculated from the project Award Date.
- [ ] Automated reminders are sent at 7-day, 3-day, 1-day, and overdue triggers for each milestone.
- [ ] Research Director can waive a milestone with a logged justification.
- [ ] Timeline visual correctly shows all milestone statuses with correct colour coding.
- [ ] All role dashboards (PI, Research Director, College Dean, VP Academic Affairs, Finance, UD President, HR, Procurement) display correct real-time data.
- [ ] Expenditure report exports correctly as both PDF and Excel.
- [ ] All notification emails contain the project reference number and a functional deep-link.
- [ ] Arabic language toggle is functional across all major views and email templates.
- [ ] Audit log records all create/update/delete events with actor identity and timestamp.
- [ ] Load test confirms system performance with 150 concurrent users.
- [ ] Penetration test report issued with **no Critical or High severity findings**.
- [ ] User Acceptance Testing sign-off obtained from: PI representative (one per college), Research Director, College Dean, VP of Academic Affairs, Finance Director, UD President's office, HR Director, Procurement Officer, and IT Director.
- [ ] All 6 milestones are correctly calculated from the project Award Date.
- [ ] Automated reminders are sent at 7-day, 3-day, 1-day, and overdue triggers for each milestone.
- [ ] Research Director can waive a milestone with a logged justification.
- [ ] Timeline visual correctly shows all milestone statuses with correct colour coding.
- [ ] All role dashboards (PI, Research Director, College Dean, VP Academic Affairs, Finance, UD President, HR, Procurement) display correct real-time data.
- [ ] Expenditure report exports correctly as both PDF and Excel.
- [ ] All notification emails contain the project reference number and a functional deep-link.
- [ ] Arabic language toggle is functional across all major views and email templates.
- [ ] Audit log records all create/update/delete events with actor identity and timestamp.
- [ ] Load test confirms system performance with 150 concurrent users.
- [ ] Penetration test report issued with **no Critical or High severity findings**.
- [ ] User Acceptance Testing sign-off obtained from: PI representative (one per college), Research Director, College Dean, VP of Academic Affairs, Finance Director, UD President's office, HR Director, Procurement Officer, and IT Director.

---

## 15. Glossary

| Term | Definition |
|---|---|
| **AED** | UAE Dirham — the currency used for all budget and expenditure values in PARMS. |
| **CEIT** | College of Engineering & Information Technology — one of UD's four colleges. |
| **DBS** | Dubai Business School — one of UD's four colleges. |
| **CoL** | College of Law — one of UD's four colleges. |
| **GUCR** | Gulf University Centre for Research — UD's dedicated research centre. |
| **Co-PI** | Co-Principal Investigator — a researcher who shares responsibility for a funded project alongside the PI. |
| **GitFlow** | A branching model for Git that defines a strict structure for project releases. |
| **HR** | Human Resources Department at UD. |
| **IEF** | Interview Evaluation Form — UD's standard weighted scoring form for evaluating RA candidates (Ref: UD-HRD-TAR-FRM-002). Used within PARMS for candidate shortlist submissions. |
| **KHDA** | Knowledge and Human Development Authority — Dubai's regulatory authority for higher education. |
| **M1–M6** | Milestone 1 through Milestone 6 — the six standard post-award timeline checkpoints enforced by PARMS. |
| **MFA** | Multi-Factor Authentication — an additional security step beyond password authentication. |
| **PARMS** | Post-Award Research Management System — the platform described in this PRD. |
| **PI** | Principal Investigator — the lead faculty member responsible for a funded research project. |
| **PRD** | Product Requirements Document — this document. |
| **PRF** | Purchase Requisition Form — UD's standard form for initiating a procurement request. |
| **RA** | Research Assistant — a staff member hired to support a funded research project. |
| **RBAC** | Role-Based Access Control — a security model where access is determined by assigned role. |
| **RPO** | Recovery Point Objective — maximum acceptable data loss in a disaster scenario. |
| **RTO** | Recovery Time Objective — maximum acceptable system downtime in a disaster scenario. |
| **SLA** | Service Level Agreement — the maximum time an actor should take to complete an action in the system. |
| **SSO** | Single Sign-On — one login credential (UD Microsoft 365) used across all UD systems. |
| **UAT** | User Acceptance Testing — formal testing by end users before production deployment. |
| **VNET** | Virtual Network — an isolated private network within Azure. |
| **WAF** | Web Application Firewall — a security layer that filters and monitors HTTP traffic. |

---

<div align="center">

**University of Dubai · Post-Award Research Management System · PRD v1.2**

*Confidential — Internal Use Only*

</div>
