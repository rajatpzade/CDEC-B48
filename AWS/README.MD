# Introduction to Virtualization and Cloud Computing

Welcome to the **AWS Batch Day 1** session! This document provides an overview of the topics we'll cover today, along with helpful resources and instructions for hands-on practice.

## Topics Covered

### 1. **Introduction to Virtualization**
- **What is Virtualization?**
  - Virtualization is the creation of a virtual version of hardware, allowing multiple operating systems to run on a single physical machine.
  
- **Types of Virtualization**
  - Server Virtualization: Multiple virtual servers on one physical machine.
  - Storage Virtualization: Combining multiple physical storage devices into a single virtual unit.
  - Network Virtualization: Abstracting network resources into a manageable virtual framework.

- **Key Benefits**:
  - Efficient resource utilization
  - Cost savings
  - Scalability
  - Simplified management

#### **Deep Dive Knowledge**:
- Virtualization uses a hypervisor (like VMware or VirtualBox) to manage VMs.
- Popular tools include KVM, Xen, and Microsoft Hyper-V.
- Real-time Example: A company can run a legacy Windows app on a Linux server using virtualization.

#### **Simple Explanation**:
- Think of virtualization as renting rooms in a house (the physical machine) where each room (VM) has its own tenant (OS).

### 2. **Virtualization vs Cloud**
- Virtualization is a foundational technology; cloud computing builds on it.
- **Comparison Table**:
  | **Feature**          | **Virtualization**                     | **Cloud Computing**                       |
  |-----------------------|----------------------------------------|-------------------------------------------|
  | **Definition**        | Technology to create virtual environments. | Delivery of on-demand computing resources via the internet. |
  | **Deployment**        | Local (on-premises servers).           | Hosted on the internet.                   |
  | **Scalability**       | Limited by physical hardware.          | Highly scalable without physical limits.  |
  | **Access**            | Internal network only.                | Accessible from anywhere with an internet connection. |

#### **Deep Dive Knowledge**:
- Virtualization focuses on optimizing hardware usage, while cloud emphasizes service delivery and flexibility.
- Real-time Example: Virtualization is like owning apartments in a building, whereas cloud is like Airbnb where anyone can rent as needed.

### 3. **Cloud Models (IaaS, PaaS, SaaS)**
- **Infrastructure as a Service (IaaS)**:
  - Virtualized hardware resources.
  - **Examples**: AWS EC2, Google Compute Engine.
  - **Real-time Example**: Hosting a website on AWS EC2 where you control the OS and applications.

- **Platform as a Service (PaaS)**:
  - Platforms for application development.
  - **Examples**: AWS Elastic Beanstalk, Google App Engine.
  - **Real-time Example**: Using AWS Elastic Beanstalk to deploy a web app without worrying about the underlying infrastructure.

- **Software as a Service (SaaS)**:
  - Software accessible over the internet.
  - **Examples**: Gmail, Salesforce.
  - **Real-time Example**: Using Google Docs to collaborate on documents in real-time.

#### **Simple Explanation**:
- **IaaS**: Like renting a raw apartment and furnishing it yourself.
- **PaaS**: Like renting a fully furnished apartment but adding your own decorations.
- **SaaS**: Like booking a hotel room where everything is ready.

### 4. **AWS Account Creation**

Follow these steps to create your AWS account:
1. Visit [AWS Free Tier](https://aws.amazon.com/free/).
2. **Sign Up**:
   - Enter your email address and password.
   - Create an account name.
3. **Account Type**: Choose "Personal" or "Professional."
4. **Payment Method**: Add a valid credit/debit card for identity verification.
5. **Verify Identity**: Enter your mobile number for OTP verification.
6. **Select Support Plan**: Choose "Basic (Free)."
7. Log in to the AWS Management Console.

#### **Deep Dive Knowledge**:
- AWS Free Tier offers 12 months of free services like EC2, S3, and Lambda with usage limits.
- Real-time Example: Use the free tier to deploy a simple static website using S3 and monitor costs via the AWS Billing Dashboard.

---

## Hands-On Practice
- **Objective**: Create an AWS account and explore the Management Console.
- **Tasks**:
  1. Sign up for an AWS account using the steps above.
  2. Navigate through the AWS Console to identify key services like EC2, S3, and RDS.

---

## Resources
- [AWS Free Tier Overview](https://aws.amazon.com/free/)
- [AWS Documentation](https://docs.aws.amazon.com/)
- [Virtualization Basics](https://www.vmware.com/topics/glossary/content/virtualization.html)

---

## Key Takeaways
- Virtualization is the backbone of cloud computing.
- Understand the differences between IaaS, PaaS, and SaaS.
- AWS provides a user-friendly interface for cloud services.

----

# AWS Batch Day 2: Introduction to AWS Dashboard and EC2

## Topics Covered

### 1. **Introduction to AWS Dashboard**
The AWS Management Console is the primary interface for managing AWS resources. It is a web application that allows you to:
- Access and manage services like EC2, S3, RDS, and Lambda.
- Monitor your usage and billing.
- Set up security configurations and permissions.

#### **Key Components of the Dashboard**:
1. **Navigation Bar**: Displays your logged-in account, active region, and access to global services like billing and support.
2. **Service Search Bar**: Helps you quickly locate AWS services by name.
3. **Resource Groups**: Allows grouping and managing related resources.
4. **Recent Services**: A list of services you used recently for quick access.
5. **Build a Solution**: Quick links to common tasks such as launching an instance or creating a database.

#### **Best Practices**:
- Always verify the active region to avoid deploying resources in unintended locations.
- Use the Billing Dashboard to track costs and identify unusual usage patterns.

![Sample Image](images/2024-12-30%2010.14.03.gif)

---

### 2. **Region vs Availability Zone (AZ)**
AWS resources are deployed in Regions and Availability Zones to ensure high availability, fault tolerance, and low latency.

#### **Region**:
- A geographical location, such as **US East (N. Virginia)** or **Asia Pacific (Mumbai)**.
- Each region is independent and contains multiple Availability Zones.
- Choose a region based on proximity to your users, compliance requirements, and cost considerations.

#### **Availability Zone (AZ)**:
- A physically distinct data center within a region.
- Each AZ is isolated but connected to other AZs in the same region via low-latency links.
- Example: The **Asia Pacific (Mumbai)** region has three AZs: ap-south-1a, ap-south-1b, and ap-south-1c.

#### **Why Regions and AZs Matter**:
- **High Availability**: Deploy resources across multiple AZs to ensure uptime during failures.
- **Low Latency**: Choose regions close to your users to minimize network delays.
- **Cost Optimization**: Some regions have lower costs for the same services.

![Sample Image](images/Regions.gif)

---

### 3. **Introduction to EC2 Service**
Amazon Elastic Compute Cloud (EC2) is a core service for deploying scalable virtual servers in the cloud.

#### **Features**:
- **Scalability**: Easily scale instances up or down based on demand.
- **Customizable Instances**: Choose instance types based on CPU, memory, and storage needs.
- **Secure Access**: Use SSH keys and security groups for secure connections.
- **Flexible Pricing**:
  - **On-Demand Instances**: Pay per hour with no long-term commitments.
  - **Reserved Instances**: Commit for 1-3 years for lower prices.
  - **Spot Instances**: Bid for unused capacity at discounted rates.

#### **Use Cases**:
- Hosting web applications.
- Running batch jobs or machine learning models.
- Building development and testing environments.

---

### 4. **Creating Your First EC2 Instance (Ubuntu)**

#### **Steps to Launch an EC2 Instance**:
1. **Navigate to EC2 Service**:
   - Log in to the AWS Management Console.
   - Search for "EC2" in the service search bar and select it.

2. **Launch Instance**:
   - Click on the "Launch Instance" button.

3. **Choose an Amazon Machine Image (AMI)**:
   - Select **Ubuntu Server 20.04 LTS** (or another version as needed).

4. **Select Instance Type**:
   - Choose **t2.micro** for free tier eligibility (1 vCPU, 1 GB RAM).

5. **Configure Instance Details**:
   - Leave the default settings.
   - Optionally, enable Auto-Assign Public IP for internet access.

6. **Add Storage**:
   - Keep the default storage size (e.g., 8 GB).
   - Modify if additional storage is required.

7. **Add Tags**:
   - Create a tag to identify your instance (e.g., `Key: Name, Value: MyFirstInstance`).

8. **Configure Security Group**:
   - Create a new security group.
   - Add an inbound rule to allow **SSH (port 22)** from your IP address.

9. **Review and Launch**:
   - Verify your settings and click "Launch."
   - Select an existing key pair or create a new one for SSH access.

10. **Access Your Instance**:
    - Download the private key file (`.pem`) if creating a new key pair.
    - Use an SSH client (like PuTTY or Terminal) to connect:
      ```bash
      ssh -i /path/to/key.pem ubuntu@<Public-IP-Address>
      ```

#### **Best Practices**:
- Always restrict SSH access to specific IP addresses for security.
- Use Elastic IPs for instances requiring a static public IP.

---

## Resources
- [AWS EC2 Documentation](https://docs.aws.amazon.com/ec2/)
- [AWS Free Tier Details](https://aws.amazon.com/free/)
- [SSH Key Management](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html)

---

## Key Takeaways
- The AWS Dashboard is your central hub for managing cloud resources.
- Regions and AZs provide resilience and flexibility for deployments.
- EC2 is a powerful service for launching virtual servers with customizable configurations.

----

# AWS Batch Day 3: Security Groups and Instance Management

## Topics Covered

### 1. **Security Group (SSH and RDP Port)**
Security Groups act as virtual firewalls that control inbound and outbound traffic for your AWS instances. 

#### **Key Concepts**:
- **Inbound Rules**: Define the traffic allowed to reach your instance.
- **Outbound Rules**: Define the traffic allowed to leave your instance.
- Rules specify:
  - Protocol (e.g., TCP, UDP, ICMP).
  - Port Range (e.g., 22 for SSH, 3389 for RDP).
  - Source (IP address or another security group).

#### **Common Ports**:
- **SSH (Port 22)**: Used for secure remote access to Linux instances.
- **RDP (Port 3389)**: Used for remote access to Windows instances.

#### **Best Practices**:
- Restrict access to specific IP ranges for security.
- Use custom security groups for different applications or roles.

#### **Steps to Configure a Security Group**:
1. Open the EC2 Dashboard and navigate to "Security Groups."
2. Create a new security group.
3. Add inbound rules:
   - For SSH: Protocol = TCP, Port = 22, Source = My IP.
   - For RDP: Protocol = TCP, Port = 3389, Source = My IP.
4. Add outbound rules (default allows all traffic).
5. Attach the security group to your instance during or after creation.

---
# SSH Service: Secure Shell Basics

## What is SSH?
SSH (Secure Shell) is a cryptographic network protocol that provides a secure way to access remote servers and systems. It allows administrators and developers to log in, execute commands, and manage resources over an encrypted connection.

---

## Key Features of SSH
- **Secure Communication**: Uses encryption to secure the connection.
- **Authentication**: Supports various methods like password-based or key-based authentication.
- **Port Forwarding**: Allows secure tunneling of other protocols.
- **File Transfers**: Includes tools like `scp` and `rsync` for transferring files securely.
- **Session Management**: Offers features like persistent sessions and command execution.

---

## SSH in AWS
SSH is commonly used in AWS to manage EC2 instances and other Linux-based resources securely.

### Default Settings for AWS EC2:
- **Port**: 22 (must be open in the security group).
- **Authentication**: Key-pair (`.pem` file) generated during instance creation.

---

## Setting Up SSH for Remote Access

### 1. **Installing SSH Client**
Most operating systems come with SSH clients pre-installed. For example:
- **Linux/MacOS**: SSH is available by default in the terminal.
- **Windows**: Use `ssh` in PowerShell or install third-party tools like PuTTY.

### 2. **Connect to a Remote Server**
To connect to a remote server:
```bash
ssh -i /path/to/key.pem username@<remote-ip-address>
```
- Replace `/path/to/key.pem` with the path to your private key file.
- Replace `username` with the server's default user (e.g., `ubuntu` for Ubuntu instances).
- Replace `<remote-ip-address>` with the public IP of the remote server.

---

### 3. **Configuring SSH Access on AWS EC2**
1. **Verify Security Group**:
   - Ensure the inbound rule allows SSH (port 22).
   - Restrict access to your IP address for enhanced security.

2. **Set File Permissions**:
   ```bash
   chmod 400 /path/to/key.pem
   ```
   This ensures that the private key has the correct permissions.

3. **Connect Using the SSH Command**:
   ```bash
   ssh -i /path/to/key.pem ubuntu@<Public-IP>
   ```

4. **Troubleshooting Connection Issues**:
   - Verify that the instance is running.
   - Check the public IP and ensure it matches the instance.
   - Ensure your IP is allowed in the security group.

---

### 4. **Using SSH Config File**
Simplify repeated connections by creating an SSH configuration file:

#### Example Config File (`~/.ssh/config`):
```plaintext
Host myserver
    HostName <Public-IP>
    User ubuntu
    IdentityFile /path/to/key.pem
```
Connect with:
```bash
ssh myserver
```

---

### 5. **Advanced SSH Usage**
- **Port Forwarding**:
  Securely access local or remote ports.
  ```bash
  ssh -L local_port:remote_host:remote_port user@remote_ip
  ```
- **Transfer Files with `scp`**:
  Copy files securely between local and remote systems.
  ```bash
  scp -i /path/to/key.pem file.txt user@<remote-ip>:/path/to/destination
  ```
- **Persistent Sessions with `tmux` or `screen`**:
  Keep SSH sessions active even if the connection drops.

---

## Security Best Practices
- **Restrict Access**: Limit SSH access to specific IP addresses.
- **Disable Root Login**: Prevent direct root access by modifying `/etc/ssh/sshd_config`.
- **Use Strong Keys**: Always use strong, unique key pairs.
- **Regular Key Rotation**: Replace keys periodically to maintain security.

---

## Resources
- [Official OpenSSH Documentation](https://www.openssh.com/manual.html)
- [AWS EC2 Key Pair Guide](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html)
- [Secure File Transfer with scp](https://linux.die.net/man/1/scp)

---

## Summary
SSH is an essential tool for securely managing remote servers. By understanding its features and applying best practices, you can ensure secure and efficient access to your resources. Let’s practice setting up and using SSH in our next session! 🚀


---
### 2. **Create Instance of Windows**
AWS EC2 supports launching instances with Windows operating systems for various use cases, such as hosting .NET applications or running Windows-based tools.

#### **Steps to Launch a Windows Instance**:
1. **Navigate to EC2**:
   - Log in to the AWS Management Console.
   - Search for "EC2" and open the service.

2. **Launch Instance**:
   - Click on "Launch Instance."

3. **Choose AMI**:
   - Select a Windows Server AMI, such as **Windows Server 2019 Base**.

4. **Choose Instance Type**:
   - Select **t2.micro** (free tier eligible).

5. **Configure Instance Details**:
   - Leave default settings.
   - Optionally, assign an Elastic IP for a static public IP.

6. **Add Storage**:
   - Keep the default storage size or increase based on your needs.

7. **Configure Security Group**:
   - Add an inbound rule for RDP (port 3389).

8. **Launch and Download Key Pair**:
   - Download the `.pem` key file for accessing the instance.

9. **Retrieve Password**:
   - After launching, go to the instance details.
   - Click on "Get Windows Password" and decrypt it using the `.pem` key file.

10. **Connect to the Instance**:
    - Use Remote Desktop Protocol (RDP) on your local machine:
      - Hostname: Public IP of the instance.
      - Username: Administrator.
      - Password: Retrieved from the AWS console.

---

### 3. **Remote Access of Linux and Windows Machines**

#### **Linux Instance Remote Access**:
1. **Prerequisites**:
   - Ensure SSH is allowed in the security group.
   - Have the `.pem` key file downloaded during instance creation.

2. **Using SSH Command**:
   ```bash
   ssh -i /path/to/key.pem ubuntu@<Public-IP>
   ```

3. **Troubleshooting**:
   - Verify that the instance is running.
   - Ensure your local machine's IP is added to the security group.

#### **Windows Instance Remote Access**:
1. **Enable RDP Access**:
   - Ensure RDP is allowed in the security group.

2. **Using Remote Desktop Client**:
   - Open Remote Desktop Connection (Windows) or install an RDP client (Linux/Mac).
   - Enter the public IP address of the instance.
   - Use the Administrator username and decrypted password.

3. **Troubleshooting**:
   - Check the RDP port in the security group.
   - Ensure the instance has a public IP.

---

## Resources
- [AWS Security Group Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html)
- [Launching Windows Instances](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/LaunchingAndUsingInstances.html)
- [Connecting to Linux Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html)

---

## Key Takeaways
- Security Groups are essential for controlling access to your instances.
- RDP and SSH are the primary protocols for remote access to Windows and Linux instances, respectively.
- Proper configuration of Security Groups ensures both accessibility and security.


----

# SSH Service: Advanced Usage

## Topics Covered
- **SSH Service (Key-Based Authentication)**
- **Practical: Create Another Login User**
- **Deploy Web Server Using NGINX**
- **Deploy Web Server Using HTTPD**

---

## 1. **SSH Service (Key-Based Authentication)**
Key-based authentication in SSH replaces password-based authentication with a more secure method using cryptographic keys. This ensures enhanced security and eliminates the risks of brute force attacks.

### **Key Concepts**:
- **Private Key**: Stays on the client machine and is used to initiate authentication.
- **Public Key**: Placed on the server in the `~/.ssh/authorized_keys` file.
- SSH uses the private key to prove the identity of the client.

### **Steps to Set Up Key-Based Authentication**:
1. **Generate an SSH Key Pair**:
   ```bash
   ssh-keygen -t rsa -b 2048 -C "your_email@example.com"
   ```
   - `-t rsa`: Specifies the key type.
   - `-b 2048`: Sets the key size.
   - `-C`: Adds a comment for identification.

   Save the keys in the default location (`~/.ssh/id_rsa`).

2. **Copy the Public Key to the Server**:
   ```bash
   ssh-copy-id -i ~/.ssh/id_rsa.pub user@<server-ip>
   ```
   Alternatively, manually copy the contents of `id_rsa.pub` to the server's `~/.ssh/authorized_keys` file.

3. **Test the Connection**:
   ```bash
   ssh -i ~/.ssh/id_rsa user@<server-ip>
   ```

4. **Disable Password Authentication** (Optional):
   - Edit the SSH configuration file on the server (`/etc/ssh/sshd_config`):
     ```plaintext
     PasswordAuthentication no
     ```
   - Restart the SSH service:
     ```bash
     sudo systemctl restart sshd
     ```

### **Benefits**:
- No need to remember complex passwords.
- Stronger security with encrypted keys.
- Automated processes (e.g., scripts) become seamless.

---

## 2. **Practical: Create Another Login User**
Adding a new user to the system allows multiple individuals to securely access and manage the server.

### **Steps to Create a New User**:
1. **Add a New User**:
   ```bash
   sudo adduser <username>
   ```
   - Replace `<username>` with the desired username.
   - Follow the prompts to set a password and additional details.

2. **Add the User to the Sudo Group** (Optional):
   ```bash
   sudo usermod -aG sudo <username>
   ```

3. **Set Up SSH Access**:
   - Switch to the new user:
     ```bash
     su - <username>
     ```
   - Create the `.ssh` directory:
     ```bash
     mkdir ~/.ssh && chmod 700 ~/.ssh
     ```
   - Add the public key:
     ```bash
     echo "<public-key>" > ~/.ssh/authorized_keys
     chmod 600 ~/.ssh/authorized_keys
     ```

4. **Verify Access**:
   From your local machine, test SSH access:
   ```bash
   ssh -i ~/.ssh/id_rsa <username>@<server-ip>
   ```

---

## 3. **Deploy Web Server Using NGINX**
NGINX is a lightweight, high-performance web server and reverse proxy server used to host websites and applications.

### **Steps to Deploy NGINX**:
1. **Update the Package Manager**:
   ```bash
   sudo apt update
   ```

2. **Install NGINX**:
   ```bash
   sudo apt install nginx -y
   ```

3. **Start and Enable the NGINX Service**:
   ```bash
   sudo systemctl start nginx
   sudo systemctl enable nginx
   ```

4. **Verify the Installation**:
   - Open a web browser and navigate to the server's public IP.
   - You should see the default NGINX welcome page.

5. **Configure the Firewall** (If Enabled):
   - Allow HTTP and HTTPS traffic:
     ```bash
     sudo ufw allow 'Nginx Full'
     ```
   - Check the firewall status:
     ```bash
     sudo ufw status
     ```

6. **Host a Custom Website**:
   - Replace the default content:
     ```bash
     sudo nano /var/www/html/index.html
     ```
     Add your HTML content and save the file.

7. **Restart NGINX**:
   ```bash
   sudo systemctl restart nginx
   ```

8. **Verify the Website**:
   - Open the server's public IP in a web browser to view your hosted site.

---

## 4. **Deploy Web Server Using HTTPD**
HTTPD (Apache HTTP Server) is a widely-used open-source web server known for its flexibility and robustness.

### **Steps to Deploy HTTPD**:
1. **Update the Package Manager**:
   ```bash
   sudo yum update -y
   ```

2. **Install HTTPD**:
   ```bash
   sudo yum install httpd -y
   ```

3. **Start and Enable the HTTPD Service**:
   ```bash
   sudo systemctl start httpd
   sudo systemctl enable httpd
   ```

4. **Verify the Installation**:
   - Open a web browser and navigate to the server's public IP.
   - You should see the default Apache HTTPD test page.

5. **Configure the Firewall**:
   - Allow HTTP and HTTPS traffic:
     ```bash
     sudo firewall-cmd --permanent --add-service=http
     sudo firewall-cmd --permanent --add-service=https
     sudo firewall-cmd --reload
     ```

6. **Host a Custom Website**:
   - Navigate to the default document root:
     ```bash
     cd /var/www/html
     ```
   - Replace or add content to `index.html`:
     ```bash
     sudo nano index.html
     ```
     Add your HTML content and save the file.

7. **Restart HTTPD**:
   ```bash
   sudo systemctl restart httpd
   ```

8. **Verify the Website**:
   - Open the server's public IP in a web browser to view your hosted site.

---

## Resources
- [NGINX Documentation](https://nginx.org/en/docs/)
- [Apache HTTPD Documentation](https://httpd.apache.org/docs/)
- [OpenSSH Documentation](https://www.openssh.com/manual.html)
- [Linux User Management Guide](https://linuxize.com/post/how-to-create-a-new-user-on-linux/)

---

## Key Takeaways
- Key-based authentication is a secure and efficient way to access servers via SSH.
- Adding new users enables secure multi-user environments.
- NGINX and HTTPD provide robust platforms for hosting web applications.

------------

# Amazon EC2: Comprehensive Guide

This README provides detailed information about Amazon EC2, covering its dashboard, instance types, status checks, AMIs, launch templates, and purchasing options. The content is organized to ensure clarity and practical usability for users.

---

## Day 5 : **Amazon EC2 Dashboard Overview**

The Amazon EC2 Dashboard provides a centralized interface to manage EC2 resources. Key components of the dashboard include:

- **Instances**: View and manage running instances.
- **Launch Instances**: Create new EC2 instances using preconfigured settings.
- **Instance Types**: Explore the various types of instances available.
- **Elastic Block Store (EBS)**: Manage attached storage volumes.
- **Key Pairs**: Secure access to instances with SSH keys.
- **Security Groups**: Configure firewall settings for your instances.
- **Elastic IPs**: Allocate static public IP addresses to your instances.

---

## **Instance Types**

Amazon EC2 offers a wide range of instance types to suit diverse workloads. Below are the main categories:

### **General Purpose**
Balanced compute, memory, and storage.
- Examples: M5, T2, T3, M6a, Mac2

### **Compute Optimized**
Ideal for compute-intensive tasks.
- Examples: C5, C6i, C7g

### **Memory Optimized**
Designed for high-performance databases and memory-intensive applications.
- Examples: R5, X1, X2idn

### **Storage Optimized**
For workloads requiring high, sequential read/write access to large data sets.
- Examples: I3, D2, H1

### **Accelerated Computing**
Designed for applications requiring GPUs or hardware accelerators.
- Examples: P3, G5, Inf1

### **High-Performance Computing (HPC)**
For HPC applications requiring low latency and high performance.
- Examples: Hpc6a, Hpc7g

[Refer to AWS Instance Types Documentation](https://aws.amazon.com/ec2/instance-types/)

---

## **Status Checks for Amazon EC2 Instances**

### **Overview**
Amazon EC2 continuously monitors instance health via automated status checks. These checks ensure instances are running without issues.

- **System Status Check**: Verifies the infrastructure hosting your instance is functioning correctly.
- **Instance Status Check**: Monitors the software and network configuration of your instance.

### **Common Failure Causes**
- Networking issues
- Exhausted memory
- Corrupted file systems
- Kernel incompatibilities

### **CloudWatch Alarms**
You can set alarms to monitor status checks and take automated actions, such as instance recovery, if issues are detected.

[Refer to AWS Status Checks Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/monitoring-system-instance-status-check.html)

---

## **AMI (Amazon Machine Image)**

### **AMI Types**
1. **EBS-backed AMI**: Boot volume stored on Amazon EBS.
2. **Instance-store-backed AMI**: Boot volume stored on local instance storage.

### **Creating an AMI**
1. Navigate to the EC2 dashboard.
2. Select the instance you wish to create an AMI from.
3. Choose **Actions > Image > Create Image**.
4. Provide the necessary details and click **Create Image**.

### **Copying an AMI**
You can copy AMIs between regions to enhance redundancy or deploy in multiple regions.

[Refer to AWS AMI Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html)

---

## **Launch Templates**

Launch templates enable consistent configuration of EC2 instances. They support settings like:
- AMI ID
- Instance Type
- Security Groups
- Key Pair

### **Creating a Launch Template**
1. Open the EC2 dashboard.
2. Navigate to **Launch Templates**.
3. Click **Create Launch Template**.
4. Fill in required details, including AMI ID, instance type, and security groups.

[Refer to AWS Launch Template Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-launch-templates.html)

---

## **Purchasing Options**

### **Overview**
Amazon EC2 offers several purchasing options to optimize costs:

1. **On-Demand Instances**: Pay for instances by the second.
2. **Savings Plans**: Commit to a consistent usage level for 1 or 3 years.
3. **Reserved Instances**: Commit to specific configurations for 1 or 3 years.
4. **Spot Instances**: Use spare EC2 capacity at reduced costs.
5. **Dedicated Hosts**: Full physical servers for your instances.
6. **Dedicated Instances**: Single-tenant instances.
7. **Capacity Reservations**: Reserve capacity in specific AZs.

[Refer to AWS Purchasing Options Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-purchasing-options.html)

---

## **Summary**
This guide provides a foundational understanding of EC2, enabling users to make informed decisions about configuring and managing their instances. Leverage AWS documentation for deeper insights and stay updated with the latest AWS features.



