---
title: "while stalling ubuntu it shows FREEDOS OS alongside rather than windows 7"
date: 2016-07-22
forum: Installation &amp; Upgrades
---

### Post by spandya32 on 2016-07-22
Okay so I have a lenovo G50 80 laptop which came with a freeDOS so i installed windows 7 in lagacy support and it was not an activated version.I want to install ubuntu and keep windows 7 for playing games.i saw some tutoriols on how to do that and it was straight forward but as the option came on how you want to install ubuntu(the 3 options).the first options says :install ubuntu alongside freeDOS.

i checked the "something else" option it is showing 2 partitions 1st was FAT and it was of 1 gb and another was 900 above gb of NTFS

now i know nothing about drives and parttions so i'd be glad if you suggest the solution step by step.
 i am installing ubuntu 16.04 LTS from a bootable USB.

---

### Post by grahammechanical on 2016-07-22
You installed Windows 7 in legacy mode. Are you now installing Ubuntu in EFI mode? With UEFI boot systems all operating systems must be installed in the same mode.

Regards.

---

### Post by spandya32 on 2016-07-22
no i am installing ubuntu also in legacy mode

---

### Post by yancek on 2016-07-22
Do you have any unallocated space on the drive? You can't install Ubuntu on a FAT32 or ntfs filesystem.  You can shrink the windows partition to a reasonable size from windows Disk Management and leave as much unallocated space as you want for Ubuntu.

What does "it was not an activated version" mean in reference to windows 7?

---

### Post by spandya32 on 2016-07-25
ah it means i did not make a purchase of windows 7 and it has a watermark "activate windows 7".and about shrinking windows partition ..how do i do it? i dont have unllocated space.tell me how to make one.

---

