# VPC
A virtual private cloud (VPC) is a virtual network dedicated to your AWS account. It is logically isolated from 
other virtual networks in the AWS Cloud. You can launch your AWS resources, such as Amazon EC2 instances, into your 
VPC.

![image](https://github.com/user-attachments/assets/68942c35-be00-4be2-8234-d282f5941caf)
## create VPC 

for creating a VPC , flow the following steps:
go to AWS Console ,then click Services ,then go to Networking & Content Delivery , click on VPC , click on Your VPCs.
after these steps on click on VPC.
![1](https://github.com/user-attachments/assets/4aa3c1af-543a-42c6-b15d-53d1c99119c3)

## CREATE SUBNETS
for VPC , we will create four subnets. 

![2](https://github.com/user-attachments/assets/cc2ba8ca-c4dc-4ade-a57a-1d6fbf7327b6)

## Create Internet gateway and attach to VPC 
Internet Gateways. An internet gateway is a horizontally scaled, redundant, and highly available VPC component 
that allows communication between instances in your VPC and the internet. It therefore imposes no availability risks or 
bandwidth constraints on your network traffic.

create a gateway then attach it to your VPC ,

![Screenshot 2024-11-17 223621](https://github.com/user-attachments/assets/ff62f68b-5ef3-4a64-9227-ef0aff91461b)


## Create Virtual Private Gateway and Attach to VPC 
It can be a physical or software appliance. The anchor on the AWS side of the VPN connection is called a virtual 
private gateway. The following diagram shows your network, the customer gateway, the VPN connection that goes to 
the virtual private gateway, and the VPC.
create a VPGW-> actions -> attach to VPC
![Screenshot 2024-11-17 223721](https://github.com/user-attachments/assets/7fad0fb1-ea67-47f3-a249-cd6a4afd3dfa)


## Create route tables and attach to subnets 
Route Tables. A route table contains a set of rules, called routes that are used to determine where network 
traffic is directed. Each subnet in your VPC must be associated with a route table; the table controls the routing for the 
subnet. 
One route for Internet gateway, another for Virtual private gateway (R1-IGW and R2-VGW) 
* Route - 0.0.0.0/0 to IGW
* Route - 192.168.0.0/16 to VGW

create route tables ->then add route
![Screenshot 2024-11-17 223921](https://github.com/user-attachments/assets/71cf355e-01fd-47b4-ba53-122818ff62b4)

  

  ![Screenshot 2024-11-17 224006](https://github.com/user-attachments/assets/4b9652ae-44c8-4611-9b4c-096c9ca97c23)


Attach routing tables to subnets. R1-IGW to S3-Public and S4-Public, public network required to have internet access. 
Attach R2-VGW to S1-Private and S2-Private (No internet become a private subnets)

## create instances

• now we have to create two instnaces    where we have to enable the public     IPv4 .

•then on both instance we have to       downlaod the web server here i have    downlaoded the apache2 server

-- after that i chech that my             instances are working or not .

![4](https://github.com/user-attachments/assets/88ddf6af-ae8f-486d-83bf-7b790b9a6313)


## now we have to create the load         balancer

--where we have to give vpc, aviablity   zone of the ec2 instance

•then we have to create the target      group where we have to select the two  insatance we have create then we have  to go to helath check edited option    which was present below the load       balancer is create ,then edit it


•after that come to load balancer       where we have to select the target     group which we have created then make  the load balancer , it will look like  the given image below .
![5](https://github.com/user-attachments/assets/aad3a002-0308-49e2-9539-6674968dd22a)


*now put on any one instance write following commands in putty -*

* ```
  htop
  ```
  ```
  seq 999999999999999999999999999999999999999999999999999999999 > /dev/null &
  ```
  ```
  htop
  ```
