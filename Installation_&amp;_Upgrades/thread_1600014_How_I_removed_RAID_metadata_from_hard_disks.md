---
title: "How I removed RAID metadata from hard disks"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by tonywhelan on 2010-10-18
I had a couple of IDE hard disks that had previously been set up as a RAID1 array.

I wanted to re-format and use them as separate independent hard disks but Ubuntu reported that they were part of a RAID array.
 
This is how I removed that RAID metadata from the drives.

With both drives connected I booted up Ubuntu 10.10 Live CD. 

I checked the device names via System, Administration, Disk Utility - they were listed as /dev/sda and /dev/sdb

I also noted that there was an extra device with name of /dev/md-0 which was the RAID array.

I went into Applications, Accessories, Terminal and issued the following:
```
sudo dmraid -E -r /dev/sda
```
(was asked to confirm erasure of the raid metadata)
then 
```
sudo dmraid -E -r /dev/sdb 
```
(was again asked to confirm erasure of the raid metadata)

Then I rebooted the PC, and checked the device names via System, Administration, Disk Utility - no more /dev/md-0 and the two drives no longer showed as part of a RAID array.

---

### Post by psusi on 2010-10-18
dmraid is for dealing with bios fake raids.  You appear to be using Linux software raid, so you need to use mdadm.  IIRC, it is sudo mdadm --zero-superblock /dev/sda

---

### Post by annoyingrob on 2010-10-18
I just zero'd the whole drive :)

---

