# Ex.No: 6               HOLT WINTERS METHOD
### Date: 
```
Developed by: Shaik Sameer Basha
Reg No:212222240093
```

### AIM:
To implement the Holt Winters Method Model using Python.
### ALGORITHM:
1. You import the necessary libraries
2. You load a CSV file containing daily sales data into a DataFrame, parse the 'date' column as
datetime, and perform some initial data exploration
3. You group the data by date and resample it to a monthly frequency (beginning of the month
4. You plot the time series data
5. You import the necessary 'statsmodels' libraries for time series analysis
6. You decompose the time series data into its additive components and plot them:
7. You calculate the root mean squared error (RMSE) to evaluate the model's performance
8. You calculate the mean and standard deviation of the entire sales dataset, then fit a Holt-
Winters model to the entire dataset and make future predictions
9. You plot the original sales data and the predictions
### PROGRAM:
```python

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.holtwinters import ExponentialSmoothing
data=pd.read_csv("/content/AirPassengers.csv")
data
data['Month'] = pd.to_datetime(data['Month'])
data.set_index('Month', inplace=True)
model = ExponentialSmoothing(data, trend="add", seasonal="add", seasonal_periods=12)
fit = model.fit()
n_steps = 12  

forecast = fit.forecast(steps=n_steps)
forecast
plt.figure(figsize=(10, 6))
plt.plot(data.index, data, label='Original Data')
plt.plot(pd.date_range(start=data.index[-1], periods=n_steps+1, freq='M')[1:], forecast, label='Forecast')
plt.xlabel('Date')
plt.ylabel('Value')
plt.title('Holt-Winters Forecast')
plt.legend()
plt.show()
```

### OUTPUT:
![6](https://github.com/shaikSameerbasha5404/TSA_EXP6/assets/118707756/d9b4cace-51fe-4d06-8be1-fdd8f994d991)


### RESULT:
Thus the program run successfully based on the Holt Winters Method model.
