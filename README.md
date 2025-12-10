# Web Application Deployment on AWS EC2 (Using Nginx)

This project demonstrates end-to-end deployment of a web application on Amazon EC2 using Ubuntu 24.04 and Nginx. It includes launching an EC2 instance, configuring security groups, installing Nginx, deploying a custom HTML page, and making the application publicly accessible.

---

## Project Overview

- Launched and configured an EC2 instance on AWS  
- Set up security groups to allow SSH & HTTP access  
- Installed and enabled the Nginx web server  
- Deployed a custom HTML webpage  
- Verified deployment using the instance’s public IP address  

---

## Technologies Used

| Component | Technology |
|----------|------------|
| Cloud Provider | **AWS EC2** |
| OS | **Ubuntu 24.04 LTS** |
| Web Server | **Nginx** |
| Tools | Linux, Bash, SSH |
| Frontend | HTML |

---

# 1. Launching the EC2 Instance

### Steps:
1. Open **AWS Console** → EC2 → *Launch Instance*
2. Choose AMI: **Ubuntu Server 24.04 LTS**
3. Choose instance type: **t2.micro / t3.micro (Free Tier)**
4. Create or select a **Key Pair (.pem)**
5. Configure Security Group:
   - Allow **SSH (22)** → Your IP / Anywhere  
   - Allow **HTTP (80)** → Anywhere  
6. Launch the instance 

---

# 2. Connecting to the EC2 Instance

Using EC2 Instance Connect:
```
ubuntu@ip-172-31-26-68:~$
```
You are now inside your cloud server.

Meaning:

| Part | Description |
|------|-------------|
| `ubuntu` | Default username |
| `ip-172-31-xx-xx` | Private EC2 IP |
| `$` | Standard user shell |

You are now inside your EC2 cloud server.

# 3. Installing and Enabling Nginx

```bash
sudo apt update -y
sudo apt install nginx -y
sudo systemctl enable --now nginx
```
Check service status:
```
systemctl status nginx
```
Test locally:
```
curl -I http://127.0.0.1
```
# 4. Deploying the Custom Web Application

Create your custom HTML page:
```
sudo bash -c 'cat > /var/www/html/index.html <<EOF
<!doctype html>
<html>
<head><meta charset="utf-8"><title>My EC2 Web App</title></head>
<body style="font-family:Arial;max-width:700px;margin:40px auto">
<h1>Web Application Deployment on AWS EC2</h1>
<p>Deployed by: <b>Rakesh</b></p>
<p>Server: Ubuntu + Nginx on AWS EC2</p>
<p>Status: SUCCESS </p>
</body>
</html>
```

Reload Nginx to apply changes:
```
sudo systemctl reload nginx
```
# 5. Accessing the Web Application

Open in browser:
```
http://<PUBLIC-IP>
```
Example:
```
http://13.62.128.19
```
Your custom webpage will appear.

# Architecture Diagram
User Browser → AWS EC2 → Ubuntu Server → Nginx Web Server → HTML App

## Screenshots

### 1. Nginx Default Welcome Page
![Nginx Default Page](screenshots/nginx-default-page.png)

### 2. Custom Deployed Web Page
![Custom Web Page](screenshots/custom-web-page.png)

# Instance Details
| Parameter            | Value                |
| -------------------- | -------------------- |
| **Instance ID**      | i-0956ae52dba68cb08  |
| **Public IP**        | 13.62.128.19         |
| **Operating System** | Ubuntu 24.04 LTS     |
| **Web Server**       | Nginx                |
| **Status**           | Running Successfully |

# Final Outcome

- EC2 instance launched successfully

- Nginx installed and running

- Custom webpage deployed

- Application is publicly accessible

# Future Enhancements

- Deploy Node.js, Flask, or React

- Enable HTTPS (SSL) using Let’s Encrypt

- Implement CI/CD (GitHub → EC2)

- Configure Nginx as a reverse proxy

- Dockerize the application

# Author
Rakesh Dabbikar
