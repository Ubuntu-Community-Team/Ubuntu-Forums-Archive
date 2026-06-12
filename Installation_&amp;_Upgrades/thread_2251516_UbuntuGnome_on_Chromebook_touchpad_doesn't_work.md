---
title: "UbuntuGnome on Chromebook: touchpad doesn't work"
date: 2014-11-04
forum: Installation &amp; Upgrades
---

### Post by Calippe_Olivia on 2014-11-04
Hello, 
I have a Chromebook HP-q032ef. I tried Crouton, but I didn't use Chrome OS. So, I decided to install SeaBios and my favorite Linux distribution: UbuntuGnome. The installation went well, but the touchpad doesn't work. I searched by myself, but everything I found talk about Asus Chromebook or HP Pavillon. I found just one interesting post on ArchLinux forum ([https://wiki.archlinux.org/index.php/HP_Chromebook_14](https://wiki.archlinux.org/index.php/HP_Chromebook_14)). This post advices to create a new file in /etc/X11/xorg.conf.d . However, in my UbuntuGnome 14.10, this directory doesn't exist. Meanwhile, I use a mouse but if someone has a better solution. With Crouton, the touchpad worked. 
Thanks in advance

---

### Post by Pilot6 on 2014-11-05
Please, give terminal output

dmesg | grep serio

---

