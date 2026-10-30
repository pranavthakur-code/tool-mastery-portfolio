# Data Science Tool Mastery Portfolio

A hands-on showcase of the core data analyst toolkit on one real dataset:
**Palmer Penguins** (344 penguins, 3 species, Palmer Station, Antarctica).

**Guiding question:** can the three species be told apart from body measurements,
and what do the measurements reveal about each other?

## Tools demonstrated
| Tool | What the notebook shows |
|---|---|
| NumPy | Vectorised z-scores, broadcasting, percentiles; ~56x speed-up over a Python loop |
| pandas | Missing-value handling, type conversion, feature engineering, groupby, crosstab, pivot tables |
| SQL (SQLite) | GROUP BY, window function (`SUM() OVER (PARTITION BY ...)`), CTE and JOIN |
| Matplotlib / seaborn | Scatter, box, pair plot, regression plots, confusion matrix, importance chart |
| SciPy | Shapiro, Levene, ANOVA, Kruskal-Wallis, Tukey HSD, Welch t-test, effect size, chi-square |
| scikit-learn | Leak-free `Pipeline` + `ColumnTransformer`, cross-validation, baseline, logistic regression, random forest |

## Key results
- Gentoo penguins are about 1.4 kg heavier than the other species (ANOVA p < 1e-80); Adelie and Chinstrap do not differ in mass (Tukey p = 0.88).
- **Simpson's paradox:** bill length and depth are negatively correlated overall (r = -0.24) but positively correlated within every species (r = 0.39 to 0.65).
- Species can be classified with about 99% cross-validated accuracy (baseline 44%).
  Bill length and flipper length are the most useful features.

## Files
| File | Description |
|---|---|
| `Tool_Mastery_Portfolio.ipynb` | Executed notebook with code, outputs and charts |
| `penguins.csv` | Dataset (source: seaborn-data on GitHub) |
| `fig*.png` | Exported charts |

## Run it
```bash
python -m venv venv
venv\Scripts\activate          # macOS/Linux: source venv/bin/activate
pip install numpy pandas matplotlib seaborn scipy scikit-learn jupyter
jupyter notebook Tool_Mastery_Portfolio.ipynb
```
Keep `penguins.csv` in the same folder as the notebook.

## Notes
- The test set has only 86 penguins, so the perfect test score is less reliable than the 5-fold cross-validation result.
- Body-mass data is not perfectly normal for Adelie and variances differ, so a non-parametric Kruskal-Wallis test is reported next to the ANOVA.

## Data source
Horst, Hill and Gorman (2020), Palmer Penguins, via
[seaborn-data](https://github.com/mwaskom/seaborn-data/blob/master/penguins.csv).
