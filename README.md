# CISCONETWORKING

<h2>Description</h2>
Abacus company is a fast-growing company in Las Vegas, Nevada with more than 2 million customers, globally.  The company deals with selling and buying of nft's, which are basically operated from the headquarters.  The company is intendng to open a branch near the local community of Fremont.  Thus, the company required an IT grad to design the network for the branch.  The network is intended to operate seperately from the HQ network.
Being a small network, the company has the following requirements during implementation;
a) One router and one switch to be used--CISCO.
b) 3 Departments (Admin\IT, Finance/HR and Customer Service/Reception)
c) Each department is required to be in different VLANS.
d) Each department is require to have wireless network for the users.
e0 Host devices in the network are required to obtain IPv4 address automatically.
f) Devices in all departments are required to communicate with each other.

*Assume the ISP gave out a base network of 192.168.1.0, as the Network Engineer, we design and implement a network considering the above requirements.

<h2>Languages and Utilities Used</h2>
- <b>CISCO's PACEKT TRACER</b>

<h2>Environments Used </h2>
  
<h2>Program walk-through:</h2>
-DESIGNING THE NETWORK
<p align="center">
<img src=https://i.imgur.com/OajGLTE.png height="65%" width="65%" />
<br />
<br /> 

In the CISCO switch, we need to execute the following commands to setup VLANS
Switch>en\Switch>config t\  Then enter the range of interfaces--Switch(config)# int range fa0/2-4 (...5-7;8-10)
Switch(config-if-range)#switchport mode access\Switch(config-if-range)#Switchport access vlan 10

<p align="center">
<img src="https://i.imgur.com/cnVfO5x.png height="65%" width="65%" />
<br />
<br /> 
<p align="center">
<br />
<br />
Configuring Access Points.  
-Go to Port 1. SSID='Admin'  Authentication IS WPA2-PSK. Password='Sunshine1'
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/4Roozzj.png height="65%" width="65%" />
<br />
<br />
-Router configuration.  We need to turn Gig0 up.  Router>en\Router# config t\Router(config)#int gig0/0.  We then need to configure Gig0 as trunk to allow multiple interfaces\subinterfaces we created while creating VLANS.  Use these commands: Switch(config)int fa0/1\Switch(config-if)#switchport mode trunk\switchport(config-if_#do w <br/>
We then create InterVlans so that we can create multiple vlans from a single VLan, using Gig0 as a default gateway.  Router(config)#gig0/0.10 is the command. Afterwards; we have to specify encapsulation to aggregate logic interfaces using Router(config-subif)#encapsulation dot1Q.10 (..20&30) and assign the vlans their respective ip addresses and subnet mask.  For Vlan 10 we use: Router(config-subif)#ip address 192.168.1.1 255.255.255.192

<p align="center">
<img src="https://i.imgur.com/JKuzkbH.png height="65%" width="65%" />
<br />
<br />
-Router configuration for DHCP, DNS, DOMAIN, and DEFAULT GATEWAY services <br/>
<p align="center">
In a CISCO, execute the following commands:
Router(config)#servic dhcp\Router(config)#ip dhcp pool Admin-Pool (Finance, CS)\Router(dhcp-config)#ip dhcp pool Admin-Pool\Router(dhcp-config)#dns-server 192.168.1.1\Router(dhcp-config)#domain Admin.com \Router(dhcp-config)#network 192.168.1.0 255.255.255.192\Router(dhcp-config)#default-router 192.168.1.1
<p align="center">
<img src="https://i.imgur.com/ur9GHjC.png height="65%" width="65%" />
<br />
<br />
CONFIGURING DEVICES FOR DHCP
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/WDW1ibT.png height="65%" width="65%" />
<br />
<br />
<p align="center">
-All devices, including smartphones and laptops are connected AND can ping each other!  <br/>
<p align="center">
<img src="https://i.imgur.com/EsbbsF2.png height="65% width="65%"  />
<img src="https://i.imgur.com/yJxqniL.png height="65% width="65%"  />
<img src="https://i.imgur.com/yJxqniL.png  height="65%" width="65%" />
<img src="https://i.imgur.com/s3vjRaM.png height="65%" width="65%" />
<img src=https://i.imgur.com/ea7odMj.png height="65%" width="65% />
<p align="center">
<img src="https://i.imgur.com/ea7odMj.png height="65%" width="65% />




