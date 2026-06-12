---
title: "default booting shud be windows"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by mshanker on 2007-11-30
hi 
i have windows xp sp2 and ubuntu however i would like windows to be booted by default. pls tell me how to do this

---

### Post by Nano Geek on 2007-11-30
Assuming you have only Windows and Ubuntu on your computer, do the following.

[LIST=1]
[*]Open the GRUB Bootloader menu file.```
sudo gedit /boot/grub/menu.lst
```
[*]Search the file for **default\t\t0**. Replace the highlighted text with default        4
[*]Save the file, and at reboot, it should default to Windows.[/LIST]Enjoy :KS

---

