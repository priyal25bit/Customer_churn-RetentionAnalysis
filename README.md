# Churn Analysis & Customer Intelligence

## 1. The Business Challenge
In the hyper-competitive OTT landscape (Netflix, Hotstar, Prime), retention is the only way to survive. This project takes on the role of a Data Analyst tasked with identifying high-risk subscribers using a multi-dimensional dataset (Customer demographics, Subscription tiers, and Support escalations).

## 2. Core Tech Stack
- **SQL & Python Integration:** numpy, pandas, sqlite3, matplotlib, seaborn
- **Performance Engineering:** data cleaning, feature engineering, analytics
- **Behavioral Visualization**
- **Writing Actionable Insights**

## 3. Project Milestones
- **Relational Data Extraction:** Connecting Python to SQL databases to pull multi-table datasets.
- **Advanced Feature Engineering:** Data imports, calculating tenure, churn rates, and customer aging.
- **Executive Reporting:** Translating technical findings into billion-dollar business insights.

---

## Roadmap
- **Connect** SQL database to Python – `pandas` and `sqlite3`
- **Data import** using SQL query in Python – `pandas` and `sqlite3`
- **Data Cleaning** – `numpy` and `pandas`
  - Data types, rename cols, select specific cols, QCs, handle missing/null values
- **Feature Engineering** – `numpy` and `pandas`
  - Create new calculated cols, data transformation, use filters
- **Data Analysis** – `numpy` and `pandas`
  - EDA - aggregation, group by, pivot table
- **Data Visualization** – `matplotlib` and `seaborn`

---

## Churn Definition by Business

Churn analysis is the process of figuring out why customers stop doing business with you.

For this, we only need to look at three things:
- **"Who":** Identifying which customers left or will leave in future
- **"Why":** Analyzing their behavior before they left
- **"When":** Finding the "danger zone" – the point when a user leaves

| Business Type | Churn Definition |
|---|---|
| SaaS | Subscription canceled |
| E-commerce | No purchase in 90 days |
| Adtech | Using service/app in 90 – 120 days |
| Streaming | Membership inactive |
| Telecom | Account terminated |
| Banking | No transactions for X months |

---

## Database Tables

**Database:** `customer_churn`

**db_customer**
- customerid
- name
- country
- State
- gender
- dob
- interests
- pincode

**db_subscription**
- customerid
- subscription_start_date
- subscription_type
- renewal_date
- plan_type
- contract_type
- cancellation_date
- cancellation_reason
- monthly_charges
- cltv
- churn_score

**db_support**
- customerid
- complaint_date
- Escalations
- csat_score
- col_1
- comment

---

## Calculated Metrics

| KPI | Formula |
|---|---|
| Churn rate | churned customers / total customers |
| Churn by plan type | churn rate GROUP BY plan_type (Basic/Standard/Premium) |
| Churn by state | churn rate GROUP BY country, state |
| Retention rate | 1 − churn rate |
| ARPU | SUM(monthly_charges) / COUNT(active customerid) |
| Average customer tenure | AVG(DATEDIFF(cancellation_date OR NOW(), subscription_start_date)) |
| Revenue at risk | SUM(monthly_charges) WHERE churn_score > 70 |
| Escalation rate | SUM(escalations) / COUNT(complaints) × 100 |
| Avg complaints per customer | COUNT(complaints) / COUNT(DISTINCT customerid) |
| Correlation: escalations → churn | churn rate WHERE escalations ≥ 1 vs 0 |

---

## Insights

- **Churn Rate:** 28.6% | **Retention Rate:** 71.4%
- Most of the churn is from the Basic subscription plan – nothing to worry about in terms of major revenue impact
- Most of the churn happened in September 2024, and the most affected state is Karnataka
- **Average Tenure (Days):** 1,451 | **ARPU:** ₹18.8
- **Total Revenue:** 395
- **Revenue loss due to churn:** 74 | **CLTV Lost:** 2,047
- **% Revenue loss:** 18%
- **Monthly vs annual churn:** 55.6% vs 8.3%

### Action Items
- Check what happened in Karnataka – was there any price increase, user complaints, tech issues, etc.
- Did we increase the subscription price for the Basic plan, or make any recent changes — especially in September?
- Check what competitors are doing, since at least one user moved to a competitor
- Focus on customers with 'High' & 'Medium' churn risk — check their LTV (to build a priority list), review complaint history, and reach out via email, SMS, or calls to resolve their issues

---

## Portfolio Project Summary

**Churn & Revenue Impact (general summary)**
Engineered an end-to-end churn analytics pipeline for an OTT subscription platform by integrating multi-table subscriber data across acquisition type, contract structure, and plan tier (20+ KPIs). Uncovered a significant churn disparity between monthly and annual contract segments, quantified MRR leakage and CLTV erosion attributed to high-risk cohorts, and delivered a data-backed contract-migration retention strategy to reduce involuntary subscriber loss.

**Risk Scoring & Segmentation**
Developed a multi-dimensional churn risk scoring model by synthesizing subscription tenure, plan type, and support escalation signals across three relational tables (20+ KPIs), segmented the customer base into risk tiers using composite churn scores, exposed a significant lifetime value gap between churned and retained cohorts, and recommended prioritizing Premium annual-plan retention over Basic monthly acquisition to maximize long-term revenue yield.

**Support Intelligence & Cancellation Analysis**
Performed cross-functional support-churn correlation analysis by joining complaint, escalation, and CSAT data with subscription records, identified that escalated support interactions were disproportionately concentrated among churned customers, decomposed cancellation drivers into competitor switching, pricing sensitivity, and content dissatisfaction, and translated findings into a prioritized product and pricing roadmap presented to the platform's growth team.

**Churn & Revenue Impact (with dataset numbers)**
Engineered an end-to-end churn analytics pipeline for an OTT subscription dataset (20+ KPIs), identifying a 28.6% overall churn rate and surfacing that monthly-contract subscribers churned at 55.6% — 6.7x the 8.3% annual-contract rate — directly attributing $73.94/mo in MRR leakage and $2,047 in CLTV erosion to six at-risk customers, enabling a targeted contract-migration retention strategy.
