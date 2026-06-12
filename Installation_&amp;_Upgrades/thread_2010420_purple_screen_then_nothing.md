---
title: "purple screen then nothing"
date: 2012-06-25
forum: Installation &amp; Upgrades
---

### Post by deeppow on 2012-06-25
Download the 64bit version of 12.04 and created a disc.  Boot from it and get the initial purple screen but then nothing but a blinking cursor.  ??

Thanks for any assistance.

---

### Post by wilee-nilee on 2012-06-25
Check if using nomodeset gets it booted.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by deeppow on 2012-06-25
Gets me a little further but after setting nomodeset it goes black again.

I am running an nVidia card (680).

---

### Post by deeppow on 2012-06-26
Folks, 

Gotta say that I've used Ubuntu on and off for a significant number of years and instead of becoming easier to install it has become more difficult.

---

### Post by deeppow on 2012-06-26
Have tried to work down through the sticky above and still get black screens, e.g. vga771.

---

### Post by dino99 on 2012-06-26
maybe you still have a xorg.conf, delete it, now the kernel directly deal with X.

---

### Post by deeppow on 2012-06-26
> **dino99 said:**
> maybe you still have a xorg.conf, delete it, now the kernel directly deal with X.

Would this be in the installation files on the CD built from the iso?  Not sure how to go about deleting it.

---

