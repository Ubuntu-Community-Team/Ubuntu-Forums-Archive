---
title: "RAID issus"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by pavlizz on 2008-05-11
Hello There,

How can I install ubuntu on multiple raid arrays

I have create 3 RAID ARRAYS

1) RAID 1(+extra partition) 100MB for /boot Directory
2) RAID 5 498 GB for / Directory
3) RAID 5 2GB for swap 

The installation continues normally and ands
after rebooting the system felled to boot and it ask for cd

How can i run ubuntu live cd for ubuntu server cd ?

---

### Post by Pumalite on 2008-05-11
Post yor specs. Post:
sudo fdisk -l

---

### Post by pavlizz on 2008-05-11
Device    Boot	Start  End   Blocks   Id System
/dev/hda1	1      60667 48737646 fd linux raid autodetect 
/dev/hda2	66068  60789 979965   fd linux raid autodetect
/dev/hda3  *	660790 60801 96390    fd linux raid autodetect

Device    Boot	Start  End   Blocks   Id System
/dev/hdb1	1      60667 48737646 fd linux raid autodetect 
/dev/hdb2	66068  60789 979965   fd linux raid autodetect
/dev/hdb3  	660790 60801 96390    fd linux raid autodetect

Device    Boot	Start  End   Blocks   Id System
/dev/hdc1	1      60667 48737646 fd linux raid autodetect 
/dev/hdc2	66068  60789 979965   fd linux raid autodetect
/dev/hdc3  *	660790 60801 96390    fd linux raid autodetect

---

### Post by Pumalite on 2008-05-11
What about your specs?

---

### Post by pavlizz on 2008-05-11
what do you mean ?

I have 3 WD sata Disks 500GB each
My pc its p4 2.8 2*515 MB ram

---

### Post by Pumalite on 2008-05-11
Graphics?

---

### Post by pavlizz on 2008-05-11
it's onboard I have a FOXCON Motherboard 

I don't need graphics I'm trying to install ubuntu server 8.04

---

