---
title: "Odd Trouble with Ubuntu 7.04 x64"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by xValo87x on 2007-08-25
I just grabbed the 7.04 x64 Ubuntu (DVD).

I formated my drive accordingly (20gb ext3 & 2gb swap).

Booted up to the LiveDVD and did the install.

Installed fine. 

When restarting I get to the boot loader, click on the generic kernal (no problems).

Now here is what I don't get...

    -> It boot up into cmd prompt, and not the GNOME interface...
    -> The screen flashes a few times and pops up to say that my X server (graphic interface is not configured properly, would I like to view the report).
    -> The report says that it identity's my video card, but it fails to load 'nvidia' driver  ... stating that it doesnt exist.

It then returns to the cmd prompt, where I can login and do whatever...however, this is not what i was looking for...

Any suggestion's?

My system is as follows:

..Intel Core2 Duo E6600 (OC'd 2.5ghz)
..2GB Crucial Ballistix DDR2 800
..ASUS P5n32-E SLI PLUS 680i
..1(WD)200GB SATA2 1(STA)320GB SATA2
..GeForce 7800GTX 256MB
..700W PSU OCX
..LG DVD Super Drive

.. think thats all the important ones.

---

### Post by Pumalite on 2007-08-25
At the command line: sudo dpkg-reconfigure xserver-xorg Choose most defaults, choose 'vesa' as your driver. Then: startx

---

### Post by xValo87x on 2007-08-25
Thank you for the quick reply, i will try this and report back.

---

### Post by xValo87x on 2007-08-25
Thank you for the bit of info, it worked perfect.

<3

~valo

---

### Post by Pumalite on 2007-08-25
You are welcome. Glad it worked for you.

---

