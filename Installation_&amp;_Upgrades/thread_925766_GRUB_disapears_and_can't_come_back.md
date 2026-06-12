---
title: "GRUB disapears and can't come back"
date: 2008-09-21
forum: Installation &amp; Upgrades
---

### Post by twodayslate on 2008-09-21
Three days ago I turned on my computer and I was welcomed by a black screen with the flashing _
It seems like GRUB has left me. :(
I have tried everything to get her back. I have gone through your tutorials but I have received rejection after rejection! 


I have done [sudo grub]("http://ubuntuforums.org/showthread.php?t=224351") but I can't find stage1
I have done sudo mount -t ext3 /dev/sda6 /mnt/root but I get an error
I have installed the [grub bootloader]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") but that does not work since it can't find stage1. 
I have ran the live CD and I can't see my old file system. I have two hard drive and I can't see either on the live CD. I can see partitions but no content. I have XP on one and Ubuntu 8.04 on the other. Has by HD just **** itself? Since I can't see my old file system I can't see the menulist.

---

### Post by jvin248 on 2008-09-21
Are you able to see the drives (when booting from liveCD)?  Or how about at the BIOS Post screen when the computer boots up (you may need to go into BIOS to turn off "logo" and turn on "diagnostics".  If you can't see the drives these two places then you've got a drive problem.  If you swapped HDDs then you might have a cable or jumper setting incorrect (sometimes trial and error here).

---

### Post by twodayslate on 2008-09-21
I didn't swap any cables or drive before this problem, but when I did swap the IDE cables it worked. I have no idea what the problem was but my issue with GRUB has been resolved. Thank you very much.

---

