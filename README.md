# Launching an EC2 Instance and Deploying a Simple Website on AWS

## Step 1: Deploying locally

We can deploy the website locally to see how it works before deploying to AWS. We do this by cloning the github repository.

## Step 2: Launching an EC2 Instance

1. Go to the AWS Management Console and navigate to the EC2 dashboard.
2. Click on "Launch Instance" and choose an AMI for the server. I chose Ubuntu OS for this project.
3. Select an instance type, configure instance details, add storage, and configure security groups to allow inbound traffic on port 22 (SSH) and port 80 (HTTP).
4. Review and launch the instance, and create a new key pair or use an existing one to connect to the instance securely.
5. I chose to connect to the Instance via Instance connect for this project

## Step 3: Setting Up Apache2 Web Server on Ubuntu

1. SSH into the EC2 instance using the key pair and Instance Connect.
2. Update the package index and install Apache2 by running the following commands:
    ```bash
    sudo apt update
    sudo apt install apache2
    ```
3. Start the Apache2 service:
    ```bash
    sudo service start apache2
    ```
4. Check status of Apache2 server:
    ```bash
    sudo service apache2 status
    ```
    We can also do this by copying the public IP address of the EC2 instance to the browser and see if the Apache2 webpage loads 

## Step 4: Deploying a Simple index.html File on the Web Server

1. Create a simple HTML file named `index.html` with your desired content. A sample one can be found in this repository
   
2. Move the `index.html` file to the Apache document root directory:
    ```bash
    sudo mv index.html /var/www/html/
    ```
3. Ensure the file permissions are set correctly:
    ```bash
    sudo chmod 644 /var/www/html/index.html
    ```
4. Access the website by entering your instance's public IP address or DNS name in a web browser. You should see the content of your `index.html` file served by Apache.

Congratulations! You have successfully launched an EC2 instance, connected to it via Instance Connect, set up an Apache2 web server on Ubuntu, and deployed a simple website on the web server in AWS.
