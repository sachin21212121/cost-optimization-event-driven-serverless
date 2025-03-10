# EBS Snapshot Cleanup Lambda

## Overview
This AWS Lambda function automates the cleanup of unused Amazon Elastic Block Store (EBS) snapshots. It identifies snapshots that are not associated with any active EBS volumes or are linked to volumes that are not attached to running EC2 instances and deletes them to free up storage and reduce costs.

## Features
- Retrieves all EBS snapshots owned by the account.
- Identifies running EC2 instances.
- Deletes snapshots that are not associated with any volume.
- Deletes snapshots of volumes that are not attached to running instances.

## Prerequisites
- AWS account with necessary permissions.
- An IAM role with the following permissions:
  - `ec2:DescribeSnapshots`
  - `ec2:DescribeInstances`
  - `ec2:DescribeVolumes`
  - `ec2:DeleteSnapshot`
- AWS Lambda configured with Python runtime.
- `boto3` library (included in AWS Lambda by default).

## Installation and Deployment
1. Clone this repository:
   ```sh
   git clone https://github.com/yourusername/ebs-snapshot-cleanup.git
   cd ebs-snapshot-cleanup
   ```
2. Create a new AWS Lambda function in the AWS Management Console.
3. Upload the `lambda_function.py` script or paste the code directly.
4. Assign an appropriate IAM role to the Lambda function.
5. Configure the trigger (e.g., CloudWatch Event Rule to run periodically).

## Usage
This Lambda function runs automatically based on the configured schedule (e.g., daily or weekly) and deletes unused snapshots.

### Sample Execution Output
```
Deleted EBS snapshot snap-0123456789abcdef0 as it was not attached to any volume.
Deleted EBS snapshot snap-0987654321abcdef0 as its associated volume was not found.
```

## Security Considerations
- Ensure that only necessary permissions are granted to the Lambda function.
- Review and test the script in a non-production environment before deployment.


## Author
[Sachin Jha](https://github.com/yourusername)


