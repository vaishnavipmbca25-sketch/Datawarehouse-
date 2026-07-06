# Snowflake Olist E-Commerce Data Warehouse

## Overview
This project implements an end-to-end Data Warehouse for the Kaggle Olist E-Commerce Dataset using Snowflake. It follows a scalable Medallion Architecture (Bronze, Silver, Gold) to ingest, clean, and model raw data into a Star Schema, connected to Power BI for automated reporting.

## 🏗️ Project Architecture
**View the interactive architecture diagram here:** [Lucidchart Architecture Diagram](https://lucid.app/lucidchart/dd732790-6029-41cb-a24d-17443a5a0e47/edit?viewport_loc=-1708%2C-695%2C4008%2C1756%2C0_0&invitationId=inv_d4d90fe0-846b-405c-b81c-c3754955ff10)

## 🛠️ Tech Stack
 *Data Warehouse & Orchestration:** Snowflake (Stored Procedures, Tasks)
 *Data Source:** Kaggle (CSV)
 *Transformation:** SQL (`COPY INTO`, `COALESCE`)
 *Analytics:** Power BI

## ⚙️ Workflow
1. *Ingestion:* Raw CSVs are uploaded to a Snowflake Internal Stage and loaded into the Bronze layer.
2. *Medallion Architecture:*
   🥉 Bronze (Raw): Stores unmodified original data for validation.
   🥈 Silver (Cleaned): Removes invalid records, handles `NULL` values via `COALESCE`, and standardizes data formats.
   🥇 Gold (Star Schema): Models data into Dimension tables (e.g., `DIM_CUSTOMER` with SCD Type 1, `DIM_PRODUCT`) and a Fact table (`FACT_ORDER_ITEMS`) using surrogate keys.
3. *Automation & Validation:* Primary/foreign keys and row counts are validated. The entire ETL pipeline runs automatically every day via a Snowflake Task executing a Stored Procedure.
4. *Monitoring:* Snowflake Notification Integration triggers automated email alerts for pipeline successes or failures.
5. *Reporting:* Power BI connects directly to the Gold Layer to visualize sales, delivery performance, and customer insights.

## 📊 Key Features
* Automated Daily ETL Pipeline
* Medallion Data Modeling & Star Schema Design
* Slowly Changing Dimensions (SCD Type 1)
* Automated Email Alerting & Data Validation
