---
title: "Install Problem on Via PC2500e (gOS motherboard)"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by sdwood68 on 2007-12-04
I'm having trouble installing Kubuntu 7.10 on to the Via PC2500e mother board. This is the same one as in the walmart gOS machine. 

Install goes fine but it does not recognize the RTL8169 Ethernet controller or the USB controllers during install. So of course I get a  nice login screen and no mouse ( I only have USB mice) 

How do I go about getting it to install the r8169 and USB driver from the rescue boot from grub? It did not like 

insmod r8169

on the command line. 

Sorry for being a bit of a noob on this.

Stuart

---

### Post by sdwood68 on 2007-12-04
Found the problem, The Bios was set for fail safe and turned them off.......

---

