---
title: "Installing on Thinkpad T61"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by GML3G0 on 2007-06-09
I've been trying to install Kubuntu on my new Thinkpad T61 (Intel X3100, Intel 4965 AGN) and I keep getting the following error as it's loading the kernel:

/bin/sh: can't access tty; job control turned off (initramfs)

I tried installing using the alternate CD, and it installed and booted up fine. However, when the GUI loads, I don't see anything. The screen is just an almost solid teal color.

---

### Post by GML3G0 on 2007-06-10
bump

---

### Post by GML3G0 on 2007-06-10
to the top

---

### Post by jbennet on 2007-06-10
I have the same problem on an ancient R30. Using the irqpoll option as well as vga=711 fixes it (it may hang for up to an hour for some reason, just leave it)

---

### Post by GML3G0 on 2007-06-11
OK, I'm in a functional Kubuntu environment. I reinstalled using the alternate CD and set a much lower resolution before downloading the the xorg-intel drivers using apt-get and setting the intel driver in my xorg.conf. 1440x900 works now. There's only one problem however - whatever is displayed on the monitor is very blurry. Any ideas?

---

### Post by sorin7486 on 2007-07-03
What is the native resolution for your display ??... Usually if you use displays at resolutions different than the native one you get a blurry image...

---

### Post by ciphermonk on 2007-07-03
The procedure for getting rid of the blurryness as well as getting sound and wireless working can be found here...

[http://forums.fedoraforum.org/showthread.php?t=159516](http://forums.fedoraforum.org/showthread.php?t=159516)

I recently worked all those things out on my T61. I even have Compiz Fusion running on it.

---

### Post by verica on 2008-02-15
I'm A Biginner With Ubuntu. I'm Trying To Install The Grafic Card Drivers In Ubuntu For A T61. Can You Help Me Out With Some Steps? Thx.

---

