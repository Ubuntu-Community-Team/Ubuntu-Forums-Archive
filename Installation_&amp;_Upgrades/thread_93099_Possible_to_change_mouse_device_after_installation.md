---
title: "Possible to change mouse device after installation?"
date: 2005-11-21
forum: Installation &amp; Upgrades
---

### Post by marcris on 2005-11-21
I installed Breezy on my rather ancient desktop and the result works fine, except that I had a USB mouse plugged in during installation and now Breezy requires the USB mouse and won't work with a serial one. Is there a way to change this after installation, or do I have to go re-install?

---

### Post by giftnudel on 2005-11-21
hi, 

you can do sudo dpkg-reconfigure xserver-xorg and enter the correct mouse device (preferred) or look into /etc/X11/xorg.conf and change it there (don't do this since apt will not update the file if it is modified by the user)

So far,

giftnudel

---

### Post by marcris on 2005-11-22
Thanks a lot. I'll try that as soon as I can.

---

