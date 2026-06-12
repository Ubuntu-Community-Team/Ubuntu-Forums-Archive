---
title: "Problems with network after upgrade"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by GoldWing on 2011-10-17
Hi,


I did an upgrade to 11.10.
The system is complaining about the network when starting up, it gets a timeout, I don't know why.
Also when I login, the network icon says that there is no network.
However, my network seems to be fine. I can ssh to my machine and everything in firefox is working fine.
Is this a bug?
This is my interfaces file:


[COLOR="DarkOrange"]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 192.168.10.7
	netmask 255.255.255.0
	network 192.168.10.0
	broadcast 192.168.10.255
	gateway 192.168.10.1
[/COLOR]

---

