---
title: "Wireless detection disappeared"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by jovean on 2009-12-22
This morning I turned on the computer, and my wireless connection is on (I can turn it on and off with the hotkeys), but none of the local networks (including my home network) are detected - so I can't connect to any of them.  (I am currently using a wired connetion).

I did install some updates yesterday, so it might be that, but ... how to resolve?

I am using an LG R510, here is my ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:23:8b:68:50:39  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe68:5039/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:828078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:826321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:837062851 (837.0 MB)  TX bytes:75117753 (75.1 MB)
          Interrupt:28 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18890 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3585162 (3.5 MB)  TX bytes:3585162 (3.5 MB)

ra0       Link encap:Ethernet  HWaddr 00:17:c4:65:18:33  
          inet6 addr: fe80::217:c4ff:fe65:1833/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 
```

---

