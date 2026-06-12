---
title: "install ubuntu in vmware as guest on windows xp"
date: 2006-03-12
forum: Installation &amp; Upgrades
---

### Post by al_gomez on 2006-03-12
Hello, I recently installed ubuntu 5.10 on vmware server (beta).  The host is a laptop toshiba satellite m35x-s149. Running windows xp pro sp2. 
The problem I have is that I can't get internet connection. I used a community wireless network provided by my landlord. 
I don't know why ubuntu can't recognize the wireless. 
VMware has this settings:

Memory 192 MB
Hard Disk (IDE 0:0) 
CD-ROM (IDE 1:0)     Auto Detect
Ethernet                  NAT
Processors               1

when I open the Virtual Network Editor, I am no surre what setting I need to have. 
Under summary I see:

VMnet0 (bridged)  Bridged to Atheros AR5004G Wireless Network Adapter - Packet Scheduler Miniport

VMnet1 (host-only) a private network shared with the host
VMnet8 (NAT) Used to share the host's IP address

There are more tabas, I am not sure if is neccesary I post what they show. I would like to ask if someone can help me with the VMWare settings, and what other stepes after installation of ubuntu on the virtual server s done, I need to do. 

Any help is greatly appreciated.

---

### Post by alamba on 2006-03-12
You can either use VMnet0 (bridged) or VMnet8 (NAT). If you're on a DHCP server and don't have an issue of how many IP's you can use then use the bridged interface. 

This let's the virtual interface talk "directly" to the network by giving it an IP for itself. Once configured you can access the internet easily.

Incase you don't have access to more IP's over your network (via DHCP or otherwise) then use NAT. In this case the physical machine NAT's the traffic between the virtual machine and the network.

Let me know incase of any questions or help in setting it up.

Akshay

---

