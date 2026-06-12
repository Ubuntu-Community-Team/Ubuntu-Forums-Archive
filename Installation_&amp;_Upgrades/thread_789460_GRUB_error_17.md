---
title: "GRUB error 17"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by JamesBenson on 2008-05-10
I tried to install ububtu 7.04 yesterday.  I have three internal hard drives: sda (Windows), sdb (Windows file storage), and sdc (Linux).  I ran the LiveCD and used the guided option.  The only option I saw for GRUB was hd0.  I get Error 17 when GRUB tries to load.  Nothing will load after the error 17 message.  Apparently, GRUB is not in the MBR of sda.  

How do I correct this so I can have a dual boot?  I am fairly new to Linux and would appreciate any assistance.

Thanks,

JB

---

### Post by Pumalite on 2008-05-10
Post:
sudo fdisk -l

---

