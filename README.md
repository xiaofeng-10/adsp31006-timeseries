# adsp31006-timeseries

# Retail Demand Forecasting with Time Series Models
## Overview
This project analyzes historical retail sales data and builds time-series forecasting models to predict future sales trends. Using weekly sales data from multiple Walmart stores, the analysis identifies seasonal demand patterns and evaluates different forecasting approaches.

## Dataset
The dataset contains 6,435 weekly sales observations across 45 stores from 2010 to 2012.

## Time-series diagnostics
- ACF and PACF plots to analyze autocorrelation structure
- Seasonal decomposition to separate trend, seasonal, and residual components
- Outlier detection using the IQR method

## Modeling Approach
1. SARIMA
A baseline SARIMA(1,0,0)(0,1,0)[52] model was constructed based on ACF/PACF diagnostics and stationarity tests.
2. Auto-SARIMA (SARIMAX)
An automated model selection procedure using pmdarima identified the best model: SARIMA(2,0,2)(1,0,0)[52]
Holiday indicators were incorporated as exogenous variables to capture retail demand spikes.
3. Prophet
A Prophet forecasting model was also implemented with yearly seasonality and holiday regressors.

## Model Evaluation
| Model | RMSE | MAE | MAPE |
|-------|------|-----|------|
| SARIMA(1,0,0)(0,1,0)[52] | $51,863 | $34,345 | 3.39% |
| Auto-SARIMA(2,0,2)(1,0,0)[52] | $33,666 | $27,492 | 2.78% |
| Prophet | $50,826 | $38,901 | 3.84% |

**Auto SARIMA** provides the **best forecasting accuracy** with the lowest error across all three metrics.

## Forecasting
Using the Auto-SARIMA model, the project generated 52-week future sales forecasts incorporating holiday indicators. The forecasts is reliable and it predicts a strong sales increase during the holiday season, which is consistent with peaks seen in previous years.

## Implications
The forecast can support potential retail planning tasks such as:
- inventory management
- staffing decisions
- demand planning
