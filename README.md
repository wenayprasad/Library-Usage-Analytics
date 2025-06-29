📘 README – Library Usage Analytics (Power BI Project)
📌 Project Overview
This Power BI dashboard analyzes the library usage patterns based on book checkouts, popular genres, and late returns. The visual insights help track borrowing behavior and highlight improvement areas for library operations.

🎯 Objectives
Monitor book borrow trends over time

Identify top genres and authors

Track late return behavior using KPIs

Analyze borrowing by month and genre

🗂️ Dataset Details
Project uses 3 Excel/CSV files:

Books.csv – BookID, Title, Author, Genre

Borrowers.csv – BorrowerID, Name, Age, Gender

CheckoutLogs.csv – LogID, BookID, BorrowerID, CheckoutDate, DueDate, ReturnDate

📌 Data simulated manually for educational purposes.

📊 Power BI Dashboard Features
✅ KPIs
📚 Total Checkouts

⏰ Late Return % (Calculated from DueDate vs ReturnDate)

🎭 Top Genre (Based on max checkout count)

✅ Visuals
📊 Clustered Column Chart – Top Authors by total checkouts

📈 Line Chart – Borrowing trend over time

📅 Matrix – Genre-wise monthly borrow count

💳 Card Visuals – KPI summary

🔘 Slicer – Optional filters by Genre or Month (if added)

⚙️ DAX Measures & Calculations
DAX
Copy code
-- Late Return Flag (Column)
LateReturnFlag = IF(CheckoutLogs[ReturnDate] > CheckoutLogs[DueDate], 1, 0)

-- Late Return %
Late Return % = 
DIVIDE(SUM(CheckoutLogs[LateReturnFlag]), COUNTROWS(CheckoutLogs)) * 100

-- Top Genre
Top Genre = 
CALCULATE(
    VALUES(Books[Genre]),
    TOPN(
        1,
        SUMMARIZE(Books, Books[Genre], "Total", CALCULATE(COUNTROWS(CheckoutLogs))),
        [Total], DESC
    )
)
🧠 Insights You Can Derive
Which genres are most borrowed in which month?

Which author is most popular?

How much of the borrowing activity is returned late?

Are borrowings increasing or declining over time?

📁 Files Included
Books.csv

Borrowers.csv

CheckoutLogs.csv

Library_Usage_Analytics.pbix

README.md

🔖 Tools Used
Microsoft Power BI

Microsoft Excel

DAX for KPIs

Data Modeling using relationships

📌 Author
Vinay Prasad
