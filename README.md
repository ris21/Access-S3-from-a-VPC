# Access-S3-from-a-VPC
I created this project to demonstrate how to securely access an Amazon S3 bucket from an EC2 instance within a Virtual Private Cloud (VPC) in AWS. 
I was able to create and configure a VPC, launch an EC2 instance, configure security groups, create S3 bucket, use IAM to create access keys, and finally use the AWS CLI to interact with S3 bucket. 
By implementing this hands-on project, I gained a comprehensive understanding of networking, security, and cloud storage integration on AWS.

## Architecture Diagram
![image alt]( https://github.com/ris21/Access-S3-from-a-VPC/blob/main/architecture%20diagram-Access%20S3%20from%20a%20VPC.png)

## Project Objectives
1. Create and configure a Virtual Private Cloud (VPC) with subnets and security groups.
2. Launch an EC2 instance within the VPC and configure access via SSH port 22.
3. Set up IAM roles to allow secure access to S3 from the EC2 instance.
4. Access and upload files from an S3 bucket using the AWS CLI.

## Skills Gained
1. VPC Setup: Created and configured VPCs, subnets, route tables, and Internet Gateways.
2. EC2 Configuration: Launched EC2 instances and configured security groups for controlled access.
3. Security Best Practices: Managed IAM roles and permissions to provide EC2 instances secure access to AWS services.
4. AWS CLI Usage: Learned to interact with AWS services like S3 from an EC2 instance using the command line.
5. Networking: Understood the concepts of private and public subnets, and routing traffic within a VPC.
6. Cloud Storage: Accessed and manipulated objects in S3 buckets using programmatic access (CLI) from an EC2 instance.

## Project Steps

### 1. Created a Virtual Private Cloud (VPC) with Public and private subnets. An Internet Gateway was created and attached to the VPC to allow internet access to resources within the public subnet
![image alt]( https://github.com/ris21/Access-S3-from-a-VPC/blob/b30b5ad4ff675a4d2ee97ca8b4032cbe0e32dfe4/rispar-vpc.PNG)
![image alt]( https://github.com/ris21/Access-S3-from-a-VPC/blob/b30b5ad4ff675a4d2ee97ca8b4032cbe0e32dfe4/rispar-vpc%202.PNG)
### 2. Launched an EC2 Instance in the VPC using Amazon Linux 2 AMI. The EC2 instance was launched within the previously created VPC and assigned to the public subnet with a public IP address. - A security group was configured to allow SSH access (port 22). 
![image alt]( https://github.com/ris21/Access-S3-from-a-VPC/blob/b30b5ad4ff675a4d2ee97ca8b4032cbe0e32dfe4/instance%20launch%20success.PNG)
### 3. Created a S3 bucket and uploaded 2 objects(files) to it
![image alt]( https://github.com/ris21/Access-S3-from-a-VPC/blob/main/create%20bucket.PNG)
![image alt]( https://github.com/ris21/Access-S3-from-a-VPC/blob/b01eedb72addf13f889dd66952edfecf058a0ebf/objects%20upload.PNG)
### 4. Used my account to create access keys within IAM for EC2 to Access S3 securely via the CLI 
![image alt]( https://github.com/ris21/Access-S3-from-a-VPC/blob/b01eedb72addf13f889dd66952edfecf058a0ebf/create%20access%20keys.PNG)
### 5. Used the access key to connect to the EC2 instance using the public IP
![image alt]( https://github.com/ris21/Access-S3-from-a-VPC/blob/b01eedb72addf13f889dd66952edfecf058a0ebf/ec2%20connect.PNG) 
### 6. Accessed and uploaded files to the S3 bucket using the following commands;

#### aws s3 ls - list S3 bucket
#### aws s3 ls risparbucket – list objects in S3 bucket 
#### sudo touch /tmp/test.txt – created a new .txt file
#### aws s3 cp /tmp/test.txt s3://risparbucket/ - Uploaded the .txt file to the S3 bucket
#### aws s3 ls s3:// risparbucket - Verified the upload by listing the bucket contents

![image alt]( https://github.com/ris21/Access-S3-from-a-VPC/blob/b01eedb72addf13f889dd66952edfecf058a0ebf/list%20s3%20bucket%20objects.PNG)
