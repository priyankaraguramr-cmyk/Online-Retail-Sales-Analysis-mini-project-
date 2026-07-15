# Online-Retail-Sales-Analysis-mini-project-
Excel & Power BI Project — README
This project takes a raw e-commerce transaction dataset, cleans it in Excel, and builds an interactive Power BI dashboard to analyze sales performance, product popularity, and customer behaviour for a UK based online gift retailer.

Project Overview:
The Online Retail dataset contains around 541,000 transaction records from 1 December 2010 to 9 December 2011. The raw data was cleaned and prepared in Excel, then loaded into Power BI, where a star schema data model, DAX measures, and a three-page interactive report with click-through storytelling navigation were built to answer questions about sales trends, top products, and customer value.

Tools Used:
•	Microsoft Excel – data cleaning, transformation and pivot tables
•	Power BI Desktop – data modelling, DAX measures, report building
•	Power BI Service – publishing the report online
•	UCI Machine Learning Repository – source of the raw dataset

Dataset:
Attribute	Detail:
Source	Online Retail dataset, UCI Machine Learning Repository
Time period	1 December 2010 – 9 December 2011
Rows after cleaning	392,692 (from an original ~541,000 rows)
Grain	One row per product line item, per invoice

Columns:
Column	Description:
InvoiceNo	Unique transaction number. Numbers starting with C are cancelled orders.
StockCode	Unique product code.
Description	Product name.
Quantity	Units sold in the transaction line.
InvoiceDate	Date of the transaction.
UnitPrice	Price per unit, in GBP.
CustomerID	Unique customer number.
Country	Customer's country.
Sales	Quantity × UnitPrice, added during cleaning.
Year / Month Name / Quarter	Date breakdown columns added for reporting.

Project Structure:
Online-Retail-Analysis/
|-- Online_Retail_Raw.xlsx              (original dataset)
|-- Online_Retail_Cleaned.xlsx          (cleaned dataset - Excel stage)
|-- OnlineRetail_PowerBI.pbix           (Power BI report file)
|-- Online_Retail_PowerBI_Report.pdf    (exported dashboard, PDF)
|-- Online_Retail_Project_Document.docx (full project write up)
|-- README.docx                         (this file)

Data Cleaning (Excel):
•	Removed around 132,000 rows with a blank Customer ID.
•	Removed duplicate rows.
•	Removed cancelled orders (invoice numbers starting with C) and negative quantities.
•	Standardized the InvoiceDate column and added Year, Month Name and Quarter columns.
•	Added a calculated Sales column (Quantity × UnitPrice).
•	Checked and corrected data types across key columns.
•	Built pivot tables to check totals before moving to Power BI.

Power BI Data Model:
A star schema was built with one fact table and four dimension tables, joined on active one-to-many relationships:
•	FactSales – InvoiceNo, InvoiceDate, Quantity, UnitPrice, Sales, CustomerID, StockCode, Country
•	DimCustomer – CustomerID, Country
•	DimProduct – StockCode, Description
•	DimDate – Date, Month, Month Name, Quarter, Year
•	DimCountry – Country

DAX Measures:
12 measures were built for the report, including Total Sales, Total Orders, Distinct Customers, Average Order Value, Sales per Customer, Monthly/Quarterly/YTD Sales, and % of Total Sales.

Report Pages:
•	Sales Overview – KPI cards, monthly sales trend (with year to month drill down), country distribution, map, navigation buttons
•	Product Analysis – top products by sales (Top 10 filter applied), product detail table, treemap, navigation buttons
•	Customer Analysis – customers by country, KPI cards, top customers table

Interactivity:
•	Slicers for Year, Country and Month Name on each page
•	Drill down on the monthly sales trend chart (Year to Month level)
•	Bookmarks: Sales Overview - Default, Product Analysis - Default
•	Click-through storytelling navigation buttons on the Sales Overview and Product Analysis pages, linked to bookmarks (see Interactive Storytelling Navigation below)

Interactive Storytelling Navigation (Bookmarks + Buttons):
The Sales Overview and Product Analysis pages include a simple click-through navigation system built with Power BI Bookmarks and Buttons, so viewers can move between the two pages without using the page tabs.
1. Enable the required panes
In the View tab, under Show panes, enable Bookmarks and Selection (Filters is usually already enabled).

2. Create a bookmark for each page
i.	On the Sales Overview page, set the filters/slicers to the desired default view, open the Bookmarks pane and click Add. Rename it “Sales Overview - Default” and confirm Data and Display are checked.
ii.	On the Product Analysis page, set the desired default view, click Add in the Bookmarks pane, and rename it “Product Analysis - Default”.

3. Insert the navigation buttons
On the Sales Overview page, go to Insert > Buttons > Blank and add a small button. In the Format button pane, set Action > On = Type Bookmark, and Bookmark = “Sales Overview - Default”; add a text label such as “1” or “Overview”. Copy this button, place a second one beside it, then update its Action to point to “Product Analysis - Default” and change its label to “2” or “Products”.

4. Copy the buttons to the other page
Select both buttons on the Sales Overview page, copy them, and paste them in the same position on the Product Analysis page so both pages share identical navigation controls.

 5. Test the buttons
While editing in Power BI Desktop, a normal click only selects a button for formatting; hold Ctrl and click to trigger the bookmark. After publishing, or in Presentation Mode, a normal single click navigates as expected.

6. Publish the report
Use File > Publish (or the green Publish button), sign in if prompted, choose a workspace, and open the report in Power BI once publishing completes.

7. Verify in Power BI Service
Open the published report in the browser and click each button to confirm it navigates to the correct page and state. The browser URL should update with a bookmarkGuid parameter, confirming the bookmark navigation is working.

8. Optional enhancements applied
•	Descriptive button labels (“Overview” / “Products”) in place of “1” / “2”
•	A short narrative text box near the buttons, e.g. “Explore the story: Overview → Product Insights”
•	A Top N filter (Top 10 by Total Sales) applied to the top products chart on the Product Analysis page
•	Report shared with the team via the Share button, and scheduled refresh configured under Workspace > Dataset Settings
•	Key visuals pinned to a dashboard for an at-a-glance summary view

Key Insights:
•	Total sales for the period were about 9 million pounds, from around 19,000 orders and 5 million units sold.
•	The United Kingdom made up about 82% of total sales.
•	Paper Craft, Little Birdie and Regency Cakestand 3 Tier were the two top selling products by value.
•	A small group of customers generated a disproportionate share of total sales.

How to Use:
•	Open OnlineRetail_PowerBI.pbix in Power BI Desktop.
•	Use the Year, Country and Month Name slicers on each page to filter the data.
•	Click a year on the Monthly Sales Trend chart and use the drill down arrow to view month level detail.
•	Use the Bookmarks pane, or the on-page navigation buttons (“Overview” / “Products”), to jump between the Sales Overview and Product Analysis pages.
