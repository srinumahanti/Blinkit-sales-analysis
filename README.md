# Blinkit Sales Analysis Dashboard

![Blinkit Overview](./Blinkit%20overview.png)

## 📌 Project Overview
This project analyzes **Blinkit sales data** using **Power BI** to uncover insights into product performance, outlet trends, and customer behavior.  
The dashboard provides interactive filters, KPIs, and visualizations that help decision-makers track performance, optimize sales strategies, and identify growth opportunities.

---

## 🎯 Objectives
- Build an **interactive Power BI dashboard** for Blinkit sales performance.  
- Track **key KPIs** such as Total Sales, Average Sales, Number of Items, and Average Rating.  
- Analyze sales by **item type, fat content, outlet size, outlet location, and outlet type**.  
- Study **outlet establishment trends** across years.  
- Provide stakeholders with **data-driven insights** to support sales growth and operational efficiency.  

---

---

## 📊 Dashboard Features
- **KPI Cards (Top):**
  - Total Sales (1.20M)  
  - Avg Sales ($141)  
  - No of Items (8523)  
  - Avg Rating (3.9)  

- **Filters Panel (Left):**
  - Outlet Location Type  
  - Outlet Size  
  - Item Type  

- **Visualizations (Middle & Right):**
  - Donut Chart — Sales by Fat Content (Low Fat vs Regular).  
  - Bar Chart — Sales by Item Type (Fruits, Snacks, Dairy, etc.).  
  - Bar Chart — Sales by Fat Content by Outlet.  
  - Line Chart — Outlet Establishment trend (2010–2020).  
  - Donut Chart — Sales by Outlet Size (Small, Medium, High).  
  - Bar Chart — Sales by Outlet Location (Tier 1, 2, 3).  
  - Matrix Table — Outlet Type breakdown with Total Sales, No of Items, Avg Sales, Avg Rating, Item Visibility.  

---

## 🛠️ Data Model
The dataset includes (or should include) the following columns:  
- `Item_Identifier`  
- `Item_Type`  
- `Item_Fat_Content`  
- `Item_Visibility`  
- `Item_Outlet_Sales` (Total Sales)  
- `Outlet_Identifier`  
- `Outlet_Size` (Small, Medium, High)  
- `Outlet_Location_Type` (Tier 1, Tier 2, Tier 3)  
- `Outlet_Type` (Grocery Store, Supermarket Type1/2/3)  
- `Outlet_Establishment_Year`  
- `Rating`  

---

## 📐 DAX Measures Used
```DAX
-- Total Sales
Total_Sales = SUM(Sales[TotalPrice])

-- Average Sales
Avg_Sales = AVERAGEX(Sales, Sales[TotalPrice])

-- Number of Items
No_Of_Items = DISTINCTCOUNT(Sales[Item_Identifier])

-- Average Rating
Avg_Rating = AVERAGE(Sales[Rating])

-- Sales by Fat Content
Sales_By_Fat = 
CALCULATE(
    SUM(Sales[TotalPrice]),
    ALLEXCEPT(Sales, Sales[Fat_Content])
)

-- Sales by Outlet Size
Sales_By_OutletSize = 
CALCULATE(
    SUM(Sales[TotalPrice]),
    ALLEXCEPT(Sales, Sales[Outlet_Size])
)

-- Sales by Outlet Location
Sales_By_Location = 
CALCULATE(
    SUM(Sales[TotalPrice]),
    ALLEXCEPT(Sales, Sales[Outlet_Location])
)

-- Sales by Item Type
Sales_By_ItemType = 
CALCULATE(
    SUM(Sales[TotalPrice]),
    ALLEXCEPT(Sales, Sales[Item_Type])
)

