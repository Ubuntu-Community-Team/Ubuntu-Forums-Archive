---
title: "Hal.dll missing (windoze no boot) RESOLVED"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by fokuslee on 2006-12-29
I just recently installed Edgy on top of winXP.  When booting winXP from grub I receive the error of Hal.dll missing.  
This is not caused by a corrupt dll, don't use win recovery to correct this.  When u are using the partiton creater correctly Ubuntu will NEVER touch winXP partition.  
The problem is caused by windows boot.ini not couping with the extra OS 
In short you must edit the boot.ini file for windows.  

here are two guides that will save your windoze.  

[http://www.ubuntuforums.org/showthread.php?t=78509&highlight=hal.dll+missing](http://www.ubuntuforums.org/showthread.php?t=78509&highlight=hal.dll+missing)
[http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=395264](http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=395264)

ps you should use 
lsparts (only for 5.10?) 
fdisk -l 
to determine the correct mount and also where boot.in reside (for me boot.ini was not with winXP, it was in another NTFS partition i created earlier)
to gain root use sudo -i

go into synaptic enable all repos then ntfstools should be avaible for install via synaptic meaning no need to compile.  
I am hoping that someone with good linux knowledge can write a complete guide to solve this problem.  I am a linux nub so this is as much as i can help.  Still if you read the guide carefully you should beable to solve the problem.  Good Luck.

---

### Post by Sef on 2006-12-29
Thank you for providing a solution to that problem.

---

