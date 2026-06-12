---
title: "Partitioning problem &quot;No root file system defined&quot;"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by bumpkin on 2008-09-11
--- Problem was caused by USB-SATA race condition.   
--- Configured SATA drive as RAID in bios. Boots now.
--- See:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702)

Installed 6.10 several months ago. Booted up yesterday and only got the splash screen and an error "failed to set xfermode err_mask=0x4"  Nothing I did would get the machine to boot. 

Next used a Slackware disk and transferred my data to a thumbdrive. Slack had no problem seeing the disk.

What I want to do now is reinstall the system but preferably without reformatting the hard drive.  When I do the install from the CD in text mode I get the following error.

"No Root file system is defined"

Here is the partition table as listed in the install

LMV VG fbdb, LV root - 76.6 GB Linux-device-mapper
     #1 76.6 GB ext3
LVM VG fbdb, LV Swap_1 - 3.1 GB Linus-device-mapper
     #1 3.16GB F Swap  Swap
SCSI (0,0,0) (sda) - 80.0 GB ATA STJ80815AJ
     #1 Primary 255.0 MB B K ext3 /media/sda1
     #5 Logical 79.7 GB    K lvm

When I select "Finish  partitioning and write changes to disk"
I get the "No root file system is defined"

I would prefer to not wipe the entire disk. 

Any suggestions on how to preserve the data and system files?

---

### Post by mikewhatever on 2008-09-11
As it says, you need to specify the root partition, in other words, the system partition must be mounted as /, and I rather doubt there is a way to avoid formatting it.

---

