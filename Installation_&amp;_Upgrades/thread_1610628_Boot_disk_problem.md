---
title: "Boot disk problem"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by kmach1ne on 2010-10-31
Okay, I've been trying to dual boot windows 7 and ubuntu. I want ubuntu as my primary but I can't seem to get the ubuntu disk to boot. I recently DBAN'd my hard drive so it's completely clean, (in terms of no viruses, fragmentation, etc.) I installed windows 7 32 bit just to try and burn the ubuntu disk so all my hard drive has is a fresh copy of windows 7 on it. 

I've researched the problem and I find similar problems but didn't really tell me exactly how to fix it. I can load up the disk in windows and view the demo and documentation (autorun) but won't boot to actually install it on my other partition.

Hope I made everything clear enough for someone to answer. Thanks.

---

### Post by Quackers on 2010-10-31
Welcome to UF.
Firstly, when you burned the Ubuntu disk did you select "burn image" or "burn iso". As it is a .iso file it cannot be burned normally. 
Secondly, when you installed Windows 7 did you use the whole hard drive or just a partition on that hard drive? If Windows is using the whole drive you will need to shrink the Windows 7 partition to create some free space for Ubuntu to install in. First defrag the drive, maybe even twice. Then you can go to Start and then right-click on Computer and select Manage. In the window that opens up select Disk Management. In the new window right-click on the Windows main partition and select Shrink. The new window will give details as to how much the partition can be shrunk (usually about half). Use the defaults or change to what you want then click ok.

---

