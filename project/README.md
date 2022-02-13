# Udacity Cloud Devops Project 2 - Deploy a high-availability web app using CloudFormation

## Architecture Diagram:
![Diagram](../UdacityAWSDevopsC2.png)


## Getting Started
Deploy S3 bucket
```
aws cloudformation create-stack --stack-name UdacityAwsDevopsC2S3 --template-body file://s3.yml  --parameters file://s3.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-east-1
```
Upload `index.html` to the bucket.

Deploy the network
```
aws cloudformation create-stack --stack-name UdacityAwsDevopsC2Network --template-body file://network.yml  --parameters file://network.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-east-1
```


Deploy the bastion server
```
aws cloudformation create-stack --stack-name UdacityAwsDevopsC2Bastion --template-body file://bastion.yml  --parameters file://bastion.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-east-1
```

Deploy the web server and load balancer
```
aws cloudformation create-stack --stack-name UdacityAwsDevopsC2Servers --template-body file://servers.yml  --parameters file://servers.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-east-1
```

Visit load balancer endpoint to confirm the following webpage loads:
![Webpage](../ExpectedWebpage.png)


The endpoint will be output `LoadBalancerDNS` from the `UdacityAwsDevopsC2Servers` stack.
