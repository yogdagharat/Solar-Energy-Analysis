# ☀️ Barriers to Solar Energy Adoption

An exploratory data analysis project examining **why solar energy adoption lags behind solar potential** — globally and within the United States. The analysis investigates economic, geographic, and infrastructure factors that drive or hinder solar adoption.

---

## 📌 Project Overview

Despite abundant sunlight in many parts of the world, solar energy adoption remains highly unequal. This project asks:

- Which countries and U.S. states have the highest solar potential — and are they using it?
- What economic and infrastructure factors best explain adoption rates?
- Within the U.S., how do installation costs, household income, and roof-level solar potential relate to actual installations?

The analysis is split into two notebooks: a **global view** and a **U.S.-focused deep dive**.

---

## 📓 Notebooks

| Notebook | Description |
|---|---|
| [`Solar_Energy_Analysis_Global.ipynb`](Solar_Energy_Analysis_Global.ipynb) | Global analysis of 150+ countries using photovoltaic potential, GDP, grid reliability, and electricity access. Includes regression modelling, clustering, and a solar underperformance metric. |
| [`Solar_Energy_Analysis_USA.ipynb`](Solar_Energy_Analysis_USA.ipynb) | U.S. state-level analysis linking rooftop solar potential, installation costs, household income, and actual solar adoption rates. |

---

## 🔍 Key Findings

**Global**
- Solar adoption is highly right-skewed — a small number of countries account for the vast majority of installed capacity.
- GDP per capita and grid reliability are the strongest predictors of adoption, even more than raw solar potential (GHI/PVOUT).
- Many high-sunlight, low-income regions (Sub-Saharan Africa, parts of South Asia) are significant underperformers relative to their resource base.
- K-Means clustering identifies three country archetypes: *Developed Leaders*, *Emerging Markets*, and *Underperformers*.

**United States**
- Solar potential (capacity factor) does not strongly predict adoption at the state level — economic factors dominate.
- Higher median household income correlates with more installations, suggesting cost remains a barrier.
- States with the most installations (e.g. California) have moderate-to-high solar potential AND high incomes, not just sunlight.

---

## 📊 Datasets

| Dataset | Source |
|---|---|
| Global Photovoltaic Power Potential by Country | [World Bank Data Catalog](https://datacatalog.worldbank.org/search/dataset/0038379/global-photovoltaic-power-potential-by-country) |
| Distributed Solar Techno-economic Data (USA) | [DOE / NREL via data.nlr.gov](https://data.nlr.gov/submissions/112) |
| USA Solar and Storage Data | [Lawrence Berkeley National Lab](https://emp.lbl.gov/tracking-the-sun/) |
| USA Median Household Income | [NIH / HDPULSE](https://hdpulse.nimhd.nih.gov/data-portal/) |
| RS Clean Energy Credit | [IRS](https://www.irs.gov/credits-deductions/residential-clean-energy-credit) |
| Solar Tax Credit Explanation | [EnergySage](https://www.energysage.com/solar/solar-tax-credit-explained/) |
| Canada Greener Homes Initiative | [Natural Resources Canada](https://natural-resources.canada.ca/energy-efficiency/home-energy-efficiency/canada-greener-homes-initiative) |

---

## 🛠️ Libraries Used

- `pandas`, `numpy` — data manipulation
- `matplotlib`, `seaborn` — visualisation
- `statsmodels` — OLS regression & VIF analysis
- `scikit-learn` — K-Means clustering, StandardScaler, SimpleImputer

---

## 📁 Repository Structure

```
├── Solar_Energy_Analysis_Global.ipynb   # Global EDA, regression, clustering
├── Solar_Energy_Analysis_USA.ipynb      # US state-level EDA
└── README.md
```

---

## ▶️ How to Run

1. Clone the repository
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn statsmodels scikit-learn openpyxl
   ```
3. Download the datasets from the links above and place them in the repo root with these filenames:
   - `solargis_pvpotential_countryranking_2020_data.xlsx`
   - `usa_solar_potential.csv`
   - `usa_solar_costs.csv`
   - `usa_household_income.csv`
   - `usa_state.csv`
4. Open and run either notebook in Jupyter

---

## 📌 Notes

- The U.S. installation cost analysis uses data from 2022 onward only.
- Missing values in the cost dataset are encoded as `-1` and are treated as `NaN`.
- The global adoption variable (`pv_wp_per_capita`) is log-transformed due to strong right skew.
- The solar underperformance metric is defined as `potential_pvout / (log_pv_wp_per_capita + 1)` — higher values indicate countries with strong sunlight but poor adoption.
