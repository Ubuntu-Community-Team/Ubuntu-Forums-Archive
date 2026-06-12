---
title: "live usb on dell laptop with no hard drive"
date: 2018-10-08
forum: Installation &amp; Upgrades
---

### Post by cfli1688c1 on 2018-10-08
i got a dell laptop that is without a hard drive.  I would like to use it with a live usb.
I tried it with zorin os, which i understand to be a branch of ubuntu.
The problem i face is that zorin os does not recognize the wifi unit on the dell laptop, which is broadcom, i need to load bcm driver for wifi to work.
with live usb, i am unable to update the wifi driver/module.

Is there any live linux that recognize broadcom wifi out of the box?

---

### Post by sudodus on 2018-10-09
It is possible to install Ubuntu (and other linux distros) into a USB pendrive. I mean install like installed into an internal drive (but into a USB pendrive).

It works best with a fast USB 3 pendrive, but it is possible also with a slower drive.

See the following link (and links from it),

[How do I install Ubuntu to a USB key? (without using Startup Disk Creator)](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312)

This way it will be possible to install and use a proprietary driver for the Broadcom Wifi chip.

---

### Post by mastablasta on 2018-10-09
another option is live USB with persistancy. however a better option is to actually install it on the USB stick.

furthermore hard drives are relatively cheap lately and you could also get a used one...

---

### Post by C.S.Cameron on 2018-10-09
Dell is not very descriptive.
I understand that 18.04 fixes a number of driver issues.
Especially with Atom cherry trail or Apollo Lake processors.
Isorespin, ([http://linuxiumcomau.blogspot.com/2017/06/customizing-ubuntu-isos-documentation.html](http://linuxiumcomau.blogspot.com/2017/06/customizing-ubuntu-isos-documentation.html)) may be another solution.
Best to do a full install if you want to install proprietary drivers.

---

