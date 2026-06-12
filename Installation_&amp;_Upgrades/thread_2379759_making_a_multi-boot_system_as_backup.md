---
title: "making a multi-boot system as backup"
date: 2017-12-09
forum: Installation &amp; Upgrades
---

### Post by lseg on 2017-12-09
Hi guys,

I have a system with 3 HDDs, All 3 have a 100GB partition with the OS, The rest ( 1.5 TB each) was added to a soft raid RAID 5 and mounted to /home. The 100GB partition were also softraid, but RAID1. I thought that was a good idea several years ago. Actually it isn't. My system crashed and I can not boot the OS again. The fact that is RAID 1, doesnt help, they all three have the same issue... I would like to change this for the future, and reinstall the OS on 1 of the three 100GB partitions e.g. sdc1, so not using softraid for the OS anymore, still keeping the RAID5 for the /home though. 

Since I would still have the 100GB partition on sda and sdb I would like to make them a backup for my OS partition on sdc. I would like to copy this sdc1, with the installed OS, to the available sda1 and sdb1. 
If my system crashes again, and I can not boot from sdc1, I would like to boot from an older copy which is on sda1 or sdb1. Is this possible?
Can I just do an rsync or a copy from a running OS partition to another partition (which I would then mount).
Can I just tell to GRUB: now boot from sdb1 instead of from sdc1.

I'm not so sure what should be changed to the copied drive (sda and sdb) to make it bootable, e.g. should I do something extra to make each disc bootable (MBR, ... not sure how this works). I suspect I also have to change something to fstab for each disk (fstab on each disk will need the UID from that disk and not from the original sdc). What else should I do?

Kind regards,

Luc

---

### Post by oldfred on 2017-12-09
While you may be able to copy system, you have to reinstall grub, change all UUID settings in fstab and perhaps some other settings.

It really is easier just to do another install, then everything matches. I have multiple installs on many drives and even full installs on my larger flash drives.
I prefer to have a full install on every drive that is bootable from that drive. I normally use 25GB for / (root) and have all data in a shared /mnt/data partition. I do not use RAID, so do not know what additional complications that may add.

       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive.

---

