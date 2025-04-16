# Use-Azure-Synapse-Link-for-Azure-CosmosDB

This project demonstrates how to analyze data stored in **Azure Cosmos DB** using **Azure Synapse Analytics**. With Synapse Link, you can query data in near real-time without extracting or duplicating it.

## Purpose

- Connect Azure Cosmos DB to Synapse Analytics using **Synapse Link**
- Analyze data using **Spark Notebooks** and **Serverless SQL Pool**
- Work with a sample sales dataset for demonstration purposes

## Technologies Used

- **Azure Cosmos DB** (NoSQL API)
- **Azure Synapse Analytics**
  - Spark Notebooks
  - Serverless SQL Pool
- **Apache Spark**
- **Synapse Link**
- **JSON Data Model**

## Getting Started

1. In Azure Portal:
   - Create a **Cosmos DB** account (NoSQL API)
   - Create a **Synapse Workspace**
   - Set up **Synapse Link** between Cosmos DB and Synapse

2. Upload the `sales_sample_data.json` file to your Cosmos DB container

3. In **Synapse Studio**:
   - Import the notebooks from the `notebooks/` directory
   - Start a Spark session and run the notebooks

4. Alternatively, run the query in `sql/serverless_openrowset_query.sql` using Serverless SQL Pool


👤 Author
Sefa Öztürk
IT Trainee | Azure Data Engineer in progress
📇 LinkedIn: linkedin.com/in/sefa-ozturk1972


## Sample Queries

### Spark SQL
```sql
SELECT category, SUM(quantity) as total_sold
FROM sales
GROUP BY category

----
### Serverless SQL (OPENROWSET)
SELECT *
FROM OPENROWSET(
    BULK 'https://<storage-url>/sales-data/',
    FORMAT='CSV'
) AS rows

## Notes
 - No need for a separate ETL process – Synapse Link keeps Cosmos DB in sync

 - You can explore and analyze data using either Spark or SQL

 - Make sure to flatten or transform nested JSON structures when needed







