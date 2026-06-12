---
title: "No Wireless Network with kernel 2.6.32-17.26"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mapuo on 2010-03-24
Hi,
there is a problem with my wireless network with the latest kernel update.
I can connect to the network but there is no traffic after the connection.
In the dmesg there are these lines:
```

[   13.862198] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   13.878590] iwlagn 0000:03:00.0: loaded firmware version 228.61.2.24

```
My wireless adapter is Intel 4965 AGN.
I booted with the previous kernel to use internet.

---

### Post by mike984 on 2010-03-26
There is a bug opened on it.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545708](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545708)

---

### Post by RedSingularity on 2010-03-26
Just curious, what is your ifconfig output?

---

### Post by mapuo on 2010-03-26
> **RedSingularity said:**
> Just curious, what is your ifconfig output?

I'll post it later when I get back at home.
```

mapuo@mapuo-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1a:6b:38:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:58:xx:xx  
          inet addr:192.168.1.126  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fe58:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48591 (48.5 KB)  TX bytes:16176 (16.1 KB)

```

---

