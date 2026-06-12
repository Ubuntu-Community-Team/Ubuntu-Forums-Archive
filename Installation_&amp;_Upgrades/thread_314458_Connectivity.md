---
title: "Connectivity"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by comexdl on 2006-12-07
have installed 6.06 on pc with XP. I have no problem
connecting to the net when in XP but I have no connection
when I boot up my Ubuntu system.. suggestions? I'm guessing
that I am overlooking something obvious ..

---

### Post by endersshadow on 2006-12-07
Need some more info.  Are you trying to connect via ethernet, dial-up, wireless, or DSL?

After that, if you could post the result of this command, that'd be helpful:

```
ifconfig
```

---

### Post by averagejoe84 on 2006-12-07
What do you get if you open up a terminal and type ifconfig?

---

### Post by comexdl on 2006-12-07
> **endersshadow said:**
> Need some more info.  Are you trying to connect via ethernet, dial-up, wireless, or DSL?

After that, if you could post the result of this command, that'd be helpful:

```
ifconfig
```
ethernet

eth0   Link encap: Ethernet
inet6 addr:
up broadcast running multicast mtu:1500 metric:1
rx packets:5 errors:0 dropped: 0 overruns:0 rame: 0
tx packets:0 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisions: 0 txqueuelen: 1000
rx bytes: 2433 (2.3 KiB) tx bytes: 0 (0.0 b)
interrupt: 217 Base address: 0x2000

lo  link encap: local loopback
inet addr: 127.0.0.1 mask: 255.0.0.0
inet6 addr: ::1/128 Scope: Host
up loopback running mtu:16436 metric:1
rx packets: 5 errors: 0 dropped: 0 overruns: 0 frame: 0
tx packets: 5 errors: 0 dopped: 0 overruns: 0 carrier: 0
collisions: 0 txqueuelen: 0
rx bytes: 272 (272.0 b) tx bytes: 272 (272.0 b)

hope this gives you a clue ... many thanks for the help ..

---

### Post by comexdl on 2006-12-07
> **averagejoe84 said:**
> What do you get if you open up a terminal and type ifconfig?

ethernet

eth0 Link encap: Ethernet
inet6 addr:
up broadcast running multicast mtu:1500 metric:1
rx packets:5 errors:0 dropped: 0 overruns:0 rame: 0
tx packets:0 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisions: 0 txqueuelen: 1000
rx bytes: 2433 (2.3 KiB) tx bytes: 0 (0.0 b)
interrupt: 217 Base address: 0x2000

lo link encap: local loopback
inet addr: 127.0.0.1 mask: 255.0.0.0
inet6 addr: ::1/128 Scope: Host
up loopback running mtu:16436 metric:1
rx packets: 5 errors: 0 dropped: 0 overruns: 0 frame: 0
tx packets: 5 errors: 0 dopped: 0 overruns: 0 carrier: 0
collisions: 0 txqueuelen: 0
rx bytes: 272 (272.0 b) tx bytes: 272 (272.0 b)

hope this gives you a clue ... many thanks for the help ..

---

### Post by comexdl on 2006-12-07
> **endersshadow said:**
> Need some more info.  Are you trying to connect via ethernet, dial-up, wireless, or DSL?

After that, if you could post the result of this command, that'd be helpful:

```
ifconfig
```

ethernet

eth0 Link encap: Ethernet
inet6 addr:
up broadcast running multicast mtu:1500 metric:1
rx packets:5 errors:0 dropped: 0 overruns:0 rame: 0
tx packets:0 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisions: 0 txqueuelen: 1000
rx bytes: 2433 (2.3 KiB) tx bytes: 0 (0.0 b)
interrupt: 217 Base address: 0x2000

lo link encap: local loopback
inet addr: 127.0.0.1 mask: 255.0.0.0
inet6 addr: ::1/128 Scope: Host
up loopback running mtu:16436 metric:1
rx packets: 5 errors: 0 dropped: 0 overruns: 0 frame: 0
tx packets: 5 errors: 0 dopped: 0 overruns: 0 carrier: 0
collisions: 0 txqueuelen: 0
rx bytes: 272 (272.0 b) tx bytes: 272 (272.0 b)

hope this gives you a clue ... many thanks for the help ..

---

### Post by endersshadow on 2006-12-07
Try this:

```
sudo ifdown eth0
sudo ifup eth0
sudo dhclient
```

Post back with results. Thanks!

---

### Post by comexdl on 2006-12-09
> **endersshadow said:**
> Try this:

```
sudo ifdown eth0
sudo ifup eth0
sudo dhclient
```

Post back with results. Thanks!

results:

no dhcp offers received
no working leases in persistent database - sleeping

also - was using port 67

---

