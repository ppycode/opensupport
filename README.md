# OpenSupports Deployment with AWS CloudFormation

This guide explains how to deploy and promote the OpenSupports application across environments (e.g., development, staging, and production) using AWS CloudFormation and GitHub Actions.

## Table of Contents
1. [Pre-requisites](#pre-requisites)
2. [Infrastructure Overview](#infrastructure-overview)
3. [Deploying the Application](#deploying-the-application)
4. [CI/CD Pipeline Setup](#cicd-pipeline-setup)

---

## Pre-requisites

Before you start, ensure the following are in place:

- **AWS Account**: Make sure you have an AWS account with programmatic access enabled.
- **AWS CLI**: Installed and configured with your credentials.
- **CloudFormation Templates**: Already created for EC2, RDS (MySQL), S3, VPC, Subnets, and Security Groups.
- **GitHub Repository**: Code repository for the OpenSupports application.
- **GitHub Actions**: Workflow to deploy the application.

---

## Infrastructure Overview

The infrastructure for OpenSupports consists of:
- **EC2 Instances**: Hosting the OpenSupports application.
- **RDS (MySQL)**: Database for application data.
- **S3**: For storing static files.
- **VPC, Subnets, and Security Groups**: To manage networking and secure access to the infrastructure.

---

## Deploying the Application

### 1. Clone the Repository
Clone the repository containing the CloudFormation templates and the OpenSupports application code:

```bash
git clone https://github.com/your-repo/opensupports.git
cd opensupports
2. Deploy the CloudFormation Stack
Use the AWS CLI or AWS Management Console to deploy the CloudFormation templates that provision the necessary resources (EC2, RDS, S3, etc.).

3. Set Up OpenSupports on the EC2 Instance
After the stack is created, obtain the public IP address of the EC2 instance and SSH into it.

Install Dependencies: Download the dependencies required to run OpenSupports.
Configure the Application:
Set up the application configuration (e.g., database connection) in the config.php file.
Connect to the RDS MySQL instance using the credentials defined in the CloudFormation template.
Start the Web Server.
CI/CD Pipeline Setup
Configure GitHub Actions
The CI/CD pipeline uses GitHub Actions to automate deployment. The workflow file is located in .github/workflows.

GitHub Secrets
Configure the following secrets in your GitHub repository for AWS access:

AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
Push Changes
Any changes pushed to the main branch will trigger the CI/CD pipeline, which will:
Deploy changes to the EC2 instance using SSH.
