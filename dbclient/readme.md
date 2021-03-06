# Configure WSL:Ubuntu to run .net core and DynamoDB with aws client
All this can be done from Visual Studio code terminal window

## 1. Install .net
goto home directory
```
$ cd
```
get install script
```
$ wget https://dotnet.microsoft.com/download/dotnet-core/scripts/v1/dotnet-install.sh
```
run install script
```
$ bash ./dotnet-install.sh
```
## 2. Update .profile (include next lines)
```
# set PATH so it includes dotnet if it exists
if [ -d "$HOME/.dotnet" ] ; then
    PATH="$HOME/.dotnet:$PATH"
fi
```
reload bash's .profile without logging out
```
$ source ~/.profile
```
## 3. Install aws client
goto home directory
```
$ cd
```
[Installing the AWS CLI version 2 on Linux](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html)
```
$ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
$ unzip awscliv2.zip
$ sudo ./aws/install
```
## 4. Configure the AWS CLI
[Configuring the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html)
```
$ aws configure
```
## 5. Install java
```
$ apt-get update && apt-get upgrade
$ apt-get install default-jdk
```
## 6. Install DynamoDB
[How to install DynamoDb on local Ubuntu Development](https://garywoodfine.com/how-to-install-dynamodb-on-local-ubuntu-development/)<br>
Create a hidden folder in your home directory
```
$ mkdir ./dynamolocal
```
change into the new created directory
```
$ cd ./dynamolocal
```
Download the DynamoDB tar 
```
$ wget https://s3.us-west-2.amazonaws.com/dynamodb-local/dynamodb_local_latest.tar.gz
```
uncompress it
```
$ tar xzf dynamodb_local_latest.tar.gz
```
Check the file contents in the folder 
```
$ ls 
```
The structure should look something similar too 
```
DynamoDBLocal.jar  LICENSE.txt  third_party_licenses
DynamoDBLocal_lib  README.txt
```
Optional once the file is uncompress delete the tar
```
$ rm -f dynamodb_local_latest.tar.gz 
```

## 7. Start DynamoDB
```
$ java -Djava.library.path=./DynamoDBLocal_lib -jar DynamoDBLocal.jar -sharedDb
```

## 8. Open DynamoDB Web Shell 
```
http://localhost:8000/shell/
```
Check sample code<br>
[AWS SDK for .NET Samples](https://github.com/awslabs/aws-sdk-net-samples)<br>
[LowLevelDotNetItemCRUD](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/LowLevelDotNetItemCRUD.html)
