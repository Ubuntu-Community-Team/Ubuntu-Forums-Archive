---
title: "Can't edit menu.lst"
date: 2005-07-10
forum: Installation &amp; Upgrades
---

### Post by microsome on 2005-07-10
I have a dual boot sytem with XP on the master disk and Ubuntu on a slave disk. I tried to modify the setting of the grub loader so that XP is my default OS. Unfortuneatly, I can't modify this file.

Any suggestions??

---

### Post by al7kz on 2005-07-10
Try

sudo gedit /boot/grub/menu.lst

---

### Post by drummer on 2005-07-10
[QUOTE=microsome]I have a dual boot sytem with XP on the master disk and Ubuntu on a slave disk. I tried to modify the setting of the grub loader so that XP is my default OS. Unfortuneatly, I can't modify this file.

Any suggestions??[/QUOTE]
 menu.lst is in the /boot/grub folder, so has to be edited as root:
$ sudo gedit /boot/grub/menu.lst
should be fairly easy then to change what you want ;)

---

### Post by microsome on 2005-07-12
Thanks, that worked!

---

