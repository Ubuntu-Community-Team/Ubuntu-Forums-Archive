---
title: "grub 18 error"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by maddot on 2006-08-15
hi,
 I'm sorry but i'm completely new to this whole linux scene since converting to linux. After hearing alot of good stuff about ubantu i decided to try. but this post is not about my experience. If possible, please explain as simply as possible.

 I have 2 hard disks. The first hard disk holds my previous installation of winxp pro. It is also my master hdd. Ubantu is installed on my second hard disk which is slave. the whole thing is partitioned for ubantu. After completing installation, it stalls at the grub error 18. I don't understand what really is wrong so please help.

*I apologise if this is in the wrong forums too. I'm confused where should this fall unders support or the begginer forums. Mods would you please move this if so. thanks.

---

### Post by tonym on 2006-08-15
Please provide more details of your disk layout.

Also, how do you intend to dual boot,  by selection through GRUB or by changing boot drive in the BIOS?

Regards

Tony.

---

### Post by maddot on 2006-08-15
what other details do you need(or how to get the details for that matter ](*,) ). GRUB if possible.

---

### Post by zxee on 2006-08-15
Open a terminal (at the screen where you get the grub error just press the Alt+ F2 keys) and type fdisk -l then copy and paste the output to the thread.

Added: I should have also asked you to post,if you can get to the ubuntu install either from windows or a live cd, the contents of /boot/grub/menu.lst

---

