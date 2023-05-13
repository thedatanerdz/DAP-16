DAP 16 - Tracking stock performance of historical daily prices of Nasdaq-traded stocks and ETFs

Industry 
Finance | Stock market | Investments 

Skills
Tableu | Big data | Excel | Dashboard | Data visualization | Data cleaning | Data manipulation 

Problem statements
Monitor Google, Facebook, Twitter, Tesla, Apple and Nvidia stocks performance using an interactive dashboard. 

Data Description
Historical daily prices of Nasdaq-traded stocks and ETFs. This dataset contains historical daily prices for all tickers currently trading on NASDAQ. The up to date list is available from nasdaqtrader.com. The historic data is retrieved from Yahoo finance via yfinance python package. It contains prices for up to 01 of April 2020. If you need more up to date data, just fork and re-run data collection script also available from Kaggle.
Data Structure
The date for every symbol is saved in CSV format with common fields:
Date - specifies trading date
Open - opening price
High - maximum price during the day
Low - minimum price during the day
Close - close price adjusted for splits
Adj Close - adjusted close price adjusted for both dividends and splits.
Volume - the number of shares that changed hands during a given day

All that ticker data is then stored in either ETFs or stocks folder, depending on a type. Moreover, each filename is the corresponding ticker symbol. At last, symbols_valid_meta.csv contains some additional metadata for each ticker such as full name.
Methods
DATA MANIPULATION IN PANDAS PYTHON

NOTE: 
verify manipulation on dataframe using apple.head() in between manipulation functions.
Use for loop to add columns to all DataFrames  (to simplify and optimize code)

Adding the moving average 

In the stock market, a moving average (MA) is a commonly used technical indicator that helps smooth out price fluctuations and identify trends. The MA50 and MA200 refer to the 50-day and 200-day moving averages, respectively.

The MA50 is calculated by adding up the closing prices of the last 50 trading days and dividing the sum by 50. This moving average provides a short-term view of the price trend and is useful for identifying potential buying or selling opportunities.

The MA200, on the other hand, is calculated by averaging the closing prices of the last 200 trading days. This moving average provides a longer-term view of the price trend and is useful for identifying the overall direction of the market.

Traders and analysts often use these moving averages to identify support and resistance levels, which can help inform their trading decisions. For example, if the stock price is above its MA50 and MA200, this could indicate a bullish trend, while if it is below both moving averages, this could indicate a bearish trend. 

The moving average was calculated using the expression df.column.rolling(50).mean(). In Python, df.column.rolling(50).mean() is a pandas method that is used to calculate the rolling mean of a particular column in a pandas DataFrame over a specified window size, which is 50 in this case.

This method returns a new DataFrame with a new column that contains the rolling mean of the values in the specified column. The rolling mean is calculated by taking the mean of the values in a sliding window of size 50 that moves across the DataFrame row-by-row.

Getting 'Previous day close price'
'Previous day close price' column is added via a shifting column named ‘Close’. In Python, df.column.shift(1) is a pandas method that is used to shift the values of a particular column in a pandas DataFrame by a specified number of periods, which is 1 in this case. This method returns a new DataFrame with the values in the specified column shifted forward by one row.

Getting 'Change in price'
 'Change in price' column added via subtracting 'Previous day close price' column from ‘Close’ column  to track how much stock price changed during the day. 

Getting 'Percent change in price'
'Percent change in price' column added via the expression df.Close.pct_change(). In Python, df.Close.pct_change() is a pandas method that is used to calculate the percentage change between consecutive values in a column of a pandas DataFrame.

This method returns a new DataFrame with a new column that contains the percentage change between consecutive values in the specified column.

Getting 'Previous day volume'
'Previous day volume'  column is added via a shifting column named Volume. In Python, df.column.shift(1) is a pandas method that is used to shift the values of a particular column in a pandas DataFrame by a specified number of periods, which is 1 in this case. This method returns a new DataFrame with the values in the specified column shifted forward by one row.

Getting 'Change in volume'
 'Change in volume' column added via subtracting 'Previous day volume' column from ‘Volume’ column  to track how much stock price changed during the day. 

Getting 'Percent change in volume' 
'Percent change in volume'  column added via the expression df.Close.pct_change(). In Python, df.Volume.pct_change() is a pandas method that is used to calculate the percentage change between consecutive values in a column of a pandas DataFrame.

This method returns a new DataFrame with a new column that contains the percentage change between consecutive values in the specified column.

Exporting the manipulated dataframes  to .csv file to use in dashboard 
Using the expression apple.to_csv('Apple.csv'). 

B. DASHBOARD TABLEAU 
Volume multiple line chart 
Union all data sources 
Rename title column to company with alias removing file extension 
Add Date filter field to only extract 2016 to 2020 (5 out 41 years)
Put in start and end date parameters 
Put in study period calculated field using

If [Date] >= [start date] AND [Date] <= [End date] THEN 1
ELSE 0 
END



