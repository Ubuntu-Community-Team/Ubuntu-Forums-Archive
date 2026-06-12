---
title: "i can't boot from floppy"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by davidgq on 2007-05-30
When i installed ubuntu i set to install grub onto a floppy but the disk it made doesn't seem to work. When i try booting from the floppy it just says "GRUB" on the bottom of the screen and doesnt do anything or let me type anything from there. Am i doing something wrong?

---

### Post by confused57 on 2007-05-30
> **davidgq said:**
> When i installed ubuntu i set to install grub onto a floppy but the disk it made doesn't seem to work. When i try booting from the floppy it just says "GRUB" on the bottom of the screen and doesnt do anything or let me type anything from there. Am i doing something wrong?

What you might want to try is installing grub to the Ubuntu root partition, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
the results of "find /boot/grub/stage1" will return something like "root (hd0,2)"...
you would do "setup (hd0,2)" or the results of "find /boot/grub/stage1)  to install to the root partition.

Then download and burn a GAG boot floppy:
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)
with grub on the root partition, the GAG floppy should be able to boot Ubuntu.

---

### Post by davidgq on 2007-05-31
> **confused57 said:**
> What you might want to try is installing grub to the Ubuntu root partition, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
the results of "find /boot/grub/stage1" will return something like "root (hd0,2)"...
you would do "setup (hd0,2)" or the results of "find /boot/grub/stage1)  to install to the root partition.

Then download and burn a GAG boot floppy:
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)
with grub on the root partition, the GAG floppy should be able to boot Ubuntu.

I tried this but ultimately i was left in the same place: the screen says "GRUB" followed by a blinking "_"
nothing can be typed and i have to reboot

---

