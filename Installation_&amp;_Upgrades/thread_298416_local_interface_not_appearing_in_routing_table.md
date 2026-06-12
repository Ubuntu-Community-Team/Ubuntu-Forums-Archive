---
title: "local interface not appearing in routing table"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by greghives on 2006-11-12
Hi,

Following installation of Ubuntu I notice that the lo interface does not show up when displaying routes using "route".

a.b.c.d   *         255.255.255.255 UH    0      0        0 eth1
default   a.b.c.d   0.0.0.0         UG    0      0        0 eth0

Obviously it can be added manually using,
 
route add -net 127.0.0.0 netmask 255.0.0.0 dev lo

Does anyone know why it's missing, and whether this matters. (e.g. without this route is there a possibility of local network traffic being router over the internet ?)

Thanks,
Greg

---

