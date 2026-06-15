# Project: Core Banking Web Application Manual Testing
**Target Website:** [ParaBank by Parasoft](https://parabank.parasoft.com)  
**Tester:** Rahul Verma  

## 📌 Project Overview
This repository contains the end-to-end manual testing artifacts for **ParaBank**, a mock core banking application. The project focuses heavily on data integrity, transaction workflows, account ledger calculations, validation constraints, and discovering critical business logic failures.

## 📁 Repository Contents
* **ParaBank Test Plan.docx**: Outlines the strategic approach, testing types (Functional, Security, Negative, Data Integrity), entry/exit criteria, and scope.
* **ParaBank Test Cases, Test Scenarios and Bug Report.xlsx**: 
  * **Test Scenarios**: 14 high-level scenarios covering critical modules like Funds Transfer, Bill Pay, and Loan Request.
  * **Test Cases**: 21 exhaustive test cases mapped with actual execution results and Pass/Fail statuses.
  * **Bug Report**: Detailed logs of 6 highly critical business logic defects discovered during execution.

## 🛠️ Testing Types Performed
* **Functional Testing:** Core banking operations (Account opening, statement retrieval).
* **Data Integrity & Ledger Testing:** Verifying if account balances update accurately after debits and credits.
* **Negative & Boundary Value Testing:** Inputting non-numeric values, zero amounts, and testing overdraft constraints.
* **Security & Session Testing:** Validating authorization and checking direct URL access after logout.

## 🐛 Key Defects Identified (Sample from Bug Log)
During execution, multiple high-severity logical flaws were caught that break standard banking regulations:
1. **BUG_01 (Overdraft Enforcement Failure):** 'Transfer Funds' allows processing amounts greater than the available account balance without blocking or throwing an overdraft warning.
2. **BUG_02 (Unhandled Exception):** Inputting alphabetical characters in the 'Amount' field results in a raw backend crash (`500 Internal Error`) instead of a user-friendly validation message.
3. **BUG_04 & BUG_05 (Negative Bill Pay Vulnerability):** The 'Bill Pay' module accepts negative numbers (e.g., -$20), which anomalously *increases* the sender's account balance instead of deducting it.
4. **BUG_06 (Automated Loan Approval Bypass):** 'Request Loan' approves high-value loans even when a user inputs a `$0` down payment, bypassing basic credit validation.
