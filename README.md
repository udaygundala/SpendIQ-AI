# SpendIQ-AI
AI-driven Cloud &amp; AI Cost Management with FinOps + DevOps + GenAI
=======
SpendIQ AI
AI-driven Cloud \& AI Cost Management with FinOps + DevOps + GenAI

📌 Overview
SpendIQ AI is an intelligent cost management and forecasting solution that combines:
FinOps principles – visibility, optimization, and accountability of cloud spend
AI/ML forecasting models – predicting future cloud \& AI workload costs
Generative AI (GenAI) – natural language insights, executive summaries, and what-if simulations
DevOps integration – automated cost governance gates in Azure DevOps pipelines

This project helps organizations reduce cloud waste, forecast AI spend, and align engineering with finance.

🚀 Features
📊 Spend Forecasting – Predicts cloud and AI-related spend using ML models
🔍 Anomaly Detection – Identifies unusual spikes in resource costs
🤖 Generative AI Assistant – Natural language Q\&A, executive summaries, and scenario planning
🔧 DevOps Integration – Azure DevOps pipeline checks for cost thresholds before deployments
💡 FinOps Alignment – Supports reporting, accountability, and showback/chargeback practices

🏗️ Architecture

           +-------------------+
           |   SpendIQ AI Core |
           | Forecast \& Anomaly|
           +-------------------+
                    |
    -----------------------------------------
    |            |            |             |

Conversational   Exec.        What-if       DevOps
FinOps (Q\&A)   Summaries    Simulations   Integration
 via GenAI     via GenAI    via GenAI     via ADO Gates

📂 Project Structure

SpendIQ-AI/
│── data/                 # Sample cost dataset (CSV/JSON)
│── notebooks/            # Jupyter notebooks for ML/GenAI experiments
│── pipeline/             # Azure DevOps pipeline YAML
│── src/                  # Python scripts (forecast, anomaly detection)
│── docs/                 # Architecture diagrams, FinOps notes
│── demo/                 # Screenshots / demo scripts
│── README.md             # Project overview

⚙️ Tech Stack
Cloud: Azure (AI Services, ML Studio, Cost Management APIs)
ML/AI: Python (Pandas, Scikit-learn, Prophet, OpenAI SDK)
DevOps: Azure DevOps Pipelines, Repos
GenAI: Azure OpenAI (GPT models for summaries \& Q\&A)
FinOps: Based on FinOps Framework (visibility, forecasting, optimization)

📈 Demo Use Cases

Forecast Cloud Spend → “What will our Azure GPU cost be next month?”
Detect Anomalies → Alerts if costs spike 40% in a day.
GenAI Executive Report → Auto-generated weekly summary: “Your cloud spend increased 12% due to GPU scaling in AI workloads.”
DevOps Gate → Block deployment if estimated costs exceed budget.

🔮 Roadmap

Cost dataset \& basic forecast
Anomaly detection mode
Azure DevOps pipeline integration
GenAI natural language Q\&A
Executive summary generator
Production-ready demo

👤 Author
Uday G – Senior DevOps Engineer exploring AI + FinOps + DevOps.

Sample Data schema 
## 📊 SpendIQ Normalized Sample Dataset

This repository includes a sample dataset `spendiq_normalized_sample_data.csv` that simulates **multi-cloud spend data** across AWS, Azure, and GCP.  
It is intended for **SpendIQ PoC demonstrations**, dashboards, and analytics.

### 🔹 Dataset Overview
- **Time Period:** 90 days (June–Aug 2025)
- **Clouds Covered:** AWS, Azure, GCP
- **Granularity:** Daily cost per service, per account/subscription/project

### 🔹 Schema
| Column             | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| `Date`             | Billing date (daily granularity)                                           |
| `Cloud`            | Cloud vendor: AWS / Azure / GCP                                            |
| `RootEntity`       | Top-level organization (AWS Org Root / Azure Tenant / GCP Org)             |
| `HierarchyLevel1`  | Mid-level grouping (AWS OU / Azure Mgmt Group / GCP Folder)                |
| `HierarchyLevel2`  | Account / Subscription / Project                                           |
| `HierarchyLevel3`  | Resource Group / Tag Group / SKU                                           |
| `Service`          | Cloud service name (e.g., EC2, AzureML, Vertex AI)                         |
| `Category`         | Spend category: Infra Spend / AI Spend / GenAI Spend                       |
| `UsageType`        | OnDemand / Reserved / Spot / Preemptible                                   |
| `Cost (USD)`       | Normalized cost in USD                                                     |
| `Tags`             | Flexible key-value metadata (e.g., `env`, `team`, `app`, `costCenter`)     |
| `Dimensions`       | Cloud-specific metadata (e.g., `region`, `sku`, `billingSource`)           |

### 🔹 Key Features
- **Multi-level hierarchy** across all 3 clouds (Org → Account → Service → Resource).
- **AI/GenAI tracking**: Special tagging for services like SageMaker, AzureML, Vertex AI, Bedrock, Azure OpenAI.
- **Usage types**: Helps distinguish OnDemand vs Reserved vs Spot/Preemptible usage.
- **Tag-driven governance**: Cost attribution by team, app, environment, cost center.
- **Extensible**: Schema can support new tags, services, or dimensions without schema redesign.

### 🔹 Example Row
```json
{
  "Date": "2025-08-12",
  "Cloud": "Azure",
  "RootEntity": "Tenant-456",
  "HierarchyLevel1": "Mgmt-AI",
  "HierarchyLevel2": "Sub-2005",
  "HierarchyLevel3": "RG-GenAI",
  "Service": "Azure OpenAI",
  "Category": "GenAI Spend",
  "UsageType": "OnDemand",
  "Cost (USD)": 1125.40,
  "Tags": {
    "env": "prod",
    "team": "NLP",
    "app": "customer-chatbot",
    "costCenter": "CC-2001"
  },
  "Dimensions": {
    "region": "eastus",
    "sku": "gpt-4-32k",
    "billingSource": "CostManagementAPI"
  }
}

