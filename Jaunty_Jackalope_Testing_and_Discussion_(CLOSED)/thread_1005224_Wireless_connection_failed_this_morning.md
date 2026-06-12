---
title: "Wireless connection failed this morning"
date: 2008-12-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2008-12-08
This morning my Satellite Pro laptop will not connect to my wireless network. I cannot isolate when the changes happened to the system, it presume it was one of the upgrades of Jaunty that did it, I've not done anything at all on this machine. Here is the relevant data:-

> peter@toshsat:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:f5:92:26:5b  
          inet6 addr: fe80::211:f5ff:fe92:265b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:a0:d1:26:75:77  
          inet addr:192.168.0.14  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe26:7577/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4821 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11704509 (11.7 MB)  TX bytes:371787 (371.7 KB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3288 (3.2 KB)  TX bytes:3288 (3.2 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-F5-92-26-5B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:2021
          TX packets:1399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:12641 (12.6 KB)  TX bytes:93968 (93.9 KB)
          Interrupt:17 


> peter@toshsat:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wifi0
       version: 01
       serial: 00:11:f5:92:26:5b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:26:75:77
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.14 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:1f:e7:32:19:54
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


It looks like the system attempts to connect to the router but fails. Any suggestions that might help?

---

### Post by markg48 on 2008-12-08
didnt no new ubuntu was out for testing yet but any way did u install wireless drivers ?

---

### Post by Peter09 on 2008-12-08
Its been running fine under Jaunty for weeks, then this happened this morning, something must have changed, do not know what. Excluding the possibility of a hardware fault its seems more likely that an upgrade has caused it.

---

### Post by markg48 on 2008-12-08
dont no if this applies to u but u could try installing madwifi drivers

or re isntall your wireless driver for ubuntu if u did manual  install drivers

---

### Post by markg48 on 2008-12-08
what did u exactly update ?

---

### Post by Peter09 on 2008-12-08
Thats an idea Markg48, however as I want to keep this laptop as a vanilla Jaunty install (for testing) and keeping it uncomplicated. I do not really want to depart from Jaunty. 

The machine is only used to test Jaunty so I am not desperate to find a unconventional work around. However I would like a fix for it:p

It is a bit of a puzzle as I cannot quite understand when and why this happened.

---

### Post by markg48 on 2008-12-08
did u update the kernel  coz u need to rebuild drivers if you do that

---

### Post by markg48 on 2008-12-08
:D downloading jaunty now alpha 1

---

