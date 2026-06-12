---
title: "networkcard not working dge-528t"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by Marvin on 2006-06-06
After upgrading from breezy to dapper drake my network card is no longer
working.

it works with the breezy kernel 2.6.12-10
but won't work with the dapper 2.6.15-23

The network card is a d-link dge-528t apparently it should be using the r8169
driver which seems to be loaded. but all i get after trying to get eth0 up is:

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device

---

### Post by Marvin on 2006-06-07
Aparently eth0 was now configured as eth1 which seems to be
something other people have noticed as well.
Could be more of a problem if people have firewall scripts and/or
multiple network cards. But as this is not an issue for me im using 
it as eth1 now.

---

### Post by mapkyca on 2008-03-15
Hi, I'm having the same trouble and am at my wits end!

The card is being detected as an r8169, and modprobing that manually produces some text saying that it installs as eth0, however when you later try and do anything with that interface it says that the device is unavailable.

Did you ever solve this problem?

M

---

### Post by Pumalite on 2008-03-15
Maybe you'll find this useful:
[http://www.linuxquestions.org/questions/linux-hardware-18/ethernet-card-dge-528t-and-kernel-2.6-350564/](http://www.linuxquestions.org/questions/linux-hardware-18/ethernet-card-dge-528t-and-kernel-2.6-350564/)

---

