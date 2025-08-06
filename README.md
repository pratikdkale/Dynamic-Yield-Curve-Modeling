
# Dynamic Yield Curve Modeling with Kalman Filter

## Project Title
Dynamic Yield Curve Modeling and Trading Signal Forecasting Using the Dynamic Nelson-Siegel Model with Kalman Filtering

## Summary
This project implements a robust fixed income analytics framework to model and forecast the U.S. Treasury yield curve using the Dynamic Nelson-Siegel (DNS) methodology. By leveraging daily yield data from the Federal Reserve Economic Database (FRED), we extract the latent Level (β₀), Slope (β₁), and Curvature (β₂) factors that characterize the shape of the yield curve. These factors are then smoothed using a Kalman filter to construct a dynamic state-space model of the term structure. The project further investigates the predictive power of β₁ (slope) for forecasting the 2s10s spread and designing curve steepener/flattening strategies.

The DNS model is widely adopted by central banks and asset managers due to its balance between flexibility and interpretability. Kalman filtering allows us to update our estimates of the curve factors sequentially in time, handling noisy data efficiently and enabling short-term forecasting. We evaluate the signal extracted from β₁ for potential trading applications and simulate its effect on a directional yield curve strategy. The end-to-end pipeline is built in Python and is fully modular, making it suitable for research, backtesting, or integration into a live macro model.

## Techniques Used
- Dynamic Nelson-Siegel yield curve modeling
- Kalman filtering (state-space modeling)
- Regression analysis using lagged factors
- Signal thresholding and regime filtering
- Performance evaluation using R², MSE, correlation
- PnL backtesting
- Vectorized Python implementation

## Dataset
- Source: [Federal Reserve Economic Database (FRED)](https://fred.stlouisfed.org/)
- Frequency: Daily U.S. Treasury yields (e.g., 3M, 2Y, 10Y, 30Y)
- Accessed via: `fredapi` with FRED API Key

### How to Get a FRED API Key:
1. Visit [fred.stlouisfed.org](https://fred.stlouisfed.org/)
2. Create or log in to your free account
3. Go to your account settings and generate an API key
4. Store it in a `.env` file like this:
```
FRED_API_KEY=your_api_key_here
```

## Steps Performed
1. Connect to the FRED API and download Treasury yield data
2. Clean and align yield time series across all maturities
3. Visualize static yield curves across key historical dates
4. Fit static Nelson-Siegel curves to each date
5. Apply Kalman filtering to extract dynamic β₀ (level), β₁ (slope), and β₂ (curvature)
6. Forecast 2s10s spread using lagged β₁ factors
7. Evaluate model performance with statistical metrics
8. Generate a trade signal and simulate basic strategy PnL

## Sample Plots
- Static yield curve snapshots (e.g., 2008, 2020)
- Time series of DNS factors (β₀, β₁, β₂)
- Forecasted vs actual 2s10s yield spread
- Trading signal thresholds and cumulative PnL

## Key Results
- DNS with Kalman filter achieved an R² of 0.61 and a correlation of 0.78 when forecasting 2s10s spread using lagged β₁
- Threshold-based β₁ signals captured curve shifts and improved PnL consistency
- The slope factor (β₁) provided valuable information on yield curve steepening/flattening regimes

## Business Relevance
Yield curve shape is a leading macroeconomic indicator. Accurately modeling its dynamics enables:
- Better anticipation of recessionary risks (e.g., via 2s10s inversion)
- Fixed-income strategy design (e.g., curve steepeners or butterfly trades)
- Macro signal generation for multi-asset allocation
This project demonstrates practical use of term structure models and factor-based signal research, bridging macroeconomics and quantitative trading.

