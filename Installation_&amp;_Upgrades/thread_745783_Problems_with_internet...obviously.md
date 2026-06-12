---
title: "Problems with internet...obviously"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by mfk on 2008-04-04
Ok, first of all this is what I get with ifconfig (I cut out some of the other info). I have a linksys WMP 54G router and a PCI card. 

Problem #1: My internet hangs when I download p2p files at high rates. I know that my ISP does not throttle my connection. My roommate gets great speeds. I had the same problem with windows. 

problem #2: For some reason I can't connect to internet unless I disable the firewall using Firestarter.

Problem #3: I feel like reinstalling ubuntu, but for some reason the installation goes only up to 50% and stops during the partition portion. I checked the cd...it passed the check. 



lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:948 (948.0 b)  TX bytes:948 (948.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:18:F8:A8:AB:41  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f8ff:fea8:ab41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3925 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3473167 (3.3 MB)  TX bytes:648349 (633.1 KB)

---

### Post by Pumalite on 2008-04-04
Firestarter can be configured. You need to open the port needed by your p2p

---

### Post by mfk on 2008-04-04
I already did that. Ports are open. Most of the time I can't download faster than 40, 60, 80kbs...but sometimes if it gets in the hundreds internet drops off. It still tells me that I am connected but I have to restart the computer in order for me to go on internet or do anything .

---

### Post by Pumalite on 2008-04-04
I would then suspect your provider. You can try disabling Firestarter and getting a router (a real hardware firewall), have it provide you with DHCP. I have found out that that way my connection cannot be dropped.

---

### Post by mfk on 2008-04-05
Ok, I guess I figured it out, somewhat. First of all I got rid of Firestarter, so far internet works. Second, It was the site that I was getting my torrents from. By the way, Russian sites rule...I just have to learn how to read russian. My third problem, I still don't know, but now I don't have to reinstall. :)

---

