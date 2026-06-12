---
title: "Problems with rEFIt and bootloader"
date: 2011-06-18
forum: Installation &amp; Upgrades
---

### Post by Fasopus on 2011-06-18
Hey there, I originally posted in the apple users forum with some problems installing linux as the third operating system on my mac pro. However my problem has changed quite a bit since the original post so I figured I should start a new thread. I currently have rEFIt showing 3 operating systems on boot,it shows OSx, Windows 7 and Ubuntu, booting OSx and Windows 7 works perfectly. However when I try to boot Ubuntu it boots Windows 7. I've tried updating and giving rEFIt a fresh install, as well as using the rEFIt partition table tool and nothing has solved this issue. I think the issue has something to do with where I installed the bootloader for Ubuntu.

I have 4 drives in my computer, the Ubuntu drive is the 4th drive. I installed Ubuntu to the partition /dev/sdd2 (ext3 format) and I installed the bootloader to the same location, is this correct? I noticed there is a /dev/sdd1 partition of EFI format, is that where I should have installed it? I'm also wondering if this is just an issue with 11.04, but I doubt that personally.

---

### Post by srs5694 on 2011-06-19
Please see [my response](http://ubuntuforums.org/showpost.php?p=10957471&postcount=12) in [your original thread.](http://ubuntuforums.org/showthread.php?t=1784675)

---

