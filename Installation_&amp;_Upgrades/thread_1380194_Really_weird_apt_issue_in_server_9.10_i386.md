---
title: "Really weird apt issue in server 9.10 i386"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by Tralce on 2010-01-13
When installing through apt-get, or upgrading, downloads stop. I will be in the midst of downloading a file of any size (or even running apt-get update) and the transfer will simply stop. If I ctrl+c it, then start the install/update/upgrade over it will pick up where it left off, but it gets rather tedious as I have to do this 10-20 times during any upgrade. Occasionally, running /etc/init.d/networking restart will get me through the rest of a download uninterrupted. 

This only happens on this specific computer (a PowerEdge 2650 with dual Gbit LAN cards) and none other on my network. I am using the same release on a Poweredge 1550 with no issues whatsoever. 

Also, downloads with Firefox have no issues at all. 

Any clus about what's going on here?

---

### Post by Tralce on 2010-02-06
Please note that I have had no success in fixing this, and that it's extremely important that it gets sorted out!

---

### Post by mushwars on 2010-02-06
this is a network issue not apt, are you using wireless, if so what driver/model card are you using, what wireless manager? do you experience temporary SLOW loading times on pages? Can you stream youtube videos without having to wait for them to buffer?

---

### Post by Tralce on 2010-02-06
For some reason it obsessively drops pings from google.com and us.archive.ubuntu.com:

root@2uterror:~# ping us.archive.ubuntu.com
PING us.archive.ubuntu.com (91.189.88.45) 56(84) bytes of data.
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=1 ttl=46 time=132 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=2 ttl=46 time=138 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=3 ttl=46 time=144 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=54 ttl=46 time=151 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=55 ttl=46 time=159 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=56 ttl=46 time=142 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=57 ttl=46 time=156 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=58 ttl=46 time=171 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=59 ttl=46 time=234 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=60 ttl=46 time=240 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=61 ttl=46 time=148 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=110 ttl=46 time=194 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=111 ttl=46 time=153 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=112 ttl=46 time=159 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=113 ttl=46 time=148 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=114 ttl=46 time=195 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=115 ttl=46 time=151 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=116 ttl=46 time=153 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=117 ttl=46 time=151 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=118 ttl=46 time=137 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=167 ttl=46 time=199 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=168 ttl=46 time=170 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=170 ttl=46 time=217 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=171 ttl=46 time=134 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=172 ttl=46 time=137 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=173 ttl=46 time=156 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=174 ttl=46 time=143 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=175 ttl=46 time=151 ms
^C
--- us.archive.ubuntu.com ping statistics ---
191 packets transmitted, 28 received, 85% packet loss, time 191321ms
rtt min/avg/max/mdev = 132.019/163.404/240.070/29.013 ms


So, now, the question is, "why is it dropping packets like that, and how do I go about fixing it?" 

It's connected to the same switch as my desktop and two other laptops and they do not have this issue. It's a fresh install of Server 9.10 i386. The desktop has 9.10 x64 Desktop and the laptops have Desktop i386. Nothing else is different. Here's some info that may be pertinent.

root@2uterror:~# lspci|grep Ethernet
03:06.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5703X Gigabit Ethernet (rev 02)
03:08.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5703X Gigabit Ethernet (rev 02)
root@2uterror:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:b9:c5:a1  
          inet addr:10.0.1.9  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:feb9:c5a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6803 errors:3 dropped:0 overruns:0 frame:6
          TX packets:4559 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:808606 (808.6 KB)  TX bytes:370583 (370.5 KB)
          Interrupt:28 

eth1      Link encap:Ethernet  HWaddr 00:0d:56:b9:c5:a2  
          inet addr:10.0.1.10  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:feb9:c5a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8550 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6055 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11689400 (11.6 MB)  TX bytes:470343 (470.3 KB)
          Interrupt:29

---

