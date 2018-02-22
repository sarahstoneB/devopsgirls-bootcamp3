# Serverless Website

## Recap

- In Module 1, you deployed a static website to EC2 instances. You had to choose an instance size based on how popular your site is going to be, choose an operating system for the EC2 instance, install and configure nginx and deploy the static site. 
- In Module 2, you deployed a container which served your static web site to an ECS cluster. You had to pool some EC2 instances into an ECS cluster, choose CPU and memory for the container(s), build and package the containers, and deploy them to the cluster

## Key Concepts

- When you use EC2 instances, or containers, you have to make some decisions on capacity when you are provisioning. You also have to pay for that capacity, and manage and operate those resources. For example in case of EC2, you have to keep the OS and software configured and kepts up to date.

- What is Serverless? Do not think of the word literally, as there are servers under the hood. You dont manage those servers, and do not have to take decisions on the capacity you might need. Also when you dont use the capacity, you dont pay anything for it.

- In our case of hosting a static website, we do not perform any dynamic computation. We store some files, and the computing capacity is used to handle web requests and serve the static pages.

- Simple Storage Service, S3 is an object store. In simple terms, you have the filename which is your key, and the contents of the file is the object. S3 provides you a durable file storage, and provides an API to GET, PUT and DELETE objects. It can act as a web server and serve objects on HTTP GET requests.

## What we are going to do

In this practical session, we will

- Create a S3 bucket and configure it as a web server.
- Load the static pages of our website to the bucket.
- Set up a pipeline to publish any changes to the code to S3.

## Create S3 bucket as a web server

### 1.) Go to Services > S3, then click on "Create Bucket"

![Create Bucket][3-3-1-create-s3-bucket]

### 2.) Enter a unique bucket name and click "Next". The bucket name has to be globally unique. So use something like `yourname-devopsgirls-site`

![Create Bucket][3-3-2-create-s3-bucket]

### 3.) Click "Next" without making any changes.

![Create Bucket][3-3-3-create-s3-bucket]

### 4.) In the "Manage public permissions" drop down choose "Grant public read access to this bucket". Note that you will have a warning, but since we want to host a public website in this bucket, it is ok. Click "Next".

![Create Bucket][3-3-4-create-s3-bucket]

### 5.) Review the inputs, and click "Create Bucket"

![Create Bucket][3-3-5-create-s3-bucket]

## Configure S3 bucket as a webserver

### 1.) Go to Services > S3, then click on the bucket you just created

![Create Bucket][3-3-6-configure-s3-bucket]

### 2.) Click on the "Properties" tab, and click on "Static Website Hosting"

![Create Bucket][3-3-7-configure-s3-bucket]

### 3.) Choose "Use this bucket to host a website", enter "index.html" in the "Index Dcoument" text box, and click "Save".

![Create Bucket][3-3-8-configure-s3-bucket]

## Copy the static website files to S3 bucket

>>>>>>> Stashed changes