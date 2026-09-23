# PulseCart Customer Intelligence Case

## Environment

- Python 3.12
- Jupyter Notebook
- MySQL / MySQL Workbench
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- TensorFlow
- Pillow

---

## How to Rerun

### 1. Clone the Repository

```bash
git clone <repository-url>
cd PulseCart
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Run the SQL Analysis

Open MySQL Workbench and run:

```
data/mysql/pulsecart_dump.sql
```

After loading the database, open:

```
queries.sql
```

and execute the required SQL queries.

### 4. Run the Python Analysis

Open:

```
analysis.ipynb
```

Run the notebook from top to bottom. The notebook contains the analysis for Stations B–H.

---

## Business Questions

### 1. Who is leaving, and is any city or plan actually different?

Out of 850 customers, 141 churned. Houston had the highest churn rate at 30.32%, compared with 12.69% in other cities. The difference was statistically significant (p < 0.001). No formal statistical test was performed for plan-level churn differences.

### 2. Which category is driving returns, and is that gap large enough to act on?

The Kitchen category had the highest return rate at 23.84%, compared with 6.49% for all other categories. The difference was 17.35 percentage points and was statistically significant (p < 0.001). Kitchen returns should therefore be investigated further at the product and operational level.

### 3. Can you predict churn for an outreach list without leaking the future?

Yes. The churn model used customer information available before June 1, 2026, including order count, spend, recency, return rate, support tickets, plan, and city. Logistic Regression achieved 0.782 ROC-AUC, with 0.529 precision and 0.321 recall. The model can be used to prioritize outreach, but it missed 19 churned customers.

### 4. Did daily orders change after June 1, 2026, or is that noise?

Average daily orders decreased from 171.71 before June 1 to 133.70 after June 1, a decrease of about 38 orders per day. This shows a noticeable change in order volume. However, no formal change-point test was performed, so the analysis cannot conclude that June 1 caused the decrease.

### 5. What should PulseCart do in the next 30 days?

- Investigate Houston churn because the churn rate was 30.32%, compared with 12.69% elsewhere.
- Investigate Kitchen returns because the return rate was 23.84%, compared with 6.49% for other categories.
- Use the churn model for targeted outreach because it achieved 0.782 ROC-AUC and can help prioritize customers for retention campaigns. Recheck the results after 30 days.

---

## Limitations

- The analysis uses only the provided PulseCart dataset.
- The churn model still misses some actual churned customers.
- No formal statistical test was performed for plan-level churn differences.
- The decrease in daily orders after June 1 is an observed change; a formal change-point test was not performed.
- Clustering results describe behavioral groups and should not be treated as definitive customer personas.
- The CNN was trained on only 240 images, so the 100% holdout accuracy should not be treated as proof of production-level performance.
- A larger and more diverse image dataset would be needed to evaluate real-world CNN performance.
- Statistical associations and observed differences do not by themselves establish causation.
