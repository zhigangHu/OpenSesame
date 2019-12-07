# Overview and Motivation
For human traders it is a natural desire to visualize the stock market. Over the years, many stock market “heat maps” have cropped up on the web. Usually, they come and go. One of the key reasons appears to be that many of these efforts heavily focus on the graphics and miss the elephant in the room, which is functionality. The main challenge with stock market visualization tools is that the number of stocks is large (in thousands), far larger than what a (typical) human can meaningfully digest. Exacerbate that with convoluted (albeit fancy) graphics and it becomes virtually impossible to follow such a “heat map”. It is simply too much information to process
The data is not always the boring number. Sometimes you can earn the money by mining them. So we called this “Data value Digging”. 
Many people are very interesting in investing stock market, for example Dow 30, Nasdaq, S&P 500. But most of the investors have no idea what kind of stock I should buy, what time is the best time to sell. If they don’t make clear of these questions they will lost money instead earning money.

# Related Work
In recent years, by the development of Machine Learning technology, people pay more attention in the Business Intelligence(BI). Business intelligence (BI) comprises the strategies and technologies used by enterprises for the data analysis of business information. BI technologies provide historical, current and predictive views of business operations. Common functions of business intelligence technologies include reporting, online analytical processing, analytics, data mining, process mining, complex event processing, business performance management, benchmarking, text mining, predictive analytics and prescriptive analytics. BI technologies can handle large amounts of structured and sometimes unstructured data to help identify, develop and otherwise create new strategic business opportunities. They aim to allow for the easy interpretation of these big data. Identifying new opportunities and implementing an effective strategy based on insights can provide businesses with a competitive market advantage and long-term stability.
In the Business Intelligence process, the first and a very important processing is the showing the data, which means the data visualization. Only information that is absolutely necessary for the contextual understanding of the data will be depicted. The general rule for BI displays is “less is more.” Eliminate as much visual clutter as possible and let the data present itself as simply as possible. The purpose of business intelligence systems is to relate a clear message about data that is easily understood and interpreted consistently across the highest percentage of users. It is not about entertainment or visual interest for the sake of decoration. So through this project, we want to make a good attempt by using the technology we learned from the course to explore the data visualization technology using in BI process.
### Yahoo Finance
https://finance.yahoo.com/

### Visual Learning Center
https://visme.co/blog/business-intelligence-visualization/

### Paper:Visualization of Stock Market Charts
https://pdfs.semanticscholar.org/157a/1cb155ea34d33eacce0c870e8d6fd60a6c13.pdf

# Questions: 
 ## Question 1: How to find effective method to discover the corelationship among the different companies.
 ### In the stock market, there are many different companies in the market. Some of them have similar economic area. The investment should invest in the similar economic field companies to disperse the investment risky.
 At the original design, we try to use the scatter plot matrix to show the pair wise relationship between the company.
 ![Image text](https://github.com/zhigangHu/OpenSesame/blob/master/OriginalDesign/IMG_20191111_230154.jpg)
 ### But in the practise, we found because the dataset is very huge, and the svg field is limited. So it is very difficult to show all the companies in just one scatter matrix chart, and it make the audience can not find the correlation effective.
 ### So at last, we use the AP clustering method in the end design and visulization the result.
 
 ## Question2:How to show the insight of data to the normal audience
 ### In our project objective, we want to show the history data to the potential investor to let them know what is the good investment opportunity. But most of them cannot find the exact result just from some normal chart of stock. 
 ### So we implement 3 kinds of the Indicator chart:Average Direction Index(ADX),Arron,ATR Trailing Stop. After tons of data processing, we visualize the result by 3 different kind of chart. From these chart, the investment can easily find out what is good investment opportunity and what is profit in the investment.
 
 ## Question3: How to show the huge data in one chart.
 ### We scrapted the companies's stock market trade data from date '09/21/2015' to current time(more dataset more precision in the machine learning, this project is the step to predict the stock market). How to show all the data in the limited SVG field is a big problem we must handle with.
 ### So we decide to use the D3 interactive function to let the user choose the data area they want to look inside by using d3.zoomin() and d3.xbrush() function. 

# Data

### Source
In this project, we scraped the data from the very famous finance website: https://finance.yahoo.com/ .From the website we scraped top 6 high tech company: Apple Inc(AAPL), Alphabet Inc.(GOOG), Facebook Inc.(FB), Microsoft Corporation(MSFT), Amazon.com Inc.(AMZN) and Ali baba(BABA).  Since the dataset of stock market is very huge, so we just scraped all the company’s data from start date: 09-20-2015. After scraped data, we put them into 6 independent .csv data files: AAPL.csv(Apple Inc.), GOOG.csv, FB.csv(Facebook Inc.),MSFT.csv(Microsoft Corporation), AMZN.csv().
The link of data is: 
https://github.com/zhigangHu/OpenSesame/tree/master/data

### scraping method
In the project,we used Python to scape the data from the the Yahoo Finance website through the pandas_datareader library:
https://pandas-datareader.readthedocs.io/en/latest/
The Jupyter Note file:
https://github.com/zhigangHu/OpenSesame/blob/master/ScrapeData.ipynb

# Exploratory Data Analysis
### After scraping the dataset from Financial Yahoo website, we store the dataset into .csv data files.In each .csv file, there have 5 column: Date(trading date), Hign(The highest price in one trading date), Low(The lowest price in one trading date), Open(the stock price when market open), Close(the stock price when market close), Volume(the stock trading number in one trading date), Adj_Close(the close price after adjustment, most of them are same with Close, but sometime they are different.)
## Dataset for clustering 
We used the AP(Affinity Propagation) cluster method to find out the invest portfolio. But if we used all the column of dataset as clustering feature, it will take long time for computing, so we decided to just use 3 column of the dataset:Date, Open, Close for clustering. For have good clustering result, we scraped 56 different companies from the Financial Yahoo website.

# Design Evolution:
## The chart to show the price in every trading date
### Original Design
![Original Candle Stick](https://github.com/zhigangHu/OpenSesame/blob/master/OriginalDesign/IMG_20191111_230038.jpg)
### Candle Static Chart
https://zhiganghu.github.io/OpenSesame/Static_Candle_AAPL.html

## The chart to show the trend of price
### Original Design
