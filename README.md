End-to-End Real-Time Analytics on Microsoft Fabric
Learn to build an end to end data engineering and analysis pipeline utilising Microsoft Fabric’s Data Factory, Data Engineering, and Power BI experiences.

Ingesting Earthquake events data from usgs.

Technologies Used: Python, PySpark, Fabric (Data Engineering, Data Factory, Power BI)

🏗 System Architecture & Data Flow
The project follows a streamlined workflow from ingestion to visualization, as illustrated below:

1. Data Orchestration (Data Factory)
Managed via a multi-stage pipeline that triggers sequence-based PySpark Notebooks.

Pipeline Logic: Validates data availability before moving through the Medallion layers.

Automation: Integrated triggers ensure that new seismic events are processed the moment they occur.

2. The Medallion Framework (OneLake)
We utilize a Zero-Copy storage strategy where all compute engines query the same Delta tables:

Worldwide Earthquake Events API - Bronze Layer Processing: This notebook focuses on ingesting raw earthquake data from the USGS API. It performs minimal processing to store data in its original format, serving as the foundational layer for further refinement.

Worldwide Earthquake Events API - Silver Layer Processing: This notebook enhances the data from the Bronze layer by cleaning, transforming, and consolidating the earthquake data. It prepares the data for more analytical processing.

Worldwide Earthquake Events API - Gold Layer Processing: In this final processing stage, the notebook refines the data to create business-ready datasets. These are optimized for high-value insights and are tailored for specific analytical purposes, such as reporting and visualization in tools like Power BI.

3. Real-Time Consumption (Power BI)
Direct Lake Mode: Connects Power BI directly to OneLake Delta tables. This provides the performance of Import Mode without the need for manual dataset refreshes.

Semantic Sync: Automatic refresh triggers ensure the dashboard reflects global activity in real-time.
