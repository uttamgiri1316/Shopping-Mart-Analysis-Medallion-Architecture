# ShoppingMart Analytics – Microsoft Fabric Medallion Architecture

## Project Overview

ShoppingMart Analytics is a data analytics project developed using Microsoft Fabric. The project uses a medallion-style data architecture to ingest and process ShoppingMart data through the Bronze, Silver, and Gold layers and support business reporting through a KPI dashboard.

The project includes:
- A Fabric data pipeline for unstructured data ingestion into the Bronze layer.
- A Silver notebook for the Silver-layer processing.
- A Gold notebook for the Gold-layer processing.
- A Power BI dashboard presenting ShoppingMart analytics and KPI metrics.

> **Note:** This README documents the pipeline and dashboard details visible in the provided project materials. The exact transformations, notebook code, source file formats, and table names are not specified here; update those sections to match the implementation in your notebooks.

## Architecture

```text
ShoppingMart Source Files
        |
        v
Microsoft Fabric Data Pipeline
  - Lookup metadata
  - ForEach over unstructured files
  - Delete existing target file
  - Copy source files
        |
        v
Bronze Layer
(Raw ingested data)
        |
        v
Silver Notebook
(Cleaning and transformation)
        |
        v
Silver Layer
        |
        v
Gold Notebook
(Analytics-ready processing)
        |
        v
Gold Layer
        |
        v
Power BI – ShoppingMart Analytics KPI Dashboard
```

The diagram represents the project flow at a high level. The specific transformations and storage objects should be confirmed from the notebook implementation.

## Technologies Used

- **Microsoft Fabric** – Data engineering and analytics platform
- **Fabric Data Pipeline** – Orchestration and ingestion
- **Fabric Notebooks** – Silver- and Gold-layer processing
- **Lakehouse / OneLake** – Data storage (as configured in the workspace)
- **Power BI** – KPI dashboard and reporting
- **GitHub** – Project documentation and version control

## Data Ingestion – Bronze Layer

The pipeline shown in the Fabric Monitoring Hub is named:

`ShoppingMart_UnStructuredDataIngestBronzeLayer_copy1`

### Pipeline flow

1. **Lookup activity** – `Lookup_ShoppingMart_MetaDataU...` retrieves metadata used by the pipeline.
2. **ForEach activity** – `ForEachSourceUnStructuredFiles` iterates over the unstructured-file items.
3. **Delete activity** – `Delete_ExistingFile` removes an existing destination file before copying, according to the pipeline configuration.
4. **Copy activity** – `Copy_ShoppingMart_Unstr...` copies the source files to the configured destination.

The screenshot shows the pipeline run as **Succeeded** in the Monitoring Hub.

### Run details visible in the screenshot

| Property | Value |
|---|---|
| Pipeline | `ShoppingMart_UnStructuredDataIngestBronzeLayer_copy1` |
| Run status | Succeeded |
| Start time | October 31, 2026, 8:56:18 PM |
| End time | October 31, 2026, 8:56:51 PM |
| Overall run duration | Approximately 33 seconds |
| ForEach activity | Succeeded |
| ForEach duration | 22 seconds |
| Copy activities shown | Succeeded |
| Delete activities shown | Succeeded |

The run details are a record of the execution shown in the screenshot, not a guarantee of future runs.

## Medallion Data Processing

### 1. Bronze Layer

The Bronze layer is the ingestion layer. The Fabric pipeline copies source unstructured files into the configured Bronze destination.

**Pipeline:** `ShoppingMart_UnStructuredDataIngestBronzeLayer_copy1`

### 2. Silver Layer – Notebook

The Silver notebook is used for the next processing stage after ingestion.

Document the notebook implementation here:
- Notebook name: **Silver notebook** (replace with the exact notebook name)
- Input: Bronze-layer data
- Processing: Add the actual cleaning, validation, standardization, or transformation steps implemented in the notebook.
- Output: Silver-layer data in the configured destination.

### 3. Gold Layer – Notebook

The Gold notebook prepares data for analytics and reporting.

Document the notebook implementation here:
- Notebook name: **Gold notebook** (replace with the exact notebook name)
- Input: Silver-layer data
- Processing: Add the actual aggregations, KPI calculations, joins, or business logic implemented in the notebook.
- Output: Gold-layer data consumed by the reporting solution, as configured.

> Replace the descriptions above with the exact notebook activities and output table names before publishing if you want the README to reflect the implementation precisely.

## ShoppingMart Analytics KPI Dashboard

The supplied dashboard PDF is titled **Shopping Mart Analytics KPI Metrics**. It includes slicers for Year, Month, Day, Product Name, and Category.

### KPI cards

| KPI | Value shown in the dashboard |
|---|---:|
| Sum of TotalAmount (Total Sales) | $769.42K |
| Count of ProductID (Total Product Sold) | 2.939K |

### Dashboard visualizations

The dashboard contains the following visual sections:

- **Top 5 Products AvgRating** – product rating overview.
- **Top 5 Products by Stock Quality** – stock quantity by product.
- **Top 5 Products by Sales** – sales amount by product.
- **Category By Sales ($)** – sales comparison across categories.
- **Web Engagement** – engagement event distribution, including purchase, view, add-to-cart, and click.
- **Top 5 Customers By Sales** – customers ranked by sales amount.
- **Sales By Month** – monthly sales trend.
- **Social Sentiment** – positive, neutral, and negative sentiment distribution.

### Example dashboard values visible in the PDF

| Dashboard metric | Example value |
|---|---:|
| Category sales – Electronics | 168K |
| Category sales – Fashion | 186K |
| Category sales – Home Goods | 195K |
| Category sales – Sports | 220K |
| Top 5 Customers By Sales – displayed total | 54,528.11 |

Values are transcribed from the supplied dashboard PDF and may depend on the selected filters or report state.

## Repository Structure

A suggested GitHub repository structure is:

```text
ShoppingMart-Analytics/
├── README.md
├── pipeline/
│   └── UnstructuredDataIngestBronzeLayer.png
├── notebooks/
│   ├── Silver_Notebook.ipynb
│   └── Gold_Notebook.ipynb
└── reports/
    └── ShoppingMart_Analytics_LT_KPI.pdf
```

This is a suggested layout. Adjust the folders and filenames to match the files you upload to GitHub. Add any other pipeline JSON, source files, or screenshots only if they are part of your repository.

## Execution Flow

1. Configure the source and destination connections in Microsoft Fabric.
2. Run the `ShoppingMart_UnStructuredDataIngestBronzeLayer_copy1` pipeline to ingest the unstructured source files into the Bronze layer.
3. Run the Silver notebook using the ingested Bronze data.
4. Run the Gold notebook using the Silver-layer output.
5. Refresh or connect the Power BI report to the configured analytics data.
6. Review the ShoppingMart Analytics KPI dashboard.

The precise notebook execution order, parameters, and refresh method should follow the dependencies configured in your Fabric workspace.

## Monitoring and Validation

Use the **Monitoring Hub** in Microsoft Fabric to:
- Check pipeline run status.
- Review start and end times and durations.
- Inspect Lookup, ForEach, Delete, and Copy activity statuses.
- Open activity details when troubleshooting failures.

Validate the Silver and Gold notebook outputs against their expected schemas, row counts, and business logic. Confirm dashboard values after data refresh.

## GitHub Publication

To publish this project to GitHub:

1. Create a GitHub repository for ShoppingMart Analytics.
2. Add this `README.md` to the repository root.
3. Upload the Silver and Gold notebook files.
4. Upload the pipeline screenshot and dashboard PDF if you are permitted to share them.
5. Ensure that credentials, connection strings, tokens, private source data, and other confidential project information are not committed.
6. Commit and push the files to the repository.

## Project Status

The provided Fabric Monitoring Hub screenshot shows the unstructured Bronze ingestion pipeline run completed successfully. The project also includes Silver and Gold notebooks and a ShoppingMart Analytics KPI dashboard PDF.

---

**Author:** Add your name  
**Project:** ShoppingMart Analytics  
**Platform:** Microsoft Fabric
