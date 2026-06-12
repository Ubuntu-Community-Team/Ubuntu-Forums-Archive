---
title: "Hot Plug/swap sata"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by bricktop on 2007-11-14
Hi guys,

I searched to forum and could not find any answers to my question, please forgive me if I am double posting.

I have a server with 8 sata drives in removable hot swappable bays running on 7.04 connected to 2 sunix SATA4000 controller cards. What do i need to do to make the drives hot swappable.

Do i need to power down the drives before i remove them or is it safe to do so while the disks are powered on and unmounted?

Basically i need to know what physically needs to be done before a remove the drive without powering down the server. Theses drives contain backup data and no system data at all.

Thanks

---

### Post by fatespeaks on 2007-11-26
I think the SATA power connector is specially designed to allow hot plug operation.  That said, I still power off the drive and allow it to spin down before removing.

However, I think that software support will be your bigger issue right now.  I have the AMS 5-in-3 SATA backplane ([http://www.american-media.com/product/backplane/sata300/sata300.html](http://www.american-media.com/product/backplane/sata300/sata300.html)) and a Promise SATA300 TX4.  Ubuntu 7.10 doesn't seem to recognize a hot-plugged drive.  At least my system didn't completely lock up like it did on Debian Etch.  Linux 2.6.23 includes several patches for libata (sata drivers) ([http://kernelnewbies.org/Linux_2_6_23](http://kernelnewbies.org/Linux_2_6_23)).  Ubuntu 7.10 is on Kernel 2.6.22.

Until the SATA support stabilizes you may want to use a USB enclosure for your hot-swapping needs.  See this post for more info ([http://osdir.com/ml/linux.ubuntu.server/2006-08/msg00006.html](http://osdir.com/ml/linux.ubuntu.server/2006-08/msg00006.html)).  Though I hope someone has a better solution as I am trying to achieve the same goal.

Cheers,
Aaron

---

