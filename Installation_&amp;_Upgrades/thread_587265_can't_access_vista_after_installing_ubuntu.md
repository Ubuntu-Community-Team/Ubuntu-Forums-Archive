---
title: "can't access vista after installing ubuntu"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by martin622292 on 2007-10-22
installed ubuntu after vista (home basic) assuming it would automatically configure a dual boot 
system . . . (it did before with windows 2000) . . . now it boots only into ubuntu . . . no sign of vista!

---

### Post by radovan01 on 2007-10-22
what about vista partitions?

---

### Post by Wiebelhaus on 2007-10-22
1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

---

### Post by logos34 on 2007-10-22
Reinstalling grub is not going to help if there's no vista entry in your config file or the options are set wrong.

Post your menu.lst:

**cat /boot/grub/menu.lst**

---

### Post by Hobbs131 on 2007-10-23
What you did was the correct thing actually...What you need to do now is reinstal vista overwriting ubuntu. But when you reinstal vista you need to partition it with the correct amount through the manual configs. after you get this done (it takes 30 min - an hour) you can then go through & install ubuntu by partitioning it to the rest (also through manual config.

---

