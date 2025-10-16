🌉 Monitoring Streaming Pipeline with Delta Live Tables
A production-grade streaming ETL demo using Databricks Delta Live Tables (DLT) to simulate IoT sensor data from major bridges. The pipeline ingests raw telemetry (temperature, vibration, tilt), enriches it with static metadata, and computes 10-minute windowed metrics using watermarks, aggregations, and joins.

🗂️ Repository Overview
File	Purpose
queries.sql	Ad hoc SQL queries to validate DLT outputs across all layers
00_data_generator.ipynb	Simulates sensor data with realistic timestamp lag
01_bronze_processing.ipynb	Bronze layer: raw streaming ingestion
02_silver_processing.ipynb	Silver layer: metadata enrichment + data quality checks
03_gold_processing.ipynb	Gold layer: 10-min aggregates + stream–stream joins
🏗️ Unity Catalog Setup
Catalog: bridge_monitoring

Schemas: 00_landing, 01_bronze, 02_silver, 03_gold

Volume: streaming under 00_landing

Subfolders: bridge_temperature, bridge_vibration, bridge_tilt

🚀 Pipeline Steps
1. Simulate Sensor Data
Run 00_data_generator.ipynb to emit synthetic readings every minute with timestamp lag.

2. Bronze Ingestion
Attach 01_bronze_processing.ipynb to a DLT pipeline. Creates raw streaming tables for each sensor type.

3. Silver Enrichment
Add 02_silver_processing.ipynb. Joins Bronze streams with static metadata and applies quality expectations.

4. Gold Aggregation
Add 03_gold_processing.ipynb. Applies watermarks, computes 10-min aggregates, and joins streams into bridge_metrics.

📚 Key Concepts
DLT Medallion Architecture: Bronze → Silver → Gold

Streaming ETL: Watermarks, window aggregations, stream–static and stream–stream joins

Declarative Pipelines: @dlt.table, @dlt.expect_or_drop, dlt.read_stream

Incremental Processing: Automatic retries and efficient updates

🔮 Next Steps
Add more metrics (e.g. tilt rate, strain gauges)

Integrate alerts via DLT expectations or Databricks SQL

Visualize metrics in real-time dashboards (Databricks SQL, Power BI)

Happy streaming! 🚧🌉🚀
