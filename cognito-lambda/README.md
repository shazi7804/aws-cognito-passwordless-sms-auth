# Cognito Passwordless SMS Authentication - Serverless

This is an AWS Serverless Application. If you deploy it, this is what you get:

- An Amazon Cognito User Pool, pre-configured with AWS Lambda triggers to implement passwordless SMS auth
- An Amazon Cognito User Pool Client, that you can use to integrate with the User Pool
- The needed Lambda functions that serve as User Pool triggers
- The permissions on the Lambda functions so that the User Pool may invoke them

## Deployment instructions

### Pre-requisites

1. Download and install [Node.js](https://nodejs.org/en/download/)
2. Download and install [AWS SAM CLI](https://github.com/awslabs/aws-sam-cli)
3. Of course you need an AWS account and necessary permissions to create resources in it. Make sure your AWS credentials can be found during deployment, e.g. by making your AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY available as environment variables.
4. You need an existing S3 bucket to use for the SAM deployment. Create an empty bucket.

### How to deploy the Serverless Application with AWS SAM CLI

1. Clone this repo `git clone https://github.com/aws-samples/amazon-cognito-passwordless-email-auth.git`
2. Enter cognito directory: `cd amazon-cognito-passwordless-email-auth/cognito`
3. Install dependencies: `npm install`
4. Set the following environment variables (all mandatory):
  - S3_BUCKET_NAME='the bucket name of the bucket you want to use for your SAM deployment'
  - SES_FROM_ADDRESS='the verfied e-mail address in SES the e-mails will be sent from'
  - STACK_NAME='the name you want the CloudFormation stack to be created with'
  - USER_POOL_NAME='the name you want your User Pool to be created with'
5. Build and deploy the application: `npm run bd` This runs AWS SAM CLI

if that succeeded, you have succesfully deployed your application. The outputs of the CloudFormation stack will contain the ID's of the User Pool and Client, that you can use in your client web app.

Deploy either through the Serverless Application Repository or with the AWS SAM CLI

```
sam deploy --stack-name=cognito-passwordless-sms-auth \
           --s3-bucket=cognito-passwordless-sms-auth --parameter-overrides ParameterKey=UserPoolName,ParameterValue=cognito-passwordless-sms-auth --capabilities CAPABILITY_IAM
```

## Clients

[Web Client (Angular)](../client/web)

[iOS Client](../client/iOS)

### License Summary

This sample code is made available under a modified MIT license. See the LICENSE file.
