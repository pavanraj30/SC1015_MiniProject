# SC1015_MiniProject
## Description  
Our motivation behind this Data Science project was to use data available to us to predict future stock price movements. In stock trading, the majority of decisions made are motivated by convictions that are subjective in nature. At what price is a stock a good buy, how we think the market will move day to day, etc differ greatly from person to person, even when it comes to industry professionals. This made us wonder if there was a way to make market decisions more objectively, using large amounts of data to find correlations and patterns. 

## Problem Definition  
Using the data available,  
- Which machine learning model is the most appropriate in predicting price movements in the stock market based on a set of predictors?

## [Dataset]
- Dataset from kaggle by Cam Nugent
- Consist of open and close prices as well as day high and day low prices for all the stocks included in the S&P500 market index from 2013 to 2018
- Over the years, all the stock prices increased. However, day to day price movements seemed to be erratic and unpredictable. It was difficult, just from the data, to discern any pattern of which day would the price of a given stock increase or decrease, and by how much.


### [1. Data Prepartion & Exploratory Data Analysis]
- Plotted out the closing price of each day with the date
- Check the correlation of each day’s open and close price, which turned out to be almost perfectly linear
- Realised we could take advantage of the short term fluctuations
- Relatively free from anomalies as all the data points sat within a relatively small range, with no outliers
- Since our motivation was to predict market movements based on data predictors, we cleaned up the data by removing the dates where there was significant market movement due to external macroeconomic shocks


### [2. ML Technique 1: Classification]
- Trade is called ‘Yes’ if on a given day, the value of close is greater than the value of open. It indicates that by buying the stock when it opens, the user will be better off by the end of the day
- Check the initial distribution of the response variable to identify if there is any ‘class imbalance’
- Set up a Multivariate Classification problem
- Set up the code with train and test datasets
- Performed basic statistical exploration and visualization on both the train and test datasets
- Proceed to plot a decision tree with max depth 2 and 4 for our analysis
- Both trees gave us similar results when it came to its test data accuracy - here being 52% indicating that this might not be a good model after all

### [3. ML Technique 2: Time Series Forecasting]
- Process of analyzing time series data using statistics and modelling to make predictions and informed strategic decisions
- Extracted the opening, closing prices and date of the NVDA stock from the data set and created a data frame with a new column consisting of the closing and opening price difference
- Checking for stationarity is important because it not only makes modelling time series easier, but it is an underlying assumption in many time series methods such as the one we will use in this project-ARIMA
- For the forecasting we have used the ARIMA or autoregressive integrated moving average  model which is a statistical analysis model that predicts future values based on past values.
- Model has the explained variance of only -.027 and a high RMSE of 8.67 -> does not accurately predict the price fluctuation on a daily basis
- Predicts accurately 6 out of 9 times, i.e, with an accuracy of 66.7%  when we check whether we will make a profit on a certain day 
- Even though our model does not accurately predict the magnitude of price fluctuations due to the large volatility in the market, it can still somewhat accurately capture the market trend and predict whether the price will rise or fall on a certain day.



### [4. ML Technique 3: Regression Analysis]
- Used the past 9 trading days of data to try to predict the next day’s price movement
- Assumption: Prices remain stable and will trend towards the local average
- Price movement is calculated by taking the difference between the current day’s closing price and the previous day’s closing price
- Variables in original dataset had no discernible pattern so we introduced two new variables that could be derived from the dataset (RSI & EMA)
- Placed these data points into a heatmap and found that by removing magnitude, deviation from EMA could be a good predictor for price movements
- Price < EMA, in 70% of the cases, price moved upwards
- Price > EMA, in 68% of the cases, price moved downwards
- While the model was unable to predict accurately how much price moved based on the price’s deviation from EMA, it was able to more accurately predict in what direction price moved
- Similarly with time series forecasting the model predicted with a 66.67% accuracy in which directions the price will move
- May not accurately predict the magnitude of price change but is still able to predict the price movements in the market


## Conclusion
- Both regression models used had a dismal prediction accuracy of **~50%**
- Insights gained from the models allowed us to come up with an adjusted classification model
- Instead of deciding to trade based on a day’s open and close prices, we used RSI as a predictor to classify a day as buy or sell
- Much better prediction accuracy of **~70%**
- To answer our problem definition, the classification model that predicted a day as buy or sell based on RSI was the best model in predicting price movements
- 3 models we used originally did not give us the results that we expected
- By integrating our approaches to regression and classification, we managed to build a model that yielded the best results


## Contributors  
- Pavanraj Selvaraju (U2122616H)
- Daniel Tan (U2121315A)
- Aditya Kumar Pugalia (U2123212D) 

## References  

