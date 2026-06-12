---
title: "No wired connection after shutdown after upgrade to lucid lynx"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by erikthedrink on 2010-05-09
Tuesday the 4th of May, I upgraded from 9.10 to 10.04.  After restarting, it worked fine.  On the morning of Thursday the 6th, I shut the system down.  On Thursday evening, I turned on the laptop, and my wired connection is not active. My cable company verified a good signal is coming from my modem.  I will try using the live cd in order to post the statistical results of any terminal functions you want me to run.  Currently, I am using my Samsung Jack.

---

### Post by erikthedrink on 2010-05-09
Using the Live CD, I am able to connect to the internet.  Under the Live CD, here are the results of 'ifconfig'
Link encap:Ethernet  HWaddr 00:1b:38:97:71:c4  
          inet addr:173.23.93.55  Bcast:173.23.93.255  Mask:255.255.254.0
          inet6 addr: fe80::21b:38ff:fe97:71c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9037 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14042010 (14.0 MB)  TX bytes:1303902 (1.3 MB)
          Interrupt:16 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3800 (3.8 KB)  TX bytes:3800 (3.8 KB)

If I remember correctly, without the live CD, my RX and TX bytes were much smaller and the same exact amount (less than a MB).:confused:

---

### Post by erikthedrink on 2010-05-10
This is the result of 'ifconfig' without a live CD

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7584 (7.5 KB)  TX bytes:7584 (7.5 KB)

---

### Post by erikthedrink on 2010-05-10
Nevermind! I Just lost my ability to mirror screens on my monitor panel. I am reinstalling 9.04 and then only upgrading to 10.04.  I will wait for the bugs to get worked out.

---

