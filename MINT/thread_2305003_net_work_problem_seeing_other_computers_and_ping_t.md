---
title: "net work problem seeing other computers and ping them"
date: 2015-12-01
forum: MINT
---

### Post by sarah101 on 2015-12-01
Hi all, first post in this forum. new to computers and Linux i have install Linux mint 17.2 and have been trying to work out the networking now for about 3 week with no success. this is the information from my computer (client) 
inxi

CPU~Dual core Intel Celeron CPU N2840 (-MCP-) clocked at Min:1826.000Mhz Max:1992.000Mhz Kernel~3.13.0-37-generic x86_64 Up~2:01 Mem~1742.3/3839.9MB HDD~500.1GB(34.1% used) Procs~221 Client~Shell inxi~1.9.17  

```
inxi -n 

Network:   Card-1: Qualcomm Atheros AR9485 Wireless Network Adapter driver: ath9k 
           IF: wlan0 state: up mac: 30:10:b3:59:21:fd
           Card-2: Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller driver: r8169 
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: 38:63:bb:c6:f4:6f
ifconfig

eth0      Link encap:Ethernet  HWaddr 38:63:bb:c6:f4:6f  
          inet addr:10.227.121.1  Bcast:10.227.255.255  Mask:255.255.0.0
          inet6 addr: fe80::3a63:bbff:fec6:f46f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27281 (27.2 KB)  TX bytes:122186 (122.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2874 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2874 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:380598 (380.5 KB)  TX bytes:380598 (380.5 KB)

pan1      Link encap:Ethernet  HWaddr 4a:5e:09:01:c8:7b  
          inet addr:10.227.121.1  Bcast:10.227.121.255  Mask:255.255.255.0
          inet6 addr: fe80::485e:9ff:fe01:c87b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:70802 (70.8 KB)

vlan1     Link encap:Ethernet  HWaddr 38:63:bb:c6:f4:6f  
          inet addr:10.227.121.1  Bcast:10.227.121.255  Mask:255.255.255.0
          inet6 addr: fe80::3a63:bbff:fec6:f46f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:30211 (30.2 KB)

wlan0     Link encap:Ethernet  HWaddr 30:10:b3:59:21:fd  
          inet addr:172.16.197.22  Bcast:172.16.207.255  Mask:255.255.240.0
          inet6 addr: fe80::3210:b3ff:fe59:21fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45425145 (45.4 MB)  TX bytes:4661764 (4.6 MB)

ping freezes here:

so far i have added other host names in to this file 

/etc/hosts/

127.0.0.1    localhost
#127.0.1.1    wayneman
172.16.1.1    wayne-sat1
#127.0.1.1    wayne-sat
10.227.121.1    wayneman

#172.10.10.11    wayne-sat
#127.0.1.1    wayne-vbtel
#10.227.121.     wayne-vb 
```

i can ping myself on the network and both work-group are in view capacity but not able to ping eah other. 

```
$ ping 172.16.1.1
PING 172.16.1.1 (172.16.1.1) 56(84) bytes of data.
```

not realy to sure about the information needed and still reading on the path throughout networking to get a better understanding. Getting there slowly eg in the /etc/hosts file is all host names put in here or just the local hostnames (client). 



Have not configured dns sofar. 

Thanks in advance

sorry look very untidy will have to work on this :oops:

---

### Post by howefield on 2015-12-02
Thread moved to the "*MINT*" sub forum.

---

