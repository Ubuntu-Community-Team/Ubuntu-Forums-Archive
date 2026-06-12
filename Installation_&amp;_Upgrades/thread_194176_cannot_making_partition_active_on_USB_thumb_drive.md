---
title: "cannot making partition active on USB thumb drive"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by cotcot on 2006-06-11
I am trying to have dapper on a USB thumb drive with the boot files (ldlinux.sys, vmlinuz, initrd etc)  on /dev/sde1 and casper-rw on /dev/sde2.
The partition /dev/sde1 should be active. Therefore i used fdisk :
 'sudo fdisk /dev/sde' ; 'p' to view the partition table ; 'a' and then '1' to set partition 1 active ; 'p' to check the result and it was shown active (*) ; 'w' to save the new partition table. This gives error 16 : device is busy although i have umounted the partitions before.
My USB thumb drive is a Peak 1 GB bought a couple of weeks ago.
Any ideas ?

EDIT 
With gparted the /dev/sde1 is tagged as 'boot'. And the pen drive tries to boot. But according to fdisk it is not active . Strange.

---

