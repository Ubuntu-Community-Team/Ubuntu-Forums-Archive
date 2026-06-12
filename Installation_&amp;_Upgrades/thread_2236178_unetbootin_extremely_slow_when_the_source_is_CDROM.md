---
title: "unetbootin extremely slow when the source is CDROM device"
date: 2014-07-25
forum: Installation &amp; Upgrades
---

### Post by mctiew on 2014-07-25
I  am trying to create a bootable USB stick using Unetbootin but the source media happened to be already burnt on the CDROM device. So I specified /dev/sr0 as the source image, wow, it took me 4 or 5 hours to create a 4G usb stick.

Something is terribly inefficient in the way it handles the CDROM source device. Perhaps if it reads the source and then dumps it as an image source it would be much much faster !

Unetbootin from Ubuntu 14.04.

---

### Post by ajgreeny on 2014-07-25
Much easier to boot to the live CD/DVD and then run the startup-disk-creator which I believe will then make a USB of the running OS.

I've never done it that way, but I think that is correct.  Certainly worth a try.

---

