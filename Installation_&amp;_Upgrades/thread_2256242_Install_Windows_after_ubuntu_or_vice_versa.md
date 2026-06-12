---
title: "Install Windows after ubuntu or vice versa?"
date: 2014-12-10
forum: Installation &amp; Upgrades
---

### Post by gaurav20 on 2014-12-10
Hi, 

I have a free hard drive on my laptop. (Backed up and completely wiped hard drive.) I wish to dual boot with windows 8.1 and Ubuntu. I have dvd's for both OS's. Do I install windows first and dual boot or do I install Ubuntu first and later partition the hard drive for windows 8?

---

### Post by MAFoElffen on 2014-12-10
Install Windows first, then Linux. You can size the partition in the Windows install, to leave enough unallocated for your Linux install.

You want to do it in this order for several reasons. First Winows runs best if in a partition that is close to the root of the drive, from a primary bootable partition. Linux doesn't care where it is, nor if it is a primary or logical partition.

Second, Windows assumes that it will be the only OS on a system, so if there is another bootloader on the system, it will over-write it. It's boot manager will find other Winodows OS instances, but does not look for Linux installs, and will not boot Linux. (Not politically correct?) Install Windows first, then when you install Linux.  At the end of the Linux install, install Grub2 as the boot manager. It will find your Winodws install and automatically add it to it's boot menu.

---

### Post by gaurav20 on 2014-12-11
Thanks, the installation went without any hiccups.

---

