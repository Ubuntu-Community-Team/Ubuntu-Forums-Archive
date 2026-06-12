---
title: "Post-upgrade eth0 startup unstable"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by Paqman on 2007-05-03
I've recently upgraded from Dapper to Edgy. Everything went swimmingly except that now eth0 is not starting up reliably. More often that not I boot up and have no ethernet. I've been getting around it by going to the networking control panel and disabling/re-enabling the ethernet, after which it works fine.

Ifconfig at startup (ie: no ethernet)
```

eth0      Link encap:Ethernet  HWaddr 00:01:6C:ED:1B:20  
          inet6 addr: fe80::201:6cff:feed:1b20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8038 (7.8 KiB)  TX bytes:810 (810.0 b)
          Interrupt:193

```

Ifconfig after restarting ethernet
```

eth0      Link encap:Ethernet  HWaddr 00:01:6C:ED:1B:20  
          *inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0*
          inet6 addr: fe80::201:6cff:feed:1b20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15880 (15.5 KiB)  TX bytes:5883 (5.7 KiB)
          Interrupt:193 

```

So why isn't this device starting reliably?

---

### Post by Paqman on 2007-05-04
Anybody mind if I bump this?

---

