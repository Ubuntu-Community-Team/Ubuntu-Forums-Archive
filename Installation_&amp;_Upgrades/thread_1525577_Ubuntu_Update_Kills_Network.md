---
title: "Ubuntu Update Kills Network"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by eculver on 2010-07-06
Just installed a bunch of updates and upon rebooting, my network interface won't talk to the network. When I try to manually start the interface:

```

sudo /sbin/ifup eth0
Ignoring unknown interface eth0=eth0

```

It's as if the interface isn't found, but is visible via ifconfig -a. 

I've tried a different network card as well as different routers and bypassing routers completely. It's simply as if the network isn't being configured properly due to a hardware issue, but dmesg indicates that the interface is detected and working, but without link. Anyone seen this lately?

Thanks in advance

---

