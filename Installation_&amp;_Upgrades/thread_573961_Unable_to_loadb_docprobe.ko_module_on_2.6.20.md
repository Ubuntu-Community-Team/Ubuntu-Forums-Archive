---
title: "Unable to loadb docprobe.ko module on 2.6.20"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by kandhala on 2007-10-12
Hi all,
I Upgraged my kernel 2.6.20 and configured MTD Options and Doc Drivers to load as Modules using make menu config on ubuntu 6 server version

I am able to boot new version of kernel without any problem but through
modprobe i am able to load all the modules except docprobe.ko module
I am getting the resource(docprobe.ko in /drivers/mtd/devices) is not available but module docprobe.ko is existing in the above said tree.

depmod -a
modprobe -a doc2000 nftl mthchat mtdblock is ok

modprobe -a docprobe.ko is giving the following problem

kernel/drivers/mtd/devices/docprobe.ko': >> Resource temporarily unavailable (-1): Resource temporarily ...

I try to open the following link of MTD it is not working presently
[http://lists.infradead.org/pipermail...ch/012179.html](http://lists.infradead.org/pipermail...ch/012179.html)

I request some one to please guide me to solve this issue

thanks
Srinivas::(

---

