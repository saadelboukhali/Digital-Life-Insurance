# Digital Life Insurance Platform Modernization & BI Analytics
### Business Analysis & Systems Architecture Portfolio

**Author:** Saad Elboukhali  
**Role:** IT Business Analyst  
**Domain:** InsurTech | Digital Life Insurance | Actuarial Pricing | Automated Underwriting | FinTech Payments | Business Intelligence

---

## 1. Project Overview

This portfolio project focuses on modernizing a traditional life insurance operation (Insura / SecureLife) into a fully digital, automated, and customer-centric insurance platform.

The project addresses inefficiencies in the traditional insurance application process, where customers relied on physical forms, agents manually collected supporting documents, and internal teams performed repetitive data entry and underwriting activities.

The proposed digital solution introduces an end-to-end insurance journey that allows customers to:

- Obtain instant life insurance premium quotations.
- Complete digital insurance proposal applications.
- Upload identity, financial, and medical documents.
- Receive automated underwriting decisions.
- Make premium payments through integrated payment gateways.
- Receive digitally generated insurance policy documents.
- Track policy status through a customer portal.

The project demonstrates the application of Business Analysis across requirements elicitation, functional specifications, Agile user stories, acceptance criteria, process modeling, UI wireframing, and executive Business Intelligence reporting.

**Main Objective:** Design a digital life insurance journey that reduces manual processing, improves underwriting efficiency, accelerates policy issuance, and provides management with actionable business insights.

---

## 2. Business Problem & Initial Assessment (As-Is)

Before modernization, the insurance company relied on a traditional paper-based application and policy issuance process.

### Existing Operational Challenges

The legacy process involved:

- Customers completing physical insurance proposal forms.
- Insurance agents collecting paper-based KYC and income documents.
- Imaging teams scanning and storing physical documents.
- Data-entry clerks manually entering application information into the Policy Administration System (PAS).
- Underwriters reviewing applications through manual workflows.
- Payment and policy issuance teams coordinating transactions and documentation separately.

### Key Business Problems

| Business Problem | As-Is Situation | Business Impact |
|---|---|---|
| Manual Proposal Submission | Customers completed physical application forms. | Slow onboarding and high customer drop-off. |
| Manual Document Collection | Agents collected and submitted physical KYC and income documents. | Document handling costs and validation delays. |
| Repetitive Data Entry | Employees manually entered applicant information into the PAS. | Increased processing time and data-entry errors. |
| Manual Premium Calculation | Premium quotations depended on actuarial calculations and manual intervention. | Delayed quotations and inconsistent processing. |
| Manual Underwriting | Applications required extensive human review. | Longer underwriting turnaround times. |
| Payment Processing Delays | Payment collection and policy issuance were handled through separate processes. | Delayed policy activation and customer communication. |
| Limited Business Visibility | Management relied on historical reports and disconnected datasets. | Difficulties monitoring sales, claims, and advisor performance. |

These challenges established the need for a more integrated digital insurance architecture.

---

## 3. Proposed Solution (To-Be Digital Architecture)

The proposed solution introduces an integrated digital insurance platform connecting the customer-facing application with the core insurance processing systems.

### End-to-End Digital Customer Journey

1. **Online Quotation:** Customers enter basic information to receive an instant premium estimate.
2. **Premium Calculation:** The Actuarial Pricing Engine calculates premiums based on age, smoking status, sum assured, and policy term.
3. **Digital Proposal Submission:** Customers complete a validated seven-step application and upload supporting documents.
4. **Automated Underwriting:** The Underwriting Engine evaluates applicant information and assigns a risk category.
5. **Underwriting Decision:** Low-risk applications follow Straight Through Processing (STP), while medium-risk applications are referred for manual review.
6. **Digital Payment:** Approved applicants pay their premiums through UPI, debit/credit cards, or Net Banking.
7. **Policy Issuance:** The Policy Administration System generates a unique policy number and activates the policy.
8. **Document Delivery:** The Document Management System generates and stores the PDF policy document.
9. **Customer Notification:** Automated email and SMS notifications confirm successful policy issuance.

### Systems Impacted

| System | Business Responsibility |
|---|---|
| Customer Portal / Mobile App | Digital quotations, application submission, document uploads, and policy tracking. |
| Actuarial Pricing Engine | Real-time premium calculation and risk-based pricing adjustments. |
| Automated Underwriting Engine | Applicant risk assessment, STP approval, and manual referral. |
| Policy Administration System (PAS) | Policy creation, activation, and lifecycle management. |
| Document Management System (DMS) | Secure document storage and PDF policy generation. |
| Payment Gateway | Digital premium collection and transaction verification. |
| Notification Service | Automated email and SMS communication. |

---

## 4. Core Functional Modules & Business Requirements

The functional specifications define four major business modules covering the complete digital insurance lifecycle.

### Module 1: Digital Proposal Submission

**Requirement:** FR-01 to FR-09  
**User Story:** US-01  
**Deliverable:** Digital Proposal Submission Flow and Wireframe.

The proposal submission module captures applicant information through seven structured application sections.

#### Key Functional Requirements

| Requirement | Description |
|---|---|
| FR-01 | Capture personal information, including name, DOB, gender, contact details, identification number, and residential address. |
| FR-02 | Capture policy details, including product type, policy term, sum assured, and premium frequency. |
| FR-03 | Capture nominee and appointee information. |
| FR-04 | Collect occupation, employer details, annual income, and financial proof. |
| FR-05 | Capture medical information, including height, weight, BMI, existing illnesses, and previous surgeries. |
| FR-06 | Capture lifestyle declarations, including smoking, alcohol consumption, and hazardous activities. |
| FR-07 | Support document uploads for identity, address, income, and medical records. |
| FR-08 | Validate mandatory application fields and document requirements. |
| FR-09 | Generate a unique Proposal ID and submit the completed application to the Underwriting Engine. |

#### Important Business Rules

**Nominee & Appointee Governance**

If the nominee is under 18 years of age, the application must require guardian/appointee information before submission.

Required information includes:

- Full Name.
- Relationship.
- Date of Birth.
- Mobile Number.
- Identity Proof.

**Document Validation**

The system must:

- Accept PDF, JPG, and PNG formats.
- Enforce a maximum file size of 5 MB per document.
- Validate mandatory documents.
- Prevent submission when required information is missing.

---

### Module 2: Actuarial Premium Calculation Engine

**Requirement:** US-02  
**Deliverable:** Actuarial Premium Calculation Engine Specification and Wireframe.

The pricing engine calculates insurance premiums in real time using applicant attributes and predefined actuarial pricing rules.

#### Mandatory Input Validation

The system validates:

- Applicant age: 18–70 years.
- Gender.
- Smoking status.
- Sum assured against the minimum eligibility threshold.
- Policy term: 1–40 years.

Invalid or missing information triggers field-level validation messages.

#### Actuarial Risk Loading Rules

**Age-Based Loading**

Additional premium adjustments apply when applicant age exceeds 50 years.

**Smoking Risk Loading**

Frequent smokers receive a 30% risk surcharge on the base premium.

**Sum Assured Adjustment**

Premium calculations incorporate proportional adjustments based on the requested coverage amount.

**Policy Term Adjustment**

The calculation engine applies the relevant pricing adjustment based on the selected policy duration.

#### Premium Calculation Formula

The proposed calculation logic is:

Final Annual Premium = Base Premium + Age Loading + Smoking Risk Loading ± Term Adjustment + Sum Assured Adjustment

Where:

Smoking Risk Loading = 30% of Base Premium for applicants classified as Frequent Smokers.

#### Customer-Facing Premium Breakdown

The pricing interface displays:

- Base annual premium.
- Age-related loading.
- Smoking-related surcharge.
- Policy term adjustment.
- Sum assured adjustment.
- Final annual premium.
- Semi-annual premium.
- Quarterly premium.
- Monthly premium.

The system also records calculation details for audit and traceability.

---

### Module 3: Automated Underwriting & Straight Through Processing (STP)

**Requirement:** US-03  
**Deliverable:** Automated Underwriting Engine Specification and Risk Routing Flow.

The underwriting engine evaluates submitted applications using predefined medical, financial, lifestyle, and actuarial rules.

Applications are classified into three risk categories.

#### Risk Classification & Decision Matrix

| Risk Category | Qualification Rules | System Action |
|---|---|---|
| Low Risk | Age 18–45, normal BMI, non-smoker, non-drinker, sufficient income, and no critical medical conditions. | Automatic approval through Straight Through Processing (STP). |
| Medium Risk | Minor medical conditions, coverage exceeding STP limits, casual smoking, or occasional alcohol consumption. | Referral to Senior Underwriter for manual review. |
| High Risk | Serious medical conditions, product eligibility violations, insufficient income, frequent smoking/drinking, or hazardous occupation. | Rejection or compliance investigation, subject to applicable underwriting rules. |

#### Underwriting Workflow

**Low-Risk Applications**

- Automatically evaluated against underwriting rules.
- Approved without manual intervention when all STP conditions are satisfied.
- Forwarded to the policy issuance workflow.

**Medium-Risk Applications**

- Routed to the Senior Underwriter workbench.
- Reviewed manually.
- Approved or rejected by an authorized underwriter.

**High-Risk Applications**

- Flagged for further assessment or rejection according to approved business rules.
- Relevant decision details recorded for audit purposes.

#### Compliance & Audit Requirements

The system records:

- Final underwriting decision.
- Applicant risk score.
- Triggered underwriting rule IDs.
- Decision timestamp.
- Manual review history.
- Responsible underwriter, where applicable.

Automated notifications are sent to the applicant, agent, operations team, and underwriter according to the workflow.

---

### Module 4: Payment Gateway Integration & Policy Issuance

**Requirement:** US-04  
**Deliverable:** Payment Gateway and Policy Issuance Specification, Swimlane Flow, and Checkout Wireframe.

This module manages premium collection, payment verification, policy generation, and customer notification.

#### Supported Payment Methods

- UPI.
- Credit Cards.
- Debit Cards.
- Net Banking.

#### Payment Processing & Error Recovery

The system supports:

- Secure payment gateway integration.
- PCI-DSS-aligned payment processing.
- Encrypted communication.
- Transaction verification.
- Bank error-code handling.
- Payment retry functionality.
- Prevention of policy generation following failed or unverified payments.

#### Automated Policy Issuance

After successful payment authorization:

1. The Policy Administration System generates a unique Policy Number.
2. The system compiles the policy document in PDF format.
3. The document includes customer, policy, nominee, and contractual details.
4. The PDF is stored in the Document Management System.
5. The policy status is updated to ACTIVE.
6. A confirmation email and SMS are dispatched.

**Example Policy Number:** `POL-2026-00847`

#### Omnichannel Customer Notifications

The Notification Service automatically sends:

- Policy issuance confirmation email.
- PDF policy document attachment.
- SMS confirmation.
- Policy identification number.
- Payment transaction reference.

---

## 5. Business Analysis Deliverables

This repository contains the complete Business Analysis documentation created to support the proposed digital insurance transformation.

### A. Requirements Elicitation & Stakeholder Documentation

**Directory:** `01_Elicitation_and_Requirements_Gathering/`

| File | Deliverable | Purpose |
|---|---|---|
| 01_Req_Gathering_Premium_Calculation.docx | Premium Calculation Elicitation | Captures actuarial pricing rules, risk loadings, and premium breakdown requirements. |
| 02_Req_Gathering_Automated_Underwriting.docx | Underwriting Elicitation | Defines low, medium, and high-risk categories and STP decision rules. |
| 03_Req_Gathering_Payment_and_Policy_Issuance.docx | Payment & Policy Issuance Elicitation | Documents payment methods, retry scenarios, policy generation, and PDF storage requirements. |

These documents demonstrate structured requirements gathering through stakeholder questions, business rule clarification, and functional requirement identification.

### B. Functional Requirements Document (FRD)

**Directory:** `02_Functional_Specifications_FRD/`

**File:** `04_FRD_Digital_Life_Insurance_Proposal_Submission.docx`

The FRD defines the functional behavior of the digital insurance platform.

It includes:

- Project objectives and scope.
- As-Is and To-Be process descriptions.
- Functional Requirements FR-01 to FR-09.
- Business rules and validation logic.
- Functional workflows.
- UI mockups and interface expectations.
- System integration requirements.
- Acceptance and validation criteria.

### C. Agile User Stories, Acceptance Criteria & Wireframes

**Directory:** `03_Agile_User_Stories_Flows_and_Wireframes/`

The project includes four detailed Agile user stories.

| User Story | Functional Module | Key Deliverables |
|---|---|---|
| US-01 | Digital Proposal Submission | User Story, AC1–AC9, Activity Flow, and 7-Step UI Wireframe. |
| US-02 | Actuarial Premium Calculation | User Story, AC-01–AC-08, Process Flow, and Calculator Wireframe. |
| US-03 | Automated Underwriting | User Story, AC1–AC8, Risk Routing Flow, and Underwriting Wireframe. |
| US-04 | Payment & Policy Issuance | User Story, AC1–AC10, Swimlane Flow, and Checkout Wireframe. |

Each user story includes structured acceptance criteria using business-oriented Given / When / Then scenarios.

The accompanying activity flows and wireframes illustrate the expected system behavior and customer interaction.

---

## 6. Executive BI Dashboard & Business Insights

**Directory:** `04_Executive_BI_Dashboard_and_Insights/`

The Business Intelligence deliverables analyze historical insurance performance, premium revenue, product distribution, advisor productivity, and claims processing.

### BI Deliverables

| File | Deliverable | Purpose |
|---|---|---|
| 09_BRD_Insurance_Performance_Dashboard.docx | BI Dashboard Requirements | Defines KPIs, chart specifications, and dashboard slicers. |
| 10_Executive_Deck_Insurance_Dashboard_Insights.pptx | Executive BI Presentation | Presents insurance revenue, product mix, claims performance, and business recommendations. |

### Executive KPI Summary

The historical insurance dataset produced the following business metrics:

| KPI | Result |
|---|---:|
| Total Policies Sold | 400 |
| Total Premium Collected | $1.13M |
| Total Active Claims | 95 |
| Total Claims Requested | $16.45M |
| Total Claims Approved & Paid | $7.32M |
| Claims Payout Ratio | 44.50% |
| Claims Processing Gap | $9.13M |

### Claims Performance Analysis

The analysis identified a significant difference between requested and approved claims.

- Total Claims Requested: $16.45M.
- Total Claims Approved and Paid: $7.32M.
- Difference: $9.13M.
- Claims Payout Ratio: 44.50%.

This gap highlights the need for improved claims workflow visibility, processing efficiency, and management oversight.

### Insurance Product Portfolio Mix

| Product | Portfolio Share |
|---|---:|
| Whole Life | 37.0% |
| Term Life | 33.5% |
| ULIP | 29.5% |

The product distribution provides management with visibility into customer demand and the composition of the insurance portfolio.

---

## 7. Strategic Business Recommendations

Based on the BI analysis, four key recommendations were identified.

### 1. Improve Claims Processing Efficiency

The $9.13M difference between requested and approved claims highlights an area requiring further investigation.

Recommended actions:

- Automate claims workflow routing.
- Improve claims status tracking.
- Identify bottlenecks in adjuster processing.
- Optimize claims team workload allocation.
- Monitor claims turnaround time through executive dashboards.

### 2. Promote High-Margin ULIP Products

ULIP was identified as an attractive product category in the portfolio analysis.

Recommended actions:

- Review product profitability and claims experience.
- Align advisor incentives with approved profitability measures.
- Improve customer segmentation.
- Monitor product performance through Power BI.

### 3. Review Term Life Underwriting Rules

Term Life represents a significant portion of the portfolio and requires closer monitoring of claims exposure.

Recommended actions:

- Review high sum-assured applications.
- Reassess underwriting referral thresholds.
- Monitor claims frequency and severity.
- Refine risk classification rules using actuarial guidance.

### 4. Scale Top Advisor Practices

The BI analysis identified Olivia Brown as a top-performing advisor.

Recommended actions:

- Review successful customer acquisition practices.
- Document effective client qualification techniques.
- Share proven sales approaches with Advisors 2, 3, and 4.
- Monitor conversion rates and premium generation across advisors.

---

## 8. Repository Structure

```text
life-insurance-ba-portfolio/
│
├── README.md
│
├── 01_Elicitation_and_Requirements_Gathering/
│   ├── 01_Req_Gathering_Premium_Calculation.docx
│   ├── 02_Req_Gathering_Automated_Underwriting.docx
│   └── 03_Req_Gathering_Payment_and_Policy_Issuance.docx
│
├── 02_Functional_Specifications_FRD/
│   └── 04_FRD_Digital_Life_Insurance_Proposal_Submission.docx
│
├── 03_Agile_User_Stories_Flows_and_Wireframes/
│   ├── 05_US01_Proposal_Submission_Flow_and_Wireframe.docx
│   ├── 06_US02_Actuarial_Premium_Calculation_Engine.docx
│   ├── 07_US03_Automated_Underwriting_STP_Engine.docx
│   └── 08_US04_Payment_Gateway_and_Policy_Issuance.docx
│
└── 04_Executive_BI_Dashboard_and_Insights/
    ├── 09_BRD_Insurance_Performance_Dashboard.docx
    └── 10_Executive_Deck_Insurance_Dashboard_Insights.pptx
