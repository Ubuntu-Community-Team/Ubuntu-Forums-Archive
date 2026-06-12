---
title: "My bootloader is gone!"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by afx on 2006-08-27
Hello everyone!
Here's the thing, I have a dual-boot setup on my laptop (Kubuntu & WinXP) and everything worked fine until I inserted the WinXP setup CD to repair(!) WinXP. As stupid as it is, it started to install Win again on its own!!! i guess it messed up my MBR so my GRUB is gone. Is there any way I can set it back cuz I can't access my Kubuntu which I use as a primary OS and I had everything set up and I don't wanna install everything from beginning! I have the 6.06 alternate cd with me (which I used to install the system as well)... Help!!!

---

### Post by moma on 2006-08-27
It is relatively easy to re-install GRUB boot loader.
This thread explains the procedure
o---> [http://ubuntuforums.org/showthread.php?p=1403833#post1403833](http://ubuntuforums.org/showthread.php?p=1403833#post1403833)
Replace  /dev/sdb with correct drive in your case.

---

### Post by RadixLecti on 2006-08-27
Not to worry.
Check this page: [http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub)

You'll probably want to install grub in the mbr, hd(0) in most cases.

---

### Post by afx on 2006-08-27
thanx peeps!
you rule (just like always...) ;-)

---

