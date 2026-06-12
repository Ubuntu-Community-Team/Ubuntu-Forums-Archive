---
title: "Server stops listening on all ports"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by fjames on 2007-09-18
I have installed the LAMP server 6.06 on 3 PC's. All different hardware.  I have the same issue on all the servers. Periodically the server appears to stop listening on all ports. I can not find any malfunction. Sometimes ifconfig shows that the static IP has changed to an IP issued by DHCP. I followed the instructions to the letter when configuring for static.

/etc/network/interfaces

auto eth1
iface eth1 inet static
address 192.168.20.100
netmask 255.255.255.0
network 192.168.20.0
broadcast 192.168.20.0
gateway 192.168.20.1

I also changed the DNS (resolv.conf).

All seems perfect. Then it stops. Downing and brining eth1 backup fixes the problem.

I have searched the internet looking for a resolution. It seems that I am the only having this problem.

Any assistance would be appreciated.
Thanks

---

