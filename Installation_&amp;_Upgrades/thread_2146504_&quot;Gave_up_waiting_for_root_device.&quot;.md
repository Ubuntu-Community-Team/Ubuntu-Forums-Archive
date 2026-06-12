---
title: "&quot;Gave up waiting for root device.&quot;"
date: 2013-05-18
forum: Installation &amp; Upgrades
---

### Post by moonguide on 2013-05-18
I installed 12.04 on a Dell Dimension 2400 that has a PCI card driving a SATA hard drive. When I boot I get the following error message:

Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
	- Check rootdelay= (did the system wait long enough?)
	- Check root= (did the system wait for the  right device?)
 - Missing modules (cat /proc/modules; ls /dev)
Alert!  /dev/disk/by-uuid/82df63b6-8b97-4287-ae1b-db29565f5370 does not exist.
Dropping to a shell!

BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4.1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) 

I'm assuming that the problem is GRUB is not finding the SATA device (although that is just a guess on my part). What do I have to do to get this box to boot?

Thanks.

---

