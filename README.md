select * from details

select * from orders

--1.total sales
select  sum(Amount) as Total_Sales from Details 

--Total profit
select SUM(Profit) as Total_Profit from Details

--Total Quantity
select SUM(Quantity)as Total_Quantity from details

--Total sales by category

select category ,SUM(amount) as Total_Sales from details group by Category

--Top 5 Customer name by  Total sales

select Top 5 orders.CustomerName ,SUM(Details.amount) as total_sales from orders inner join details on orders.order_ID = details.order_ID group by orders.customerName
order by total_sales desc

--Total Sales By payment Mode
select PaymentMode, SUM(amount) as total_sales from details group by paymentMode

--Total Sales By Sub Category
select Sub_Category, SUM(amount) as total_sales from details group by Sub_Category order by Total_sales desc

--Tot 5 states By Total sales
select Top 5 orders.state, sum(details.amount) as total_sales from orders inner join Details on orders.Order_ID=Details.Order_ID group by Orders.State order by total_sales desc

--Top 5 city by total sales by total profit
select top 5 orders.city, sum(details.amount) as total_sales , sum(details.profit) as total_profit from orders inner join details on orders.Order_ID= details.order_ID
group by orders.city order by total_sales,total_profit desc
