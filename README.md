# Sales Database Schema Design
Designed a database schema for storing and analyzing the sales &amp; understanding customer behavior for a major footwear manufacturer. 
## 1.	CASE STUDY SCENARIO
A major footwear manufacturer is losing opportunities to increase sales and decrease cost by not having adequate infrastructure to understand customer shopping behavior.
### 1.1.	BUSINESS GOAL
How can we track the performance of individual products to identify the most popular products as well as the low performers to adjust pricing strategy, inventory, description/image, and marketing campaigns?

### 1.2.	INFORMATION REQUIREMENT
Once the goal has been established, we may want to understand how end users will examine the data in the analytic work space, what types of business analysis questions they want to answer to achieve the end goal of increasing profit.
* What is the percent of total sales for any item, product family, or product class in any month, quarter or year? How does this percent of sales differ from a year ago?
*	What items were most profitable in any month, quarter, or year in any geographic area? 
*	How do product seasonal sales patterns vary by geographic location? 
*	Who are the customers that buy a specific product based on Age, Segment & geographic location?
*	What products are more likely to be bought together?
*	What product has maximum refunds?
*	What are the top performing products across different platforms?

### 1.3.	IDENTIFYING REQUIRED BUSINESS FACTS
#### 1.3.1.	What is the percent of total sales for any item, product family, or product class in any month, quarter or year? How does this percent of sales differ from a year ago?
For any product that has entry in ‘Order_has_Product’ table, By joining Product table for ‘Category’ and Order table’s ‘Shipping address’ (For geographic location ) , ‘transaction_datetime’(for time series) , ‘channel’(online/store – for distribution channel) could be retrieved for analysis purpose.

<p align="center">
  <img src="https://user-images.githubusercontent.com/39995308/54904315-69985880-4e9b-11e9-86c8-a63a2c4f8d48.png?raw=true" />
</p> 
<br />

*Figure 1-Total Sales of any item or product category across geographical locations, distribution channels & time of the year*

#### 1.3.2.	What items were most profitable in any month, quarter, or year in any geographic area? 
Product price could be retrieved to compare against sales data as retrieved in question 1. We can also query the total sales data from order table, so that we can perfectly control the sales number for any product.
#### 1.3.3.	How do product seasonal sales patterns vary by geographic location? 
The time series sales data as retrieved in question 1 could be binned in seasons to study variations across geographic locations (based on shipping address in the order table).
When we have that information, we can adjust our inventory accordingly to reduce the shipping cost. For example, we can increase swimming clothes inventory in warehouse around west coast when the summer is coming, or we can add more weather resistant appeals at locations that is going to have bad weathers.
#### 1.3.4.	Who are the customers that buy a specific product based on segmentation, such as Age, location, income, etc?
By joining sales data (as retrieved in question 1) with Customer table attributes such as age (based on ‘dob’ in customer table), segment (‘customer_classification’) & geographical location (‘shipping address zip code’ in order address table join) could be analyzed.
#### 1.3.5.	What products are more likely to be bought together?
By calculation correlation among different products in order table, we may have a set of products that are more likely to be bought together. So that we can add the related products under “things you might be interested” section to increase total sales.
#### 1.3.6.	What product has highest return rate or maximum amount of refunds 
Refund table data could be retrieved to analyze maximum against a product
<p align="center">
  <img src="https://user-images.githubusercontent.com/39995308/54904898-e8da5c00-4e9c-11e9-9879-02ebd68841ba.png?raw=true" />
</p> 
<br />
<p align="center">
<i>
Figure 2: Refund table to study refunds against a product
</i>
</p> 

#### 1.3.7.	What are the top performing products across different platforms?
Sales data (As achieved by joining product & order table) has an attribute called ‘channel’ that would have values as Store or Online to give top performing products across different products
	
### 1.4.	DATABASE SCHEMA
<p align="center">
  <img src="https://user-images.githubusercontent.com/39995308/54905318-fb08ca00-4e9d-11e9-8af2-062a6dbcf0a8.png?raw=true" />
</p> 
<br />
<p align="center">
<i>
Figure 3:Database Schema
</i>
</p> 


