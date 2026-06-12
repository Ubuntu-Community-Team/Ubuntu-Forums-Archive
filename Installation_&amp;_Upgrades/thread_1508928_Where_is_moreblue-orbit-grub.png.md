---
title: "Where is moreblue-orbit-grub.png ?"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by BergmanW on 2010-06-13
[SIZE=4]L.S.

Did an new install of Ubuntu 10.4 64 bit
tried to pimp the start-up process (grub/grub2)
As my background  is totally black when selecting the version of Ubuntu to boot.

I saw a reference to 
/usr/share/images/desktop-base/moreblue-orbit-grub.png

in module : /etc/grub.d/05-debian-theme

But it is not there.
If it should be there, what package did I miss and with what packages is that .png file installed ?

[/SIZE]

---

### Post by billstei on 2011-01-28
The package is called "desktop-base" and after I installed it (in Lucid) update-grub ran as a post-install and the moreblue-orbit-grub.png is now the boot splash background image (I assume by default, because I didn't select it).

---

### Post by Bucky Ball on 2011-01-28
You can also play with this:

[http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html](http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html)

It allows you to change the background and much more.

---

