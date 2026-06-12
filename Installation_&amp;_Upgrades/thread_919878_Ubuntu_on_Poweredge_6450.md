---
title: "Ubuntu on Poweredge 6450"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by agentfubu on 2008-09-14
Hey, 

Thanks for reading this. I want to know if there's something special I need to install Ubuntu on this system:

2 PIII Xeons (32bit)
8gb of Ram
Perc-2 SCSI controller with 4 drives
1 raid array. 

I've tried the unbuntu desktop live disk to no avail, it just stop at the busybox initramfs prompt. 

Thanks!

---

### Post by Krokido on 2009-04-29
Hi,

I have been working with Ubuntu and poweredge 6450 servers for some time now. Still I am of the newby level :S. I have found out that the IDE slimline DVD rom players give problems with installing. When scanning for the cd-rom player it can not find it (you'll see it scanning through all the 'pools', looks like folders that go from A to Z. and at 99% it says it can't find the cd-rom. (whatever the 'pools' are, forgive the newby).

I have been able to install Ubuntu desktop version 6.06 LTS through the live CD by using the IDE slimline CD Rom player.

Previously, before installing PERC 3 RAID controllers and upgrading from 4 GB to 8 GB of memory, I have been able to install a 6.06 LTS server version on the servers. Now, after the hardware upgrade, I've had lots of trouble.

On the internet and different forums I found two things both listed here;
[http://ubuntuforums.org/archive/index.php/t-477890.html](http://ubuntuforums.org/archive/index.php/t-477890.html)

good luck, I will keep on having fun with Ubuntu on the poweredge 6450.

My configs:

4x700 MHz PIII Xeon
16x512MB 133 MHz ECC REG SDram
4x18 or 4x32 Gb Harddisk on DELL PERC 3 raid with 128 MB
CD-rom drive

---

### Post by psypher on 2009-08-06
hi, i'm still having this problem. tried what the link suggested, in fact my raid controller was already in MASS STORAGE mode. I had dapper installed on this box before. Can't remember if I had this issue. Also tried noapic in the boot options but still stops and initramfs busybox. Any other suggestions?

thanks

---

