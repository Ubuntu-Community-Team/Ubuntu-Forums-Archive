---
title: "Problem: How do I get Grub to recognize XP?"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by Ameliorate on 2007-05-23
I installed ubuntu one one of my hard drives AND THEN installed XP on the other. Yet, GRUB does not list Windows as an option on the menu screen. I know that I have to edit the /boot/grub/menu.lst but I don't know what I have to put in it. 

What do I put in the file?

---

### Post by confused57 on 2007-05-23
You need to open a terminal and post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"
and
```
gedit /boot/grub/menu.lst
```
you just need to post the entries to boot Ubuntu

---

