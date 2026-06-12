---
title: "Instalation of Breezy/Hoary , DHCP fails"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by notos on 2006-03-14
Ok I downloaded the Ubuntu Breezy to make a clean install (raplacing my old Win 98 ;) ) and when it get to the part to "configuring the network" it just fails.

so I got this Debian 3.0 CD so tried withn it... and voila it does detect my connection and configures it automaticaly... ok ... but i want ubuntu so i (to see if it works) download Ubuntu Warty and yes it does configure my network

So my Dilema is if i Upgrade to Hoary or Breezy I do loss my Connection because DHCP fails to detect my connection but if i use Sarge/Warty it does not have any complain

My "network" set up is this

My PC (Old PII 400mhz :() has one on-board Ethernet and i conected a PCI Ethernet and they are:
```

0000:00:09.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
0000:00:0b.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 10)

```
the D-link one is the one im now using because  the on board one (Davicom) freezes the machine while Doing DHCP

My router Is a SpeedStream 5200 (i upgraded the firmware to make it work as a router) and is conected **directly** to my PC

I think it is my Setup but also is Bug problem because of Sarge/Warty does connect but not Hoary/Breezy

Help Please

---

### Post by Darkriser on 2006-03-14
I have WiFi router between my PC and cable modem, which I use as DHCP server, as well. During Breezy install the DHCP failed (which is ok, because the installation didn't have any clue about the SSID, WEP key, etc. so couldn't establish communication with the router). I just selected Not to configure network at this time. After instalation was completed, I set-up my USB WiFi adapter and the DHCP works perfectly. Maybe this could help you.

---

### Post by derjames on 2006-03-14
Notos, I had a similar warning when installing Breezy, during Network installation using DHCP, the configuration fails, this is usual, just ignore this warning and select "DO not configure network at this time" and let Ubuntu finish the installation

When in Ubuntu, 
-connect the Ethernet cable, 
-enter to setting>network
-in the new window; appear Ethernet and Modem which are both disabled
-Enable Ethernet (and/or modem)
-Click on properties
-enter the appropriate IP address, etc.
-Click DNS tab
-Enter DNS info
-and Ready to surf the WEB!!!
quite similar to Darkriser advice, though

Hope this helps!

DerJames

---

### Post by notos on 2006-03-14
ill try that but where do i get the DNS/ip info and all? i not used to configure the network THX :)

---

### Post by derjames on 2006-03-14
I understand you are setting up Ethernet to surf the Web, is this true?Also I understand you have a Broadband connection, thus the IP/DNS etc.. are given by your ISP (Internet Service Provider) ... for example BT, Tiscalli, AT&T, etc...
hope this helps

---

### Post by notos on 2006-03-15
True ... the problem is My ISP (Prodigy Infinitum, MX) only gives Suport to windows... 

so i know i can access my Router Config page in 192.168.254.254

if i go to Setup->DHCP

it says 
DHCP Server: 	Enabled
Start IP Range: 192.168.254.1
End IP Range: 192.168.254.253
IP Netmask: 255.255.255.0
Default Gateway: 192.168.254.254
DNS Server:  Use WAN
Domain Name: Domain.Invalid

The Ip is the one my ISP Automaticaly sets? Ie 201.143.x.x ?

---

### Post by notos on 2006-03-16
Ok  news news :)


As long as i dont update the Warty Kernel (2.6.8-6) to the breezy one i can connect to internet

other thing

Is normal that i cant acces the 192.168.254.254 config page when using the new Kernel?

HELP!

---

