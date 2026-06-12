---
title: "Grub issue after using boot-repair"
date: 2021-05-06
forum: Installation &amp; Upgrades
---

### Post by teomistre on 2021-05-06
Hello,

I was trying to remove windows using OS Uninstaller [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller) 
It got stuck and my grub is now broken

I tried using boot-repair but it doesn't work, here is the pastbin report : [URL="http://paste.ubuntu.com/p/zxNrHtVtvy/"]http://paste.ubuntu.com/p/zxNrHtVtvy/


[/URL]Any help would be greatly appreciated

---

### Post by yancek on 2021-05-06
More likely the problem is related to using OS-uninstaller. Lines 64-66 of boot repair indicate 1 OS detected and that is windows 8 or 10.  Lines 44-50 show an ext4 partition but none of the files usually shown there including the grub files.  Also under Drive partition info it shows no OS for partition 5, no fstab for partition 5.  I've never used this software so don't know what happened but it appears partition 5 (Ubuntu) was uninstalled.  The simpler solution if you wanted to use the windows partition for Ubuntu would have been to simply format it with a Linux filesysem.

---

