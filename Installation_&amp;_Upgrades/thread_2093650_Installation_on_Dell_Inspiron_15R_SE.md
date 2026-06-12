---
title: "Installation on Dell Inspiron 15R SE"
date: 2012-12-11
forum: Installation &amp; Upgrades
---

### Post by AleKnaui on 2012-12-11
Hi.

I just bought a Dell Inspiron 15R Special Edition. The specs: 8GB RAM, Core i7 3rd Gen Processor and 750GB HD. A pretty neat machine which came with Windows 8, but no installation discs, other than drivers and utilities.

I read in [http://www.ubuntu.com/certification/hardware/201203-10678/](http://www.ubuntu.com/certification/hardware/201203-10678/) that it is Ubuntu Certified, so I proceded to format the whole drive and install 12.04 in it.

My Live CD is on a partition of a WD Passport. I booted from there (mounted on sdb1) but of course the installation is to be made on sda.

I chose the following configuration for the hard drive partitions:
512MB as /boot (ext2)
2GB as swap
100GB as / (ext4)
the rest (645GB) as /home (ext4)

I set "Device for boot loader installation" to sda, since there's where I am installing.

When it was done, I restarted, and it just does not find a booting device. Next, I booted again from the live CD, and went to Disk Utility to see if the partitions were done, and there they are, but it warns me the partitions are misaligned by 3072 bytes on /boot, 2560 bytes on swap, 2048 bytes on / and 1536 bytes on /home.

I am really at a loss here. Could it just be that the boot loader must be set to sdb? does it have to do with the misalignments? If so, how should I handle them? I am also reading a little about this "UEFI" thing, which I saw when I was on  the boot selector but I don't really know how it affects me. Any directions are very welcome.

Greetings!

---

### Post by rogue1987 on 2013-03-13
did you ever get this sorted out?

---

