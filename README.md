# Forecasting SPY Volatility

Can recent market activity help forecast volatility over the next five trading days? This notebook uses SPY data from 2005–2025 to compare simple benchmarks, linear regressions and decision trees. It also explores whether unusually high trading volume contains useful information.

## Method

The target is the standard deviation of SPY’s daily returns over the **next five trading days**. Forecasts use information available at the close of each forecast date. Models are fitted on 2005–2018 data, compared on 2019–2022 data, and evaluated on a 2023–2025 test period. Accuracy is measured by mean absolute error (MAE).

## Test results

| Model | MAE | Reduction versus baseline |
|---|---:|---:|
| Recent five-day volatility baseline | 0.003690 | — |
| Regression using five-day volatility | 0.003265 | 11.5% |
| Regression using five- and twenty-day volatility | 0.003203 | 13.2% |

Both regressions beat the baseline in each test year. The twenty-day input improved overall accuracy modestly, though it did not help in every year.

## Volume exploration

On the 2019–2022 validation period, volume-only regression and random-forest models did not beat the recent-volatility baseline. An exploratory analysis found that, among days with low recent volatility, unusually high volume was associated with a larger subsequent increase in volatility. This pattern is a possible warning signal, but it has not been confirmed on an untouched test period.

## Notebook

[View the analysis and code](volatility_forecasting.ipynb)

Lower forecast error does not, by itself, imply a profitable trading strategy.
