---
title: "After I Install  Ubuntu 8.04  I Get  GRUB  Error 21"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by Sonah on 2008-08-31
Please I need HELP

I Have Eee PC 901 

it was work fine .  using Xandros linux

But I Install Ubuntu 8.04 in 8GB class6 SDhc

After Ubuntu Finish from install I Reboot 

I only Get this msg  :
 > GRUB Loading. Please wait ...
[COLOR="Red"]Error 21[/COLOR]  " 

what is the wrong ?

even if I remove the SD card from slot to boot Xandros  still get the same Error the "GRUB  Error 21"

 I'am a Noob 

I can only Boot from flash Stick that has Live Ubuntu 8.04 

can i remove GRUB ? if so then how ?

Please .. Please Help me :(

---

### Post by Pumalite on 2008-08-31
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)
Having several drives inverting the order of boot in BIOS might do the trick.

---

### Post by caljohnsmith on 2008-08-31
From the Grub manual:
> **Error 21** : Selected disk does not exist
This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 
So it looks like Grub can't find the disk that has its system files, which is probably your SD card. First of all, does Xandros Linux use Grub as its boot loader? I assume it does. If it does, then boot Ubuntu from your flash drive (make sure your SD card is *not* connected), open up a terminal, and do:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Xandros partition in the form of (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That should make it so you can boot Xandros again, and then we can try and get the Ubuntu on the SD card to boot.

---

### Post by Pumalite on 2008-08-31
Read this thread carefully:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)
Also get Super Grub and see if you can boot your Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Burn to disk and boot to disk.
Super Grub can boot Ubuntu no matter where it is if it's bootable.

---

