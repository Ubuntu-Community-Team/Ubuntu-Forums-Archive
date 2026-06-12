---
title: "After upgrading to 11.10 : boot time is really longer (udev seems to hang)"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by xyomguix on 2011-10-22
Hi there,


I did upgrade from 11.04 a few days ago and the boot time on my machine is really longer (from 10s to 50s).

I did a bootchart the boot and it seems to be udev & udevadm that are taking much of the boot time.

Any idea where I should look for to reduce udev/udevadm execution time during boot ?

My kernel is 3.0.0-12-generic 

See below my bootchard

[http://img854.imageshack.us/img854/7909/yomguigama785gmtud2hone.png](http://img854.imageshack.us/img854/7909/yomguigama785gmtud2hone.png)

---

### Post by xyomguix on 2011-10-22
[LEFT]Thanks to this threads : [http://ubuntuforums.org/showthread.php?t=1749924&page=2](http://ubuntuforums.org/showthread.php?t=1749924&page=2)

I found the solution (it was ata_id which was hanging).


> 
                             in /lib/udev/rules.d/60-persistent-storage.rules

comment out rule:

# ATA/ATAPI devices (SPC-3 or later) using the "scsi" subsystem
KERNEL=="sd*[!0-9]|sr*", ENV{ID_SERIAL}!="?*", \ SUBSYSTEMS=="scsi",  ATTRS{type}=="5", ATTRS{scsi_level}"[6-9]*", \ IMPORT{program}="ata_id  --export $tempnode"


then run as root
     Code:
     update-initramfs -u 
reboot, and check your booting time                      
[/LEFT]

---

