---
title: "modprobe.conf"
date: 2004-12-18
forum: Installation &amp; Upgrades
---

### Post by Owen on 2004-12-18
hi,
my motherboard is 8RDA3(nForce2 chipset, two network interface eth0, eth1), it freezes when i startx without disable MAC Lan(nvidia) in the BIOS, if i disable this item in the BIOS, the ubuntu will be OK. so i want to install NFORCE2 driver, after i installed nFORCE2 driver, according to the nVidia installation document, i should edit the modprobe.conf, but i can't find this file, why? what should i do?
thanks.

Owen

---

### Post by wallijonn on 2004-12-22
modprobe.d is in /etc but the modprobe program is in /sbin. 

I would think that you would have to work with /etc/modules and /etc/modules.conf

---

