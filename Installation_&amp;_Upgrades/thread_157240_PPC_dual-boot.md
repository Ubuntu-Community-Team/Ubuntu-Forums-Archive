---
title: "PPC dual-boot"
date: 2006-04-08
forum: Installation &amp; Upgrades
---

### Post by penguain on 2006-04-08
is there a step by step manual for dual booting with Ubuntu and OS X with OS X already installed

---

### Post by linear on 2006-04-08
I wouldn't call it a manual, but this is my standard set of instructions:

First read these:

[https://wiki.ubuntu.com/Installation/PowerPC]("https://wiki.ubuntu.com/Installation/PowerPC")
[http://www.askdavetaylor.com/how_do_..._mac_os_x.html]("http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html")

This worked for me:

0. Read up in the PPC forums on any model specific quirks.
1. Back up OS X partition. ([Carbon Copy Cloner]("http://www.bombich.com/software/ccc.html") works well.)
2. Repartition disk. Make two partitions, leave first as free space and second for OS X. Disk Utility is destructive (another reason for the back up), or there is a howto [here]("http://ubuntuforums.org/showthread.php?t=89960") on using **parted** to resize non-destructively. Make the partition at least 5GB, but bigger is better if you really plan to use it.
3. Boot from the Ubuntu install disk. When you get to the partitioning step, tell the installer to use the largest free space. It will take care of the rest.

---

