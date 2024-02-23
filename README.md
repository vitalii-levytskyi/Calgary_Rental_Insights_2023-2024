# Calgary Rental Insights 2023-2024

Welcome to the README file for the Calgary Rental Insights project! This project aims to provide insights into rental properties in Calgary for the year 2023-2024. Below, you'll find information on the project setup, tools used, and steps taken.

## Project Overview
The project involves extracting data from an Excel file containing information about rental properties in Calgary for the specified period. This data is then transformed and loaded into a SQL Server database using Python scripts for ETL (Extract, Transform, Load) processes.

## Tools Used
- **SQL Server Management Studio 19 (SSMS)**: Installed on-premises for database management.
- **Visual Studio Code**: Utilized for writing and executing Python scripts.
- **Python Libraries**:
  - `pandas`: Used for data manipulation.
  - `sqlalchemy`: Employed for database interaction.
  
## Project Setup
1. **Excel Data**: The raw data is stored in an Excel file named `Raw_data_2024_02_20.xlsx`, located within the `Raw_data_excel` folder.
2. **Database Setup**:
   - A SQL Server database named `practice` was created in SSMS.
   - Authentication was configured for SQL Server Authentication.
3. **Database Schema and Table Creation**:
   - A schema named `RawData` was created.
   - Within the `RawData` schema, a table named `RentalProperties` was created to store the rental property data.

## ETL Process
The ETL process involves extracting data from the Excel file, transforming it, and loading it into the `RentalProperties` table in the `RawData` schema of the SQL Server database.

### Python Script for ETL

```python
import pandas as pd
from sqlalchemy import create_engine

# Replace these variables with your actual file path and database connection details
excel_file_path = 'c:/Users/vital/Desktop/Calgary_Rental_Insights_2023-2024/Raw_data_excel/Raw_data_2024_02_20.xlsx'
sql_server_connection_string = 'mssql+pyodbc://practice:qwerty@Xiaomi-Notebook/practice?driver=ODBC+Driver+17+for+SQL+Server'

# Read data from Excel file
df = pd.read_excel(excel_file_path)

# Create SQL Alchemy engine
engine = create_engine(sql_server_connection_string)

# Overwrite data into SQL Server
# Replace 'your_table_name' with the actual table name you want to insert data into
df.to_sql('RentalProperties', engine, schema='RawData', if_exists='replace', index=False)

print("Data successfully overwritten into SQL Server.")
```


## Troubleshooting
- **File Path Issue**: Initially, using a relative file path caused errors. Switching to an absolute file path resolved the problem.
- **Database Connection Issue**: Incorrectly specifying the ODBC driver in the connection string led to connection errors. Specifying the correct ODBC driver resolved this issue.
- **Schema Specification**: For proper table creation in the desired schema, it's essential to specify the schema in the `to_sql` method.

## Conclusion
With the completion of the ETL process, data from the Excel file has been successfully loaded into the SQL Server database. Further analysis and visualization can be performed using SQL queries and other data analysis tools.
Stay tuned for updates and additional functionalities as the project progresses!
Feel free to reach out for any further inquiries or assistance.

--- 
This README provides an overview of the project, detailing the steps taken, tools used, and issues encountered during the process. It aims to provide clarity and guidance to anyone interested in understanding or contributing to the project. If you have any questions or suggestions, please don't hesitate to contact me. Thank you for your interest in Calgary Rental Insights 2023-2024!
