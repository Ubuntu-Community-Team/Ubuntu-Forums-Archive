---
title: "Internet Problems"
date: 2006-09-17
forum: Installation &amp; Upgrades
---

### Post by RinSess on 2006-09-17
I need help connecting to the internet(ADSL), which is perfectly fine on Windows XP.

My external modem is an iConnectAccess621 and I use the ethernet connection.
Ubuntu is on the same hard drive as Windows XP
I don't have a firewall in Ubuntu
Network Proxy is direct internet connection 
Network Settings is Eth0, set to DHCP and is active

**Results from "ifconfig" are as follows**
eth0      Link encap:Ethernet  HWaddr 00:13:72:0E:3F:95
          inet addr:192.168.1.100  Bcast:192.168.1.255  
          Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:fe0e:3f95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:2208 (2.1 KiB)  TX bytes:3574 (3.4 KiB)
          Base address:0xcce0 Memory:fe3e0000-fe400000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

I've so far done the following:

**1. Configure pppoe typing in "sudo pppoeconf"**
   The ethernet card was detected. However, the following message 
   appeared:

   "Sorry, I scanned 1 interfact, but the Access Concentrator of    
   your provider did not respond. Please check your network and 
   modem cables. Another reason for the scan failure may also be 
   another running pppoe process which controls the modem"

**2. Manual Connection typing in "sudo pon dsl-provider" **
   Funny characters kept appearing every few seconds and I had to 
   shutdown the terminal.

**3. Ping an internet address**
I typed "ping -c3 198.182.196.56" and "ping -c3 www.google.com" which both resulted  in 3 packets transmitted , 3 received and 0% packet loss. 

What else can I do to get connected to the internet?

---

