---
title: "Broadcom Wireless in Lucid - 2.6.32+"
date: 2009-11-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by novafluxx on 2009-11-11
Anyone know yet if Ubuntu will have the open source Broadcom wireless stuff in Lucid, or if they have it in the 2.6.32 kernel for Lucid now?

---

### Post by Kevbert on 2009-11-12
The way I got my wireless to work in Lucid was by copying the /lib/firmware/b43 and /lib/firmware/b43legacy files from my 9.04 installation.

---

### Post by cmccauley on 2010-02-09
I upgraded from 9.10 so was able to boot with an older kernel - not ideal but pretty good.

---

### Post by nanog on 2010-02-09
You may be able to use the bcmwl-kernel-source and bcmwl-modliases. The driver is open source but uses closed source firmware. Its automagically recompiled via dkms so make sure you have that installed too.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
The driver was designed for BCM4311-, BCM4312-, BCM4321-, and BCM4322-based hardware but has been shown to work well with other chips including BCM4328.

---

### Post by gjoellee on 2010-02-09
I am using the Broadcom STA driver that appeared in "Hardware Drivers". It works fine :p

---

