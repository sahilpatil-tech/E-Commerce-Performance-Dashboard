# E-Commerce-Performance-Dashboard


An end-to-end Power BI portfolio project built with the Brazilian E-Commerce Public Dataset by Olist. The report explores sales performance, products, sellers, customer geography, reviews, payments and delivery operations.

## Project Overview

This project uses Power BI to analyse Brazilian e-commerce performance and provide business insights into:

- Revenue, orders and customer activity
- Product category and seller performance
- Customer distribution across Brazilian states
- Customer reviews and satisfaction
- Delivery performance, delays and freight costs

## Dataset

**Source:** [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

The project uses nine source CSV files:

1. `olist_orders_dataset.csv`
2. `olist_order_items_dataset.csv`
3. `olist_customers_dataset.csv`
4. `olist_products_dataset.csv`
5. `olist_sellers_dataset.csv`
6. `olist_order_payments_dataset.csv`
7. `olist_order_reviews_dataset.csv`
8. `olist_geolocation_dataset.csv`
9. `product_category_name_translation.csv`

The dataset covers Brazilian e-commerce orders from 2016 to 2018.

**Dataset attribution and licence:** The dataset is provided by Olist under the CC BY-NC-SA 4.0 licence. Review the licence terms before redistributing the dataset, PBIX file or adapted materials. The original CSV files are not included in this repository.

## Tools and Technologies

- Power BI Desktop
- Power Query
- DAX
- Data modelling
- Interactive dashboards and visualisations
- Performance Analyzer

## Data Cleaning and Transformation

The nine CSV files were imported into Power BI and cleaned using Power Query.

Key transformation steps:

- Checked and corrected column data types.
- Kept identifiers as text, including ZIP code prefixes.
- Converted date/time and numeric columns to appropriate data types.
- Applied Trim and Clean operations to text columns.
- Preserved meaningful null values, such as delivery dates for orders that were not delivered.
- Promoted the first row to headers in the category translation file.
- Merged English product category translations into the products table.
- Created an order purchase date column for date-based analysis.

## Data Model

The project uses a fact and dimension table structure.

### Fact Tables

- `Fact_Orders`
- `Fact_OrderItems`
- `Fact_Payments`
- `Fact_Reviews`

### Dimension Tables

- `Dim_Date`
- `Dim_Customers`
- `Dim_Products`
- `Dim_Sellers`

### Supporting Queries

- `Geolocation_Raw`
- `Category_Translation`

The model contains seven active relationships:

1. `Dim_Date` → `Fact_Orders`
2. `Dim_Customers` → `Fact_Orders`
3. `Fact_Orders` → `Fact_OrderItems`
4. `Dim_Products` → `Fact_OrderItems`
5. `Dim_Sellers` → `Fact_OrderItems`
6. `Fact_Orders` → `Fact_Payments`
7. `Fact_Orders` → `Fact_Reviews`

Relationships use one-to-many cardinality and single-direction filtering.

## Dashboard Pages

### 1. Executive Overview

Provides a high-level view of business performance through:

- Total Revenue
- Total Orders
- Total Customers
- Average Order Value
- On-Time Delivery Rate
- Monthly Revenue Trend
- Orders by Status
- Revenue by Product Category
- Top 10 States by Orders
- Delivery and satisfaction KPIs

### 2. Product & Seller Performance

Analyses product and seller performance through:

- Revenue by Product Category
- Top 10 Products by Revenue
- Top 10 Sellers by Revenue
- Total Revenue
- Products Sold
- Total Freight
- Average Review Score
- Product category detail table

### 3. Customer & Geographic Analysis

Provides insights into customer behaviour and geographical performance:

- Total Customers
- Repeat Customers
- Repeat Customer Rate
- Average Review Score
- Top 10 States by Customers
- Revenue by Customer State
- Review Score Distribution
- Average Review Score by Category
- Customer detail table

### 4. Delivery & Operations

Focuses on order fulfilment and delivery performance:

- Delivered Orders
- Late Delivery Rate
- On-Time Delivery Rate
- Average Delivery Days
- Average Delivery Delay Days
- Late Delivery Rate by State
- Average Delivery Days Trend
- Freight Cost by Product Category
- Order Status Summary

### 5. Product Details

An interactive drill-through page providing product-level analysis, including revenue, products sold, freight, review scores and monthly revenue trends.

### 6. Product Tooltip

A report-page tooltip displaying additional product metrics when users hover over product-related visuals.

## Key DAX Measures

The report includes measures for:

### Sales Performance

- Total Revenue
- Total Freight
- Total Orders
- Total Products Sold
- Average Order Value
- Total Payment Value
- Average Payment Value

### Customer Analysis

- Total Customers
- Repeat Customers
- Repeat Customer Rate
- Date-aware customer measures

### Delivery Performance

- Delivered Orders
- Valid Delivered Orders
- Late Delivered Orders
- On-Time Delivered Orders
- Late Delivery Rate
- On-Time Delivery Rate
- Average Delivery Days
- Average Estimated Delivery Days
- Average Delivery Delay Days

### Customer Satisfaction

- Average Review Score
- Total Reviews
- Positive Reviews
- Positive Review Rate

### Time Intelligence

- Previous Month Revenue
- Revenue Growth
- Revenue Growth Percentage

### Order Status

- Cancelled Orders
- Cancelled Order Rate

### Freight Analysis

- Average Freight per Order Item

## Interactive Features

The dashboard includes:

- Year, state, category, seller and order status slicers
- Page navigation
- Product-level drill-through
- Report-page tooltips
- Dynamic titles
- Top N visual filters
- Interactive charts and KPI cards

## Business Insights

The following findings should be completed using actual values from the dashboard:

1. **Revenue Performance:** [Insert the highest-revenue product category and its revenue.]
2. **Geographic Performance:** [Insert the state with the highest customer count.]
3. **Seller Performance:** [Insert the leading seller or top-seller finding.]
4. **Delivery Performance:** [Insert the overall late delivery rate and relevant state-level findings.]
5. **Customer Satisfaction:** [Insert the highest- and lowest-rated product categories.]

Each finding should include its business implication and a practical recommendation supported by the data.

## Validation and Quality Checks

The project included:

- Validation of key DAX measures.
- Reconciliation of revenue, payment and order totals.
- Checks of delivery KPI calculations.
- Testing of slicers across report pages.
- Testing of product drill-through and tooltips.
- Review of visual interactions.
- Performance Analyzer review.
- Saving and reopening the final PBIX file.

## Important Definitions and Limitations

- **Total Revenue** is calculated using `Fact_OrderItems[price]`. It represents item-price revenue and excludes freight.
- **Total Payment Value** comes from payment records and may differ from Total Revenue because payments can include freight and other payment-related amounts.
- **Total Products Sold** counts rows in `Fact_OrderItems`. The source does not provide a quantity field in this table, so this measure represents order-item lines, not individual physical units.
- The model uses single-direction relationships. Product and seller filters can affect order-item measures without automatically filtering order-level measures such as Total Orders.
- Date-aware customer measures use DAX filter transfer to account for relationship direction.
- The dataset covers 2016–2018 and should not be interpreted as current market performance.
- Observed patterns do not necessarily establish the causes of delivery delays, customer reviews or sales performance.

## Repository Structure

```text
brazilian-ecommerce-powerbi-dashboard/
│
├── README.md
│
├── screenshots/
│   ├── executive-overview.png
│   ├── product-seller-performance.png
│   ├── customer-geographic-analysis.png
│   ├── delivery-operations.png
│   └── product-details.png
│
├── documentation/
│   ├── data-model.png
│   ├── dax-measures.md
│   └── project-methodology.md
│
└── powerbi/
    └── (PBIX file, only if licence and sharing terms permit)
```

## How to Explore the Project

1. Open the screenshots folder to view the dashboard pages.
2. Review the data model and project methodology documentation.
3. If the PBIX file is included, open it using Power BI Desktop.
4. Use the page navigator and slicers to explore the report.
5. Use the Product Details drill-through feature to explore individual products.

## Author

**Sahil Patil**

