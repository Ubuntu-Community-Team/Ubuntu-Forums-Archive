---
title: "Full backup of a running system"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by ndaneau on 2010-04-12
Hi,

I've an install of ubuntu with a / in raid1 (md0=sda5+sdb5). /boot is on sda1 and swap on sdb1. Grub on sda MBR.
Today sda completely died. Gparted doesn't see it anymore. Hopefully the system is still running as i didn't halt it.
I already backed up my /home on an external hdd.
I also deleted my swap partition wich is of no use (4 gb ram is enought) and wanted to make it the boot partition, but copy from actual /boot is unpossible (even if i can see the content of it).
Is there a way to restore a running system quickly? 
I also have a spare hdd to replace the dead one, but have to wait for a correct /boot and grub install before.
Is there a way to clone the system (like clonezilla do) but on a running system?

Thanks

Nico

edit : no more access to file in /boot

---

