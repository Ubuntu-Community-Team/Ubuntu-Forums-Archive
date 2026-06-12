---
title: "Input/output error during read on /dev/sda"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by VyomGrisham on 2011-01-31
I have an Emachines D725 series laptop with a seagate 250 GB hard drive.I have been trying to install Ubuntu Netbook 10.04 from my flash drive ( tried with CD too...no luck ).The boot order is set to detect USB first.
This is the error message I get  "**Input/output error during read on /dev/sda**" while installing Ubuntu 10.04 on my hard drive.
On clicking Retry, The installation shows 15 % completed and returns another error " **The ext4 file system creation in partition 5 of SCSI (0,0,0) (sda) failed**.
 
The Ubuntu runs perfectly from the pen drive and the disk utility which I ran from Ubuntu showed my disk as healthy ( the utility was not able to format the hard drive either... ).
 
I was able to install windows XP on the same hard drive later after formatting it.It seems there is nothing wrong with my hard drive as even running chkdsk didnt bring out anything.I am not sure if I missing out anything here...any help would be much appreciated.

---

### Post by ckantzer on 2011-02-24
I'm having this trouble too.  

I'm suspecting a bad hard drive, but how would I verify that before I return the drive?

---

### Post by srs5694 on 2011-02-24
You can use a SMART utility, such as smartctl or GSmartControl, to check the disk for errors. (Most manufacturers also have SMART utilities on their Web sites, either as Windows tools or on bootable CD-R images.)

---

