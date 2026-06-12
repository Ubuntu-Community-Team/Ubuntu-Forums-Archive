---
title: "Install Windows from USB stick in Ubuntu"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by nicucalcea on 2010-07-07
So here's the deal:

I use Ubuntu and I'm very happy with it. But, my job requires Windows 7, so I tried to install it, so I can dual boot. Unfortunately, my DVD drive is broken, and I can't install Win 7 properly.

How do I install Windows from Ubuntu, without having to use a DVD? I've got the .iso, what should I do next?

Thanks,
Nicu.

---

### Post by C.S.Cameron on 2010-07-07
> 1. sudo apt-get install gparted
2. open gparted -> format stick to ntfs
-> put bootable flag (right click in gparted - manage flags)

3. extract win7.iso to usb stick or if you have live dvd just copy contents to usb stick

From Amedac

---

### Post by nicucalcea on 2010-07-07
Thanks for the answer. But it did not work. Booted Ubuntu as usual. Am I missing some steps?

---

### Post by davidmohammed on 2010-07-07
check in your bios - you need to ensure that removable devices is higher in your boot order than your hard-drive.

---

