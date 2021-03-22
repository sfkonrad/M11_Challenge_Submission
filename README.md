**[M11_Challenge_Submission](https://github.com/sfkonrad/M11_Challenge_Submission/blob/main/M11_Challenge_Submission/M11g_Challenge_KonradK_forecasting_net_prophet.ipynb)**

Konrad Kozicki

UCB-VIRT-FIN-PT-12-2020-U-B-TTH

# [Forecasting Net Prophet](https://github.com/sfkonrad/M11_Challenge_Submission/blob/main/M11_Challenge_Submission/M11g_Challenge_KonradK_forecasting_net_prophet.ipynb)
![image](https://miro.medium.com/max/2400/1*BVIwEoE5oEmHJU8XbV_mKA.png)

In this challenge, we assume the roles of growth analysts at [MercadoLibre](http://investor.mercadolibre.com/investor-relations). With over 200 million users, MercadoLibre is the most popular e-commerce site in Latin America. We've been tasked with analyzing the company's financial and user data in clever ways to make the company grow. Therefore, we must determine whether the ability to predict search traffic can translate into the ability to successfully trade the corresponding stock.


We were tasked with completing four steps and an optional fifth step, as follows:

* Step 1: Find unusual patterns in hourly Google search traffic

* Step 2: Mine the search traffic data for seasonality

* Step 3: Relate the search traffic to stock price patterns

* Step 4: Create a time series model with Prophet

* Step 5 (optional): Forecast revenue by using time series models

The following subsections detail these steps.

---
---

## Step 1: Find Unusual Patterns in Hourly Google Search Traffic

The data science manager asks if the Google search traffic for the company links to any financial events at the company. Or, does the search traffic data just present random noise? To answer this question, we identify any unusual patterns in the Google search data for the company, and connect them to the corporate financial events.
> To do so, we completed the following steps:
> 1. Read the search data into a DataFrame, and then slice the data to just the month of May 2020. (During this month, MercadoLibre released its quarterly financial results.) Use hvPlot to visualize the results. Determine whther any unusual patterns exist.
> 2. We calculated the total search traffic for the month, then compared the value to the monthly median across all months. Google search traffic did increase during the month that MercadoLibre released its financial results.

![image](https://github.com/sfkonrad/M11_Challenge_Submission/blob/main/M11_Challenge_Submission/Documentation/Images/part-2.2_hourly_search_trends_day_of_wk.jpg)

---

## Step 2: Mine the Search Traffic Data for Seasonality

Marketing realizes that they can use the hourly search data, too. If they can track and predict interest in the company and its platform for any time of day, they can focus their marketing efforts around the times that have the most traffic. This will get a greater return on investment (ROI) from their marketing budget. To that end, we mined the search traffic data for predictable seasonal patterns of interest in the company. 
> To do so, we completed the following steps:
> 1. Group the hourly search data to plot the average traffic by the day of the week (for example, Monday vs. Friday).
> 2. Using hvPlot, visualize this traffic as a heatmap, referencing the `index.hour` as the x-axis and the `index.dayofweek` as the y-axis. Does any day-of-week effect that you observe concentrate in just a few hours of that day?
> 3. Group the search data by the week of the year. Determine whether the search traffic has a tendancy to increase during the winter holiday period (weeks 40 through 52).

![image](https://github.com/sfkonrad/M11_Challenge_Submission/blob/main/M11_Challenge_Submission/Documentation/Images/part-3.1_search_trends_wk_of_yr.jpg)

---

## Step 3: Relate the Search Traffic to Stock Price Patterns

You mention your work on the search traffic data during a meeting with people in the finance group at the company. They want to know if any relationship between the search data and the company stock price exists, and they ask if you can investigate.
> To do so, we completed the following steps:
> 1. Read in and plot the stock price data. Concatenate the stock price data to the search data in a single DataFrame.
> 2. Market events emerged during the year of 2020 that many companies found difficult. But, after the initial shock to global financial markets, new customers and revenue increased for e-commerce platforms. Slice the data to just the first half of 2020 (`2020-01` to `2020-06` in the DataFrame), and then use hvPlot to plot the data. Do both time series indicate a common trend that’s consistent with this narrative?
> 3. Create a new column in the DataFrame named “Lagged Search Trends” that offsets, or shifts, the search traffic by one hour. Create two additional columns:
>    * “Stock Volatility”, which holds an exponentially weighted four-hour rolling average of the company’s stock volatility
>    * “Hourly Stock Return”, which holds the percent change of the company's stock price on an hourly basis
> 4. Review the time series correlation, and then answer the following question: Does a predictable relationship exist between the lagged search traffic and the stock volatility or between the lagged search traffic and the stock price returns?

![image](https://github.com/sfkonrad/M11_Challenge_Submission/blob/main/M11_Challenge_Submission/Documentation/Images/part-3.0_stock_volatility.jpg)

---

## Step 4: Create a Time Series Model with Prophet

Next, we produced a time series model that analyzes and forecasts patterns in the hourly search data. 
> To do so, we completed the following steps:
> 1. Set up the Google search data for a Prophet forecasting model.
> 2. After estimating the model, we plot the forecast to identify the near-term forecast for the popularity of MercadoLibre.
> 3. Plot the individual time series components of the model to answer the following questions:
    * What time of day exhibits the greatest popularity?
    * Which day of the week gets the most search traffic?
    * What's the lowest point for search traffic in the calendar year?
    * 
![image](https://github.com/sfkonrad/M11_Challenge_Submission/blob/main/M11_Challenge_Submission/Documentation/Images/part-4.0_forecast_24-hr_rolling_avg.jpg)
![image](https://github.com/sfkonrad/M11_Challenge_Submission/blob/main/M11_Challenge_Submission/Documentation/Images/part-4.0_forecast.jpg)

---

## Step 5 (Optional): Forecast Revenue by Using Time Series Models

A few weeks after our initial analysis, the finance group follows up to find out if you can help them solve a different problem. Your fame as a growth analyst in the company continues to grow!

Specifically, the finance group wants a forecast of the total sales for the next quarter. This will dramatically increase their ability to plan budgets and to help guide expectations for the company investors.

> To do so, we complete the following steps:
> 1. Read in the daily historical sales (that is, revenue) figures, and then apply a Prophet model to the data.
> 2. Interpret the model output to identify any seasonal patterns in the company's revenue. For example, what are the peak revenue days? (Mondays? Fridays? Something else?)
> 3. Produce a sales forecast for the finance group. Give them a number for the expected total sales in the next quarter. Include the best- and worst-case scenarios to help them make better plans.

Q3-2020 Revenue Pojections: 
>>>>> ##### worst case:      
>>>>>> ####  $887,525,372 
>>>> ### MOST LIKELY Q3-2020 Revenue:        $ 969,572,683
>>>>> ##### best case:       
>>>>>> #### $1,051,650,789

![image](https://github.com/sfkonrad/M11_Challenge_Submission/blob/main/M11_Challenge_Submission/Documentation/Images/part-5.1_daily_revenue.jpg)
