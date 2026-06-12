---
title: "Dual Boot??"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by DAKz on 2006-06-17
I just downloaded the Live and I am runing a dual boot MS OS windows system, if I want can I install this to the other partition? (Not the live but I ordered the CD's) 
 I see a major problem already since Windows installs a boot managr and you select the OS you wish to run, but the boot manager is in the OS in the first partition, so how can I boot to either one, is Windows going to see this new OS?

 Next If I install this on the other partition what File system is used, and can I "see" the files on the other partition?

 Sorry to sound stupid but I tried to read through some of this on here and really didn't see an answer to the boot problem, or any mention of the file system and access to another partition formated with NTFS.:confused:

---

### Post by rcarring on 2006-06-17
If you are running a desktop computer, consider acquiring a second hard disk for Ubuntu. Then refer to aysiu's pages on the subject of dual boot.

If you have only one hard disk, please could post how your hard disk is currently partitioned so that we might better help you.

---

### Post by bikeboy on 2006-06-17
Regarding windows recognising the other OS, linux will install the grub bootloader and you will be able to select windows from that when you boot up.

Writing to NTFS is not that mature yet but in Ubuntu it's pretty easy to mount your NTFS partition and read files from it safely.

---

