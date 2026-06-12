---
title: "dual boot questions - new at this!"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by i9i on 2011-06-14
I purchased a new Dell laptop.
I plan to dual boot the 64 bit Windows 7 and 32 bit Ubuntu.
I assume this will not create problems; is this correct?
Also...I noticed that the Ubuntu download file includes the word "desktop" in the filename.
I assume that the word is used as a generic term to include laptops.
Finally, is there a good resource you can recommend as a guide to installing a dual boot?
Thank you for you ideas.

---

### Post by Quackers on 2011-06-14
Welcome to UF :-)
64 bit Windows 7 and 32 bit Ubuntu will be fine.
I have desktop versions on my laptop - no problem.
Here's a good starting point for you
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

But there is something you need to check first! 
Many OEM setups with Windows 7 use all 4 primary partitions as standard. This is the maximum number available on any MBR partitioned drive.
If you just go ahead and create another partition of any kind with 4 primary partitions already being used you will cause severe problems!
Please go to Windows Disk Management utility and view what that screen says about your current partition structure.
If you are unsure please post a screenshot here.

---

