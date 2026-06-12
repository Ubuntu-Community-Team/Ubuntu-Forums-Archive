---
title: "etc/init.d/mountnfs missing in gutsy"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by jongt1 on 2008-01-14
I've just installed Ubuntu (latest download 20001012) on a new PC
based on Intel X38 chipset, Core 2 duo 6850, two SATA discs and 4gb
1066 DDR3 memory, and using the ethernet provided by the X38 chipset.
When I try to set up the use of nfs, it doesn't remount remote
filesystems during reboot, unlike every other Debian based system I've
setup. It appears that this is because statd hasn't been started at
the appropriate time, which I think is because there is no /etc/init.d/
mountnfs.sh available. According to the debian package list, it should
be provided by initscripts. But ubuntu package search seems to suggest
that there is no mountnfs.sh at all. That being the case, how is /etc/
init.d/mountnfs supposed to get called?

---

### Post by Craigus on 2008-01-14
Is nfs-common even installed ?

I've found with Gutsy and Mint 4.0 that the default installation doesn't include nfs-common and I have to install it.

---

