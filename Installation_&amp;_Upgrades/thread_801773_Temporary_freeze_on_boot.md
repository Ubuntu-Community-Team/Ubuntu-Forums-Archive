---
title: "Temporary freeze on boot"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by sjmorris on 2008-05-20
Since my upgrade from Gutsy to Hardy, the system freezes for almost three and a half minutes early in the boot process. The Ubuntu logo and progress bar show up, but the progress graphic makes one trip from left to right, but stalls on its return.  After three and a half minutes, the boot process continues to completion.

This bothersome stall didn't happen with my old installation of Gutsy and any assistance or advise the will help me eliminate it will be appreciated.

Thanks.

SJMorris

---

### Post by iaculallad on 2008-05-20
For troubleshooting purposes, issue the command on the terminal: **sudo gedit /boot/grub/menu.lst** and comment out the word "quiet" (by placing the # sign before the word). Save it then restart your system. From there, you could see  the boot process happening.. post any error that you could see.

---

