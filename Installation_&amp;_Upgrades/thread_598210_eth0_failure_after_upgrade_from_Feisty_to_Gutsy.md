---
title: "eth0 failure after upgrade from Feisty to Gutsy"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by gertvs on 2007-10-31
I just upgraded from Feisty to Gutsy using the normal procedure (Update Manager).
After boot I have network access most of the time, but after a while networking stops working.
The key problem seems to be that the eth0 interface drops packets once it fails.

ifconfig lists eth0 as follows while networking works:

eth0      Link encap:Ethernet  HWaddr 00:13:8F:D1:74:B0  
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fed1:74b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1176 (1.1 KB)  TX bytes:3857 (3.7 KB)
          Interrupt:17 Base address:0x8000 

after networking failure:

eth0      Link encap:Ethernet  HWaddr 00:13:8F:D1:74:B0  
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fed1:74b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88 errors:0 dropped:4294967295 overruns:0 frame:0
          TX packets:98 errors:0 dropped:92 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63244 (61.7 KB)  TX bytes:12725 (12.4 KB)
          Interrupt:17 Base address:0x8000 

Note the dropped:4294967295 and dropped:92

My uneducated guess is that the driver wasn't upgraded for the new kernel.
But how can I fix this?

---

### Post by gertvs on 2007-10-31
I just booted into the 2.6.20-16-generic kernel and the problem is gone.
So this seems to be a bug in the default Gutsy kernel.

---

