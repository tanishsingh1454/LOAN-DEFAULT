
# 💳 **Loan Default Power BI Dashboard**

### 📊 Dashboard Overview

The **Loan Default Dashboard** provides insights into loan disbursement trends, borrower demographics, financial risk indicators, and default rates across multiple factors such as employment type, credit score, age group, and income bracket.
This analysis helps financial institutions understand **default patterns**, identify **high-risk borrower profiles**, and improve **loan approval and monitoring strategies**.

---

## 🎯 **Objectives**

* To analyze loan distribution and default rates by various borrower characteristics.
* To identify risk factors contributing to loan defaults.
* To evaluate how employment, credit score, age, and income impact loan repayment.
* To monitor year-on-year (YOY) changes in loan amounts and default counts.

---

## ⚙️ **Steps Followed**

### Step 1 – Data Loading

* Imported loan dataset (CSV/Excel) into **Power BI Desktop**.
* Dataset included details like: *Loan ID, Applicant Age, Employment Type, Credit Score, Loan Amount, Loan Purpose, Default Status, Income, Marital Status, Education,* and *Dependents.*

### Step 2 – Data Cleaning

* Opened **Power Query Editor** to:

  * Remove null or duplicate entries.
  * Standardize column names.
  * Ensure data types (numeric, date, text) were correctly assigned.

### Step 3 – Data Transformation

* Created calculated columns and measures for:

  * **Default Rate (%)**
  * **YOY Loan Change**
  * **Total Loan Amount by Credit Score and Income Level**

### Step 4 – Dashboard Design

* Multiple pages were created:

  1. **Loan Default & Overview**
  2. **Applicant Demographics & Financial Profile**
  3. **Financial Risk Metrics**

Each page used filters for **Year, Employment Type, Credit Score, and Income Bracket.**

---

## 🧮 **Key DAX Measures**

```DAX
-- Total Loan Amount
Total Loan Amount = SUM(Loans[LoanAmount])

-- Default Rate (%)
Default Rate (%) = 
DIVIDE(
    COUNTROWS(FILTER(Loans, Loans[LoanStatus] = "Default")),
    COUNTROWS(Loans)
) * 100

-- YOY Loan Amount Change
YOY Loan Change = 
([Total Loan Amount] - CALCULATE([Total Loan Amount], DATEADD(Calendar[Date], -1, YEAR))) /
CALCULATE([Total Loan Amount], DATEADD(Calendar[Date], -1, YEAR))

-- Average Income by Employment Type
Avg Income = AVERAGE(Loans[AnnualIncome])

-- Loan by Credit Score Category
Loan by CreditScore = 
CALCULATE([Total Loan Amount], ALLEXCEPT(Loans, Loans[CreditScoreCategory]))
```

---

## 📈 **Insights**

### 🏦 **Loan Overview**

* **Average Loan Amount:** ~127K
* **Highest Loan Amount Purpose:** *Home, Business, and Auto Loans* each contributing ~6.5B.
* **Default Rate (Overall):** ~11.6% (2013–2018).

---

### 👔 **Employment Type Insights**

| Employment Type | Average Income | Default Rate (%) |
| --------------- | -------------- | ---------------- |
| Full-time       | 82,890         | 3.01             |
| Self-employed   | 82,272         | 2.86             |
| Part-time       | 82,389         | 2.36             |
| Unemployed      | 82,447         | **3.39**         |

🔹 *Unemployed borrowers show the highest default rate, while part-time employees have the lowest.*

---

### 👶 **Age Group Insights**

| Age Group         | Avg Loan (₹) | Default Rate (%) |
| ----------------- | ------------ | ---------------- |
| Teens             | 127,459      | 11.5             |
| Adults            | 127,901      | 11.6             |
| Middle Age Adults | 126,674      | 11.7             |
| Senior Citizens   | 127,355      | 11.5             |

🔹 *Adults and Middle-Age groups show slightly higher default ratios.*

---

### 🧾 **Credit Score Analysis**

| Credit Category | Median Loan (₹) |
| --------------- | --------------- |
| High            | 127,764         |
| Medium          | 127,149         |
| Low             | 128,397         |
| Very Low        | 127,515         |

🔹 *Applicants with Low Credit Scores have higher loan amounts, suggesting riskier approvals.*

---

### 👩‍💼 **Demographic Analysis**

* **Marital Status:** Married and Single applicants each represent ~8.4% of total high-credit loans.
* **Education:** Most borrowers are *Bachelor’s degree holders (64K)*, followed by *High School* and *Master’s graduates.*

---

### 📉 **Financial Risk Metrics**

* **YOY Loan Amount Change:** Fluctuates between +1.7% (growth) and -1.5% (decline).
* **YOY Default Loan Change:** Highest increase in **2015 (+2.7%)**, lowest in **2016 (-2.8%)**.
* **High Income Bracket Loans:** 32.58B total, compared to 21.73B (Medium) and 7.21B (Low).

---

## 📊 **Visualization Summary**

**Page 1 – Loan Default Overview**

* Bar Chart: Loan Amount by Purpose
* Line Chart: Default Rate by Year
* Card Visuals: Total Loan Amount, Default %, Avg Income

**Page 2 – Applicant Profile**

* Donut Chart: Loan Distribution by Credit Score Category
* Matrix: Average Loan by Age Group and Marital Status
* Bar Chart: Number of Loans by Education Level

**Page 3 – Financial Metrics**

* Line Chart: YOY Loan Amount and Default Trends
* Bar Chart: Loan by Income Bracket
* Clustered Chart: Loan by Employment Type

---

## 🛠️ **Tools & Technologies**

| Tool                 | Purpose                          |
| -------------------- | -------------------------------- |
| **Power BI Desktop** | Dashboard Design & Data Modeling |
| **Power Query**      | Data Cleaning & Transformation   |
| **DAX**              | KPIs and Calculations            |
| **Excel/CSV**        | Data Source                      |
| **Power BI Service** | Publishing and Sharing Dashboard |

---

## 🚀 **Outcome**

* Built an interactive dashboard visualizing **loan performance and risk metrics**.
* Helped identify **high-default risk groups** based on income, employment, and credit profiles.
* Provided **YOY trend insights** for data-driven policy adjustments.

---

## 🧠 **Future Enhancements**

* Integrate **Machine Learning Models** (Python + Power BI) for **default prediction**.
* Add **drill-through reports** for borrower-level details.
* Enable **real-time data refresh** via Power BI Service.
