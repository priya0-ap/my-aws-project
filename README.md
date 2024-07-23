# Serverless API with GraphQL

## Overview
This project demonstrates the use of several AWS services including Lambda, AppSync, DynamoDB, API Gateway, and CloudWatch.

## Technologies and Services
- AWS Lambda
- AWS AppSync
- Amazon DynamoDB
- Amazon API Gateway
- Amazon CloudWatch

## Setup and Deployment

### Prerequisites
- AWS Account
- AWS CLI configured
- Node.js installed (for AppSync resolvers)

### Deployment Steps

1. **Create Lambda Functions:**
   - Navigate to the AWS Lambda console.
   - Create two Lambda functions: `createItemFunction` and `getItemFunction`.
   - Upload `createItem.py` to `createItemFunction`.
   - Upload `getItem.py` to `getItemFunction`.

2. **Configure AppSync:**
   - Create a new AppSync API.
   - Import `schema.graphql`.
   - Add resolvers for `createItem` and `getItem` using the provided VTL templates.

3. **Configure API Gateway:**
   - Create a new REST API.
   - Set up POST and GET methods for `/items` resource as described in the API Gateway section.

4. **Set Up CloudWatch Logs:**
   - Ensure your Lambda functions have logging enabled.
   - View logs in the CloudWatch console under Logs > Log Groups.

### Testing

#### Using API Gateway
- Create an item:
  ```sh
  curl -X POST https://<api-id>.execute-api.<region>.amazonaws.com/<stage>/items \
  -H "Content-Type: application/json" \
  -d '{"id": "1", "name": "Test Item", "description": "This is a test item."}'
