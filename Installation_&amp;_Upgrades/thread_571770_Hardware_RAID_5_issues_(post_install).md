---
title: "Hardware RAID 5 issues (post install)"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by ryushe on 2007-10-09
Hi there,

Installed Ubuntu 7.04 Alternate on a machine destined to become an inhouse test server. Issue I'm having at current is that after going through a clean installation, after the first reboot the default boot option quits on me stating what I added below. Rescue mode (single user mode) does allow me to boot up to a certain point, but hangs after a while and drops me into busybox shell. The mssage I get before it drops me into busybox is
```
Unknown partition table
sr 0:0:0:0: Attached scsi generic sg0 type 5

ALERT! /dev/disk/by-uuid/<long string> does not exist.
```
the sr line seems to be the cd-rom drive it's finding. Looking at the modules list in busybox shows no RAID modules that I can see. The /dev/disk/by-uuid/ path does not exist indeed. Booting from the cd again and chrooting into the fresh install works fine (and the disk is indeed sda1 there). The RAID card is an Adaptec 2110S, with 3 18GB 10.000 RPM SCSI disks attached to it in a RAID5 config. The installer correctly only saw the RAID5 as one single disk and has (from what I can tell) identified it as /dev/sda.
Now what I'm thinking based on the messages I'm getting back when booting default option from grub, is that for some reason the module/drivers are not loaded in time before trying to access the filesystem. What's also bugging me is that the messages mention a hda, when the drive should be /dev/sda.

Any help or suggestions are more than welcome at this point.

```
dpti: adpt_config_hba: pci request region failed
Could not Init an I2O RAID device
Will not try to detect others
Buffer I/O error on i2o/hda, logical block 0
ldm_validate_partition_table(): Disk read failed
```

---

