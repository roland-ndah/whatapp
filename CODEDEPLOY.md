
# Installing the CodeDeploy agent on EC2
```
#!/bin/bash
sudo yum update -y
sudo yum install -y ruby wget
wget https://aws-codedeploy-eu-west-1.s3.eu-west-1.amazonaws.com/latest/install
chmod +x ./install
sudo ./install auto
sudo service codedeploy-agent status
```


# create a bucket and enable versioning
```
aws s3 mb s3://ndahbucket --region us-east-2 --profile Isaac
aws s3api put-bucket-versioning --bucket ndahbucket --versioning-configuration Status=Enabled --region us-east-2 --profile Isaac
```

# deploy the files into S3
```
aws deploy push --application-name MywebApp --s3-location s3://ndahbucket/MywebApp/app.zip --ignore-hidden-files --region us-east-2 --profile Isaac
```