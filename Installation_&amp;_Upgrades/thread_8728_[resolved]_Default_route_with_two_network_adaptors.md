---
title: "[resolved] Default route with two network adaptors"
date: 2004-12-20
forum: Installation &amp; Upgrades
---

### Post by richpri on 2004-12-20
I have two network [ethernet] adaptors.
The first [eth0] is conected to my DSL router.
The second [eth1], which was added after the install is my internal network.
It is using [192.168.168.0/24 subnet.

The route command returns:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.248 U     0      0        0 eth0
192.168.168.0   *               255.255.255.0   U     0      0        0 eth1
default         192.168.168.1   0.0.0.0         UG    0      0        0 eth1
default         w185.z208176194 0.0.0.0         UG    0      0        0 eth0


I think this means that the default route will be to eth1
Is this correct?  
If so then how can I get this changed so my default route is to eth0?

---

### Post by richpri on 2004-12-21
I found the solution. 

I removed the default router [gateway] address from the config for eth1.
This causes the default route to eth1 to go away.

Because eth1 is my internal network, it doesn't need a default route!

---

