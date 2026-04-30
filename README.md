<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0D1117,50:161B22,100:21262D&height=220&section=header&text=Macro-Financial+Stress+Testing&fontSize=44&fontColor=58A6FF&animation=twinkling&fontAlignY=38&desc=OLS+Satellite+Models+%E2%80%A2+Regulatory+Capital+Framework+%E2%80%A2+12-Quarter+Horizon&descAlignY=62&descSize=17" />

<br/>

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=20&pause=1000&color=58A6FF&center=true&vCenter=true&width=750&lines=OLS+Satellite+Models+Calibrated+to+Regulatory+Benchmarks;Baseline+%2B+Adverse+Scenario+Capital+Projections;12-Quarter+Horizon+%E2%80%A2+3+UK+Banks+%E2%80%A2+4+Portfolio+Buckets;pytest+Validation+%2B+Full+Audit+Documentation)](https://github.com/yashxsainix/macro-financial-stress-testing-Public)

<br/>

[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![statsmodels](https://img.shields.io/badge/statsmodels-OLS_Satellite_Models-4B8BBE?style=for-the-badge)](https://statsmodels.org)
[![pytest](https://img.shields.io/badge/pytest-Validated_Outputs-0A9EDC?style=for-the-badge&logo=pytest&logoColor=white)](https://pytest.org)
[![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org)

<br/>

<img src="https://img.shields.io/badge/Quarters-12-58A6FF?style=flat-square&labelColor=0D1117" />
<img src="https://img.shields.io/badge/Banks_Modeled-3-3FB950?style=flat-square&labelColor=0D1117" />
<img src="https://img.shields.io/badge/Portfolio_Buckets-4-F78166?style=flat-square&labelColor=0D1117" />
<img src="https://img.shields.io/badge/Framework-Regulatory_Supervisory-D29922?style=flat-square&labelColor=0D1117" />
<img src="https://img.shields.io/badge/Tests-pytest_Coverage-8957E5?style=flat-square&labelColor=0D1117" />

</div>

---

## ❓ The Question This Project Answers

> *Given a specified macroeconomic stress path, how does bank capital evolve — and where do regulatory constraints bind?*

This is the question at the heart of every major financial stability exercise run by central banks and regulators worldwide. The Bank of England runs this every year. The Federal Reserve runs this under DFAST. This project implements that same supervisory logic transparently, using UK data, reproducible code, and validated outputs.

---

## 🏦 What Stress Testing Actually Does

When a severe recession hits — unemployment spikes, house prices fall, corporate defaults rise — banks absorb losses through their loan portfolios. Those losses consume capital. If capital falls below regulatory minimums, the bank cannot continue operating normally.

Stress testing answers: **how much capital does each bank have, how fast does it deplete under stress, and which banks breach regulatory thresholds?**

---

## 🏗️ Framework Architecture

```mermaid
graph TD
    A["📈 Macroeconomic Scenarios<br/>• Baseline path<br/>• Adverse stress path<br/>• GDP, unemployment, HPI inputs"] --> B

    B["🗂️ Balance Sheet Module<br/>• 3 UK banks: HSBC, Lloyds, StanChart<br/>• Portfolio segmentation<br/>• Starting CET1 ratios"] --> C

    A --> C
    C["📡 Satellite Models (OLS)<br/>• Macro → credit loss mapping<br/>• 4 portfolio buckets:<br/>  mortgages, unsecured, SME, corporate<br/>• Calibrated to regulatory benchmarks"] --> D

    D["⚙️ Loss Aggregation Engine<br/>• Quarter-by-quarter loss accumulation<br/>• RWA evolution<br/>• CET1 ratio dynamics"] --> E

    E["📊 Capital Reporting<br/>• CET1 ratio paths (12 quarters)<br/>• System-level shortfall assessment<br/>• Trough capital identification<br/>• Cross-bank resilience comparison"]

    F["🧪 pytest Validation<br/>• Balance sheet consistency<br/>• Satellite model outputs<br/>• Synthetic data tests"] --> C
    F --> D

    style A fill:#58A6FF,color:#0D1117,stroke:#58A6FF
    style C fill:#3FB950,color:#0D1117,stroke:#3FB950
    style D fill:#D29922,color:#0D1117,stroke:#D29922
    style E fill:#F78166,color:#0D1117,stroke:#F78166
    style F fill:#8957E5,color:#fff,stroke:#8957E5
```

---

## 📡 The Satellite Model Logic

The core of the framework is a set of **OLS satellite models** that translate macroeconomic variables into credit losses for each portfolio bucket.

```python
# Each satellite model follows regulatory convention:
# credit_loss_rate = f(GDP_growth, unemployment_change, HPI_change, ...)
# Calibrated to match observed UK loss rates under historical stress

# Example: Mortgage portfolio satellite
# PD_mortgages ~ β₀ + β₁·ΔHPI + β₂·ΔUnemployment + β₃·GDP_gap + ε
```

This approach separates **macroeconomic scenario design** from **loss transmission** — the same pattern used in DFAST, EBA stress tests, and Bank of England FST exercises.

---

## 🏛️ Banks and Portfolio Buckets

**Banks modeled** — selected to represent distinct business models:
| Bank | Business Model | Key Exposure |
|------|----------------|-------------|
| HSBC | Global diversified | International corporate |
| Lloyds Banking Group | Domestic retail | UK mortgages + consumer |
| Standard Chartered | Emerging markets | Export-oriented corporate |

**Portfolio buckets:**
- 🏠 Owner-occupied mortgages
- 💳 Consumer unsecured credit
- 🏭 SME lending
- 🏢 Large corporate lending

---

## 📊 Key Results

<details>
<summary><b>📉 Capital Ratio Paths — Adverse Scenario</b></summary>

Under the adverse macroeconomic stress, capital depletion differs materially across banks due to differences in starting capital positions and portfolio composition. Losses are **front-loaded** — the largest capital impact occurs within the first 4 quarters of the stress horizon.

The framework generates CET1 ratio paths for each bank across all 12 quarters, identifying when (and whether) each institution breaches the regulatory minimum threshold.

</details>

<details>
<summary><b>⚠️ System-Level Shortfall Assessment</b></summary>

System-wide capital shortfall is calculated as the aggregate deficit across all banks that breach the regulatory floor under the adverse scenario. This is the headline metric used in official stress test publications.

Results are reported as conditional outcomes — not forecasts — making clear that the analysis answers *"what would happen under this scenario"*, not *"what will happen."*

</details>

<details>
<summary><b>📈 Cross-Bank Resilience Comparison</b></summary>

Banks with higher starting CET1 ratios and lower exposure to macro-sensitive portfolios (e.g., SME lending during a recession) show materially greater resilience. The framework allows direct comparison of trough capital positions across institutions under a **common stress** — which is the core purpose of supervisory stress testing.

</details>

---

## 🗂️ Repository Structure

```
macro-financial-stress-testing/
│
├── src/stress_test/
│   ├── balance_sheet.py    ← Bank balance sheets + portfolio segmentation
│   ├── scenarios.py        ← Baseline and adverse macro scenario definitions
│   ├── satellite.py        ← OLS macro → loss mapping models
│   ├── engine.py           ← Loss aggregation + CET1 capital dynamics
│   ├── reporting.py        ← Tables, figures, and summary outputs
│   ├── data.py             ← UK macro data loader
│   └── config.py           ← Constants and naming conventions
│
├── scripts/
│   └── run_stress_test.py  ← Pipeline orchestration entry point
│
├── tests/
│   ├── test_balance_sheet.py   ← Balance sheet consistency tests
│   ├── test_satellite.py       ← Satellite model output validation
│   └── test_synthetic_data.py  ← Data generation tests
│
└── outputs/
    ├── figures/            ← CET1 ratio paths, loss paths, trough charts
    └── tables/             ← System results, trough summary, loss by bucket
```

---

## 🚀 How to Run

```bash
git clone https://github.com/yashxsainix/macro-financial-stress-testing-Public
pip install -r requirements.txt

# Run the full stress test pipeline
python scripts/run_stress_test.py

# Run validation suite
pytest tests/ -v

# Outputs appear in outputs/figures/ and outputs/tables/
```

---

## 📚 Why This Matters Beyond Finance

Stress testing is applied thinking. You define a scenario, trace its effects through a system, and answer "where does it break?" That discipline — mapping a shock through a pipeline to a measurable outcome — is exactly how good analytical frameworks should be designed regardless of domain.

This project demonstrates that thinking with quantitative rigor, reproducible code, and audit-ready documentation.

---

## 👤 Author

**Yashpal Saini** · [LinkedIn](https://linkedin.com/in/yash-saini-analyst) · [Portfolio](https://yashxsainix.github.io)

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0D1117,50:161B22,100:21262D&height=100&section=footer" />
