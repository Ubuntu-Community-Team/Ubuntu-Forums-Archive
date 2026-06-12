---
title: "No Display after install"
date: 2005-11-12
forum: Installation &amp; Upgrades
---

### Post by xanthide on 2005-11-12
After the OS is installed and reboots the 2nd time, i get no display.  Well, that may not be totally correct, if anyone is old enough to recall, my display is sort of like when you didnt put your atari cartridge in right.  I get the little "bee boop" sound on startup, but thats as far as i can get.  Heres my system specs

AMD 2500+
A7N8X Deluxe
1 GB RAM
BFG 6600 GT OC

thanks for any help you can give me

---

### Post by teaker1s on 2005-11-12
at grub hit ESC and select recovery mode
sudo dpkg-reconfigure xserver-xorg 
which will help you configure your monitor and graphics  if it's gettting setup wrong

---

### Post by xanthide on 2005-11-12
[QUOTE=teaker1s]at grub hit ESC and select recovery mode
sudo dpkg-reconfigure xserver-xorg 
which will help you configure your monitor and graphics  if it's gettting setup wrong[/QUOTE]
thanks a lot, ill give that a shot :)

---

