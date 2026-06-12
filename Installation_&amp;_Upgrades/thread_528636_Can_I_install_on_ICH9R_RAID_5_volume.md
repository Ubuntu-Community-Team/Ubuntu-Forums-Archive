---
title: "Can I install on ICH9R RAID 5 volume?"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by Scorpuk on 2007-08-18
5 x 500GB SATA HDD's setup as RAID 5 (1.8TB) on the ICH9R controller


Will I be able to install Ubuntu 7.04 on the single 1.8TB volume?


I am looking at the following motherboard at the moment: GA-G33-DS3R



Tnx.

---

### Post by Scorpuk on 2007-08-19
Anyone?  :(

---

### Post by Scorpuk on 2007-08-19
Sorry to bump again, but really really need an answer as I want to order the parts this week and build by the weekend.


No point in getting the stuff if it wont work :)


tnx in advance to anyone that can help me on this.

---

### Post by corpkid on 2007-08-19
I don't think you can use RAID 5 on a fakeraid controller.  I think you are limited to RAID0 or RAID1.

If you get a true hardware controller you should be good to go.  Do a search for fakeraid and RAID5 and you should be good to go.

---

### Post by Pumalite on 2007-08-19
[http://ubuntuforums.org/showthread.php?t=528060](http://ubuntuforums.org/showthread.php?t=528060)

RAID-5 Notes

While trying to install dmraid for a RAID-5 Nvidia setup received a error 139 forced exit and upon further investigation in the TODO doc in /usr/share/doc/dmraid found that dmraid doesn't support raid modes above 1 yet. Here's the exact wording from the TODO,"higher RAID levels above 1; main restriction to support these is the need for device-mapper targets which map RAID3,4,5."

EDIT: Further research has lead me to dmraid 1.0.0.rc10, which in it's changelog notes RAID-5 support for nvidia. Current Ubuntu version is 1.0.0.rc9 which explains the lack of RAID-5 support. Will update with more info on how well it works.

/!\ The kernel device mapper (which dmraid depends on) does not yet support RAID-5. There are some early development patches available, so they might get merged into Linus's kernel in time for Edgy, but I'd say it's not all that likely.

---

### Post by Scorpuk on 2007-08-20
Thank you for your replies.

I think I was blinkered looking at the motherboard for RAID whereas I should be able to setup my HDD's with a software RAID 5 solution.


Am I correct in thinking that from the 7.04 live CD I should be able to setup my computer in the following way without an internet connection?


1. Install 5 x 500GB (identical)SATA HDD's.

2. Boot to Live CD (7.04) (Using Pioneer BDC-202 Blu-Ray Reader 12X DVD1RWDL/RAM SATA Black - OEM [should work as an ordinary CD-ROM for installation purposes]) 

3. Setup software RAID 5 on the above drives. 

4. Install OS on new RAID 5 partition.


using a Q6600 processor there should not be much of an impact overall to the system.


Basically looking at the following for the setup:

Compucase Black S411 4U Rackmount Chassis - No PSU
Gigabyte S775 Intel G33 ATX DDRII GLAN 8CH Audio VGA
Intel Core 2 Quad Q6600 (2.4GHz 1066MHz) Socket 775 L2 8MB Cache (2x4MB (4MB per core pair)) Retail Boxed Processor
6 x  Seagate ST3500630AS 500GB Hard Drive SATAII 16MB Cache 7200RPM - OEM 
Coolermaster RealPower 1000W Modular PSU - 4x 6pin and 2x 8pin PCI-E, 8x SATA
Pioneer BDC-202 Blu-Ray Reader 12X DVD1RWDL/RAM SATA Black - OEM
Corsair 2GB Kit (2x1GB) DDR2 800MHz/PC2-6400 XMS2 Dominator Memory Non-ECC Unbuffered CL4(4-4-4-12) E.P.P.DHX Technology Lifetime Warranty 


Well the PSU and Blu Ray drive will be for my new windows computer, but will be used in the interim. :)

---

