---
title: "Ubuntu 7.04: Network doesn't work"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by silent911 on 2007-05-18
I've just installed ubuntu 7.04. Whene I connect my laptop to the network DHCP doesn't work: It obtains only the IP address, but not the subnet mask and the gateway. If I put all manually I cannot use firefox or ping for example google... I don't understant what problem can be...

---

### Post by silent911 on 2007-05-18
I put manually address, netmask, gateway and dns but if i do sudo ifconfig i obtain

eth0
          inet6


etho: avah
          inet addr:169.254.4.166   mask 255.255.0.0

when the address i wrote was 192.168.x.x

---

### Post by silent911 on 2007-05-19
I tried with the live...but even if the parameters of the network are correct...it doesn't work...

---

### Post by jerrylamos on 2007-05-19
Can you try Applications, Accessories, Terminal
sudo dhclient

What do you get from:
ifconfig

Is your internet connection wired or wireless?

Cheers, Jerry

---

