---
title: "Ubuntu and Windows xp dual boot,problem!"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by mookieit on 2007-05-22
hello,

I need to say that since i have been using computers i have beed only working with windows.

I want to install windows xp,and ubuntu on my pc.

A good method that i found out is

-make a primary active partition(10MB,fat16)
-install win xp on a logical partition
-install linux on a logical partition(instal lilo in the partition where ubuntu is installed)
-use bootpart.exe and copy the boot partition of the linux partition(example : bootlnx.bin)
-copy bootlnx.bin to the primary active partition
-edit boot.ini and add the line "c\bootlnx.bin="ubuntu linux"

This dosnt work,and i do not know why.

Before i did this method,i just installed ubuntu,and grub to the MBR and i got an error 17 from grub.And i had to install my OS from the begining.

If anyone knows why my method doesnt work pleas tell me or if they know another good method tell me also.All i want is to have windows and linux on my pc,but i want them to be indepentent so if i format windows or linux i dont have a problem.

please help me!

btw i am installing ubuntu 7.04 alternate cd.

---

### Post by jamsh on 2007-05-22
Try Wubi [here]("http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html")

---

### Post by mookieit on 2007-05-22
thank you ver very much,it worked like a treat!!!

---

