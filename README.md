# StockSight: Unveiling Financial Insights Through Data Visualization

Unlock the power of data-driven decision-making in finance with our project on Extracting and Visualizing Stock Data. By seamlessly integrating Python libraries like yfinance and BeautifulSoup, we empower users to effortlessly extract historical stock data and revenue information for companies like Tesla and GameStop. 

Through intuitive visualization techniques, our project enables users to gain actionable insights, aiding in strategic investment decisions. Join us in revolutionizing the way you approach financial analysis!

## Description:
The project focuses on extracting essential stock data and revenue information, followed by visualizing the data through graphs. It involves utilizing various Python libraries for data extraction, web scraping, and graph plotting. The primary goal is to provide a clear representation of stock performance and revenue trends for analysis and decision-making purposes.

## Table of Contents:

Define a Function that Makes a Graph: Defines a function to create a graph for visualizing stock data and revenue information.

**Question 1:** Use yfinance to Extract Stock Data: Utilizes the yfinance library to extract historical stock data for a specified ticker symbol (e.g., Tesla - TSLA).

import yfinance as yf

# Create a Ticker object for Tesla (TSLA)
tesla = yf.Ticker("TSLA")

# Extract historical stock data
tesla_data = tesla.history(period='max')

# Reset index and display the first five rows
tesla_data.reset_index(inplace=True)
tesla_data.head()



**Question 2:**  Use Webscraping to Extract Tesla Revenue Data: Performs web scraping to extract Tesla's revenue data from a specified webpage and preprocesses the data for analysis.

import requests
from bs4 import BeautifulSoup
import pandas as pd

# URL for Tesla revenue data
url = 'https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/labs/project/revenue.htm'

# Download and parse HTML data
html_data = requests.get(url).text
soup = BeautifulSoup(html_data,'html5lib')

# Extract table with Tesla revenue
tesla_revenue = pd.read_html(str(soup))[1]

# Rename columns and preprocess data
tesla_revenue = tesla_revenue.rename(columns={"Tesla Quarterly Revenue (Millions of US $)":"Date","Tesla Quarterly Revenue (Millions of US $).1":"Revenue"})
tesla_revenue["Revenue"] = tesla_revenue["Revenue"].str.replace("$",'').str.replace(",", "")
tesla_revenue.dropna(inplace=True)
tesla_revenue = tesla_revenue[tesla_revenue['Revenue'] != ""]

# Display the first and last five rows
tesla_revenue.head()
tesla_revenue.tail()


**Question 3:** Use yfinance to Extract Stock Data: Similar to Question 1, this extracts historical stock data for another specified ticker symbol (e.g., GameStop - GME) using yfinance.

# Create a Ticker object for GameStop (GME)
GameStop = yf.Ticker("GME")

# Extract historical stock data
gme_data = GameStop.history(period='max')

# Reset index and display the first five rows
gme_data.reset_index(inplace=True)
gme_data.head()



**Question 4:** Use Webscraping to Extract GME Revenue Data: Utilizes web scraping to extract GameStop's revenue data from a webpage, preprocesses the data, and prepares it for visualization.

# URL for GameStop revenue data
url ="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/labs/project/stock.html"

# Download and parse HTML data
html_data = requests.get(url).text
soup = BeautifulSoup(html_data,"html5lib")

# Extract table with GameStop revenue
gme_revenue = pd.read_html(str(soup))[1]

# Rename columns and preprocess data
gme_revenue = gme_revenue.rename(columns={"GameStop Quarterly Revenue (Millions of US $)":"Date","GameStop Quarterly Revenue (Millions of US $).1":"Revenue"})
gme_revenue["Revenue"] = gme_revenue["Revenue"].str.replace("$", '').str.replace(",","")
gme_revenue.dropna(inplace=True)
gme_revenue.head()
gme_revenue.tail()



**Question 5:** Plot Tesla Stock Graph: Utilizes the previously defined function to plot the stock graph for Tesla, incorporating historical stock data and revenue information.

# Use the previously defined make_graph function to plot Tesla stock graph
make_graph(tesla_data, tesla_revenue, 'Tesla')



**Question 6:** Plot GameStop Stock Graph: Similar to Question 5, this plots the stock graph for GameStop, incorporating relevant data.

# Use the previously defined make_graph function to plot GameStop stock graph
make_graph(gme_data, gme_revenue, 'GameStop')



The project involves extracting and visualizing stock data using Python. It encompasses the following key steps:

**Data Extraction:** Utilizing yfinance library to extract historical stock data for Tesla (TSLA) and GameStop (GME) ticker symbols.

**Web Scraping:** Scraping revenue data for Tesla and GameStop from specified web pages using requests and BeautifulSoup libraries.

**Data Preprocessing:** Cleaning and preprocessing the extracted data to ensure consistency and accuracy.

**Visualization:** Plotting stock graphs for Tesla and GameStop, incorporating historical stock data and revenue information using a custom function make_graph.



This project serves as a practical exercise in data extraction, preprocessing, and visualization, vital for decision-making in finance and data analysis. The estimated time for completion is approximately 30 minutes.

















