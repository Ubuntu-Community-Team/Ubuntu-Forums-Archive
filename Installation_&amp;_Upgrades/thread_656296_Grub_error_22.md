---
title: "Grub error 22"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by indianballer24 on 2008-01-02
I just installed ubuntu gutsy to an external hard drive.  In the installation I used my whole external harddrive (sdb), and installation went perfectly without any errors.  But whenever I set my bios to boot from the usb external hard drive, the grub screen comes up and says error 22. Can someone please help me?

---

### Post by logos34 on 2008-01-02
if no grub screen, just error 22:

-[install grub to USB drive MBR using live cd]("http://ubuntuforums.org/showthread.php?t=224351").  Use 'setup (hd**1**)'

if the grub menu screen lists kernels:

highlight the ubuntu kernel and press 'e' to edit.  'e' again on the 'root' line and change to (hd**0**,?) where '?' = root partition #. Press 'enter' and 'b' to boot.  If it works make the change permanent:

gksudo gedit /boot/grub/menu.lst

---

