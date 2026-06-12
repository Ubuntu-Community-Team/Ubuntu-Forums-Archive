---
title: "How to change video mode?"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by BiscuitTin on 2008-08-05
Hi, I've finally managed to install Ubuntu on my Vaio VGX-TP1E using the Alternative install CD. The problem is that the installer is using some video mode that my monitor (TV) can't handle. If I boot the system and select the rescue mode I can log into the installed Ubuntu 8.04 installation but how do I configure the X server to change the video mode?

I've tried:

   dpkg-reconfigure xserver-xorg

But this seems to only allow me to re-configure the keyboard?

---

### Post by Pumalite on 2008-08-05
Go into Recovery Mode and try: xfix

---

### Post by BiscuitTin on 2008-08-05
Done it. Makes no difference. Startx still makes the screen go blank.

---

### Post by BiscuitTin on 2008-08-06
Solved it. Found what I needed here:

[http://www.freebsd.org/doc/en/books/handbook/x-config.html](http://www.freebsd.org/doc/en/books/handbook/x-config.html)

I created the new xorg.conf file and edited it adding my monitors resolution modes.

---

