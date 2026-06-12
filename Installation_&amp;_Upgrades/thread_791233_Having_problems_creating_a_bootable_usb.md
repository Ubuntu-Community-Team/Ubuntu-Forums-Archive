---
title: "Having problems creating a bootable usb"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by speakeasy on 2008-05-12
Hey, Ive been trying to create a way to install ubuntu from a usb... I've tried a few different tutorials but they all come to the same conclusion... when i go to boot from the usb drive i get "Missing Loader"...

I have Hardy running on my desktop and I'm trying to install it on my laptop but the cd drive recently burned out...

Does anybody know what I'm doing wrong?

Some of the tutorials...
[http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html](http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by mdurham on 2008-05-12
I was having a frustrating time too until I found this:
> - If your pendrive doesn’t boot, try “install-mbr /dev/sdX” or “lilo -M /dev/sdX” (pendrive must be umounted) after that it worked ok.
Cheers, Mike

---

