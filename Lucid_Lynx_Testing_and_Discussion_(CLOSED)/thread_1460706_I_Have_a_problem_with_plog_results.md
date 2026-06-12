---
title: "I Have a problem with plog results"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-23
when i run plog i get this:
```
Apr 23 13:29:21 ofir-desktop pppd[6455]: Using interface ppp0
Apr 23 13:29:21 ofir-desktop pppd[6455]: Connect: ppp0 <--> eth1
Apr 23 13:29:22 ofir-desktop pppd[6455]: PAP authentication succeeded
Apr 23 13:29:22 ofir-desktop pppd[6455]: peer from calling number 00:30:88:12:EB:E8 authorized
Apr 23 13:29:22 ofir-desktop pppd[6455]: Cannot determine ethernet address for proxy ARP
Apr 23 13:29:22 ofir-desktop pppd[6455]: local  IP address 
Apr 23 13:29:22 ofir-desktop pppd[6455]: remote IP address 
Apr 23 13:29:22 ofir-desktop pppd[6455]: primary   DNS address 2
Apr 23 13:29:22 ofir-desktop pppd[6455]: secondary DNS address 

```why do i get " Cannot determine ethernet address for proxy ARP"

This is my ifconfig results for now any way.:
```
eth0      Link encap:Ethernet  HWaddr 00:16:17:ca:28:0c  
          inet6 addr: fe80::216:17ff:feca:280c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:708 (708.0 B)
          Interrupt:23 

eth1      Link encap:Ethernet  HWaddr 00:1d:0f:ff:c7:c3  
          inet6 addr: fe80::21d:fff:feff:c7c3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2046309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1935118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1849638238 (1.8 GB)  TX bytes:501924058 (501.9 MB)
          Interrupt:18 Base address:0xf800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28700 (28.7 KB)  TX bytes:28700 (28.7 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:93.173.217.188  P-t-P:93.173.192.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:931 errors:0 dropped:0 overruns:0 frame:0
          TX packets:870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:551249 (551.2 KB)  TX bytes:105634 (105.6 KB)

```Thanks in advance.

---

