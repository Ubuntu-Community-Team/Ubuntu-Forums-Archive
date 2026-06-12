---
title: "Sony VAIO PCG-51412L Black Screen"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by MEISJWM on 2011-04-08
I'm experiencing an issue with loading a Sony VAIO laptop with Ubuntu.  I can load it with version 10.10 and chose the NOMODESET option.  Display works fine until reboot after setup then only an external monitor will work.  Questions:

1. Is this an xorg.conf issue?
2. Is this a driver issue?
3. Where is 10.10 storing the xorg.conf file these days or do I need to create a new one within the X11 directory?

Many thanks in advance for assistance.

---

### Post by MEISJWM on 2011-04-08
To elaborate on the Graphics controller, the lspci | grep VGA command reveals the following:

00:02.0 VGA compatible controller: Intel Corporation Core Processor Intregrated Graphics Controller (rev 02)

Thanks again.

---

