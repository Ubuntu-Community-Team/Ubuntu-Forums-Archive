---
title: "No native mode, forcing panel scaling"
date: 2011-12-30
forum: Installation &amp; Upgrades
---

### Post by fancyerii on 2011-12-30
hi all
   I installed ubuntu server 11.10 from hard disk.
   I have 2 hard disk and one is used for windows xp and the other one is left unused. Today I installed ubuntu server on it. But after installation, it can't start up. I searched a related post in 
[https://bbs.archlinux.org/viewtopic.php?id=123783](https://bbs.archlinux.org/viewtopic.php?id=123783)
   But when I enter recovery model, I can't find  /boot/grub/menu.lst, /boot is just an empty directory.

---

### Post by dino99 on 2011-12-30
" /boot/grub/menu.lst " refer to the oldish/unused grub-legacy. Now 11.10 use grub2 aka grub-pc, you find it into /etc/default/grub

more info with link below

---

### Post by fancyerii on 2011-12-30
root@host#echo "drm_kms_helper.poll=0" >> /etc/default/grub
bash: /etc/default/grup: Read-only file system

root@host#ls -l /etc/default/grub
-rw-r--r-- 1 root root 1238 ....

I want to append one line to this file but failed.
what's wrong with it?

---

### Post by fancyerii on 2012-01-03
anyone could help?

---

