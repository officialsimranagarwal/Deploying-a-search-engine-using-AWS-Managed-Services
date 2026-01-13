# Deploying a Search Engine with AWS Managed Services 🔍

![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)
![ElasticSearch](https://img.shields.io/badge/ElasticSearch-005571?style=for-the-badge&logo=elasticsearch&logoColor=white)
![CI/CD](https://img.shields.io/badge/CI%2FCD-CodePipeline-blue?style=for-the-badge)

## 📖 Overview

This project implements a serverless, scalable search engine architecture using **AWS OpenSearch (formerly ElasticSearch)**, orchestrated via a **CI/CD pipeline** built on AWS CodePipeline. It demonstrates how to automate the deployment of search infrastructure and serverless indexing logic.

## 🏗️ Technical Architecture

### 1. Ingestion & Indexing Pipeline
-   **S3 Document Store**: Raw documents (PDFs) are uploaded here.
-   **Lambda Triggers**: S3 events trigger specific Lambda functions to parse and index content.
-   **OpenSearch Service**: The managed cluster where indexed data resides.

### 2. CI/CD Workflow (AWS CodePipeline)
-   **Source**: **AWS CodeCommit** repository triggers the pipeline on commit.
-   **Build**: **AWS CodeBuild** (using Ubuntu Standard 6.0 environment) compiles the SAM templates.
-   **Deploy**: **CloudFormation** deploys the serverless application stack (Lambdas + API Gateway).
    -   *Capabilities Required*: `CAPABILITY_IAM`, `CAPABILITY_AUTO_EXPAND`.

### 3. API & Search Interface
-   **API Gateway**: Exposes HTTP endpoints.
    -   `ANY /`: Routes to `search-gateway`.
    -   `ANY /search`: Routes to `searchFunction`.

## ⚙️ Configuration Specs

-   **Runtime**: Node.js/Python (dependent on Lambda implementation).
-   **Buildspec**: Customized `buildspec.yml` to handle SAM packaging.
-   **IAM Policies**: Detailed least-privilege policies for Lambda to access OpenSearch and S3.

## 📂 Contents

-   **`managed services aws.pdf`**: Theory and diagrams.
-   **`setting up`**: CLI/Console commands for environment initialization.
-   **`final steps`**: Validating the deployment via Postman/Curl.

## 🚀 Deployment

1.  Clone the repository:
    ```bash
    git clone https://github.com/officialsimranagarwal/Deploying-a-search-engine-using-AWS-Managed-Services.git
    ```
2.  Configure the `buildspec` and push to CodeCommit to trigger the pipeline.

## 🤝 Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## 👤 Author

**Simran Agarwal**
-   [Profile](https://github.com/officialsimranagarwal)
-   [LinkedIn](https://linkedin.com/in/simran-agarwal-54751b191)

---
*Generated with ❤️ by Simran Agarwal*
