---
title: "New ubuntu isnt going well.."
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by floyd27 on 2005-10-17
Hi..
I just re-installed ubuntu 5.10

I have an issue. Windows was installed on sata drive with 5.04.
I have another drive with only linspire on it

installed 5.10 on the partition 5.04 was on (complete re-install)

Grub sees the other drives and OS's but wont booot into either one.
And..Its telling me windows has a rieiserFS file system?? (its actually on linspire)
And Linspire has no file system? 
When in ubuntu i can see all the partitions and they are correct (not mounted yet) But I can see them..
Anyone know how to fix grub?

---

### Post by aysiu on 2005-10-17
I don't know if I can help, but someone probably can if you post the output of these two commands ```
sudo fdisk -l
``` ```
cat /boot/grub/menu.lst
``` You may also want to try 

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

