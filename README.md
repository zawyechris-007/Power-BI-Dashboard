# 📊 Commercial Sales & Profitability Performance Dashboard

![Superstore Sales Dashboard](https://raw.githubusercontent.com/zawyechris-007/Power-BI-Dashboard/main/README.md)

## 📌 Executive Summary
This end-to-end commercial analytics solution evaluates 4 years of retail transaction data ($2.33M Total Sales Revenue, $292.30K Net Profit) to isolate drivers of profit decay, regional revenue leakage, and product return overhead. The project translates raw transactional logs into actionable pricing and portfolio rationalisation strategies for commercial leadership.

---

## 💡 Key Commercial Narratives & Action Plan

### 1. The Profitability Illusion (Category Margins)
* **Insight:** Technology drives **50.1% of overall net profit** ($143.08K), whereas Furniture generates **31.46% of total revenue** but only **6.75% of net profit**.
* **Rationale:** Sub-categories like **Tables** generate $208.02K in sales but operate at a severe net loss (-$17.75K, -8.5% margin). Conversely, **Copiers** generate $150.75K in sales while yielding a **37.2% net profit margin** ($56.09K).
* **Action:** Reallocate marketing budget away from low-margin volume drivers toward high-margin lines (Copiers, Accessories, Phones), and restructure Furniture delivery/assembly fee models.

### 2. Regional Revenue Leakage & Discount Thresholds
* **Insight:** Texas, Illinois, and Pennsylvania generated a cumulative net loss of **-$53.90K** (18% of overall profit drag), reaching -$20.70K in 2026 alone.
* **Rationale:** Margin compression is directly tied to ungoverned promotional discounting. Undiscounted transactions maintain a **29.5% profit margin**, but discounts **≥30%** push net margins into negative territory (-10% to -180%).
* **Action:** Enforce regional discount governance capping maximum promotional discounts at **20%**, instantly returning these regions to profitability without exiting the territories.

### 3. Revenue Decay via Product Returns
* **Insight:** Total return leakage reached **7.76% of overall revenue** ($180.50K impacted sales), driven by a **~50% jump in product returns in 2026**.
* **Rationale:** Return volume disproportionately affects high-ticket line items: **Machines** recorded an **11.1% return rate** (flipping to a net loss in 2026), and **Tables** recorded a **9.2% return rate**.
* **Action:** Audit vendor quality and shipping modes for Machines and Tables to determine if spikes stem from transit damage, product defects, or inaccurate online specifications.

---

## 🛠️ Technical Architecture & DAX Modeling

* **Data Modeling:** Star-schema design separating transactional fact tables (`Fact_Sales`) from dimension tables (`Dim_Product`, `Dim_Customer`, `Dim_Geography`, `Dim_Date`).
* **Time Intelligence DAX:** Contiguous date table integration using `SAMEPERIODLASTYEAR` and `DIVIDE` to calculate robust YoY metrics without divide-by-zero baseline errors:
  $$\text{Sales YoY\%} = \text{DIVIDE}([Total\ Sales] - [Sales\ PY], [Sales\ PY])$$
* **Data Hygiene & ETL:** SQL query optimization using CTEs and Window Functions (`LAG()`, `NTILE()`) to structure transaction data prior to Power BI ingest.

---

## 📁 Repository Structure
* `Superstore sales Dashboard.pbix`: Interactive Power BI Desktop report source file.
* `README.md`: Project documentation and commercial analytical summary.
