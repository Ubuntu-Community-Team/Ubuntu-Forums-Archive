---
title: "BIOS SLIC on ASUS notebook"
date: 2014-01-26
forum: Installation &amp; Upgrades
---

### Post by Herbon on 2014-01-26
A few days ago I purchased a ASUS S500ca running Win8. My plan was simply remove the old HD, and install a new SSD with Linux.

After I had installed the new drive, I popped in a USB drive loaded with the new OS.

The process started by stop after I choose the Linux distro.

A check of BIOS revealed it see the USB drive and SSD. But not the boot order.

I removed the SSD and imaged it on another laptop, and then installed it in the ASUS.

After the power button is pushed, it go's straight to the BIO setting and fails to boot with the installed SSD or USB. (there is no CD rom)

I found a few sites claiming BIOS maker are coding their notebooks for Win8 use only with "slic"

Is there a linux software  or hardware (removing CMOS battery) work around for this.

I would hate to install the Win8 HD back in the device. :(





[http://en.wikipedia.org/wiki/BIOS#SLIC](http://en.wikipedia.org/wiki/BIOS#SLIC) 
[http://forums.mydigitallife.info/threads/29740-WindSLIC-UEFI-SLIC-injector/page10](http://forums.mydigitallife.info/threads/29740-WindSLIC-UEFI-SLIC-injector/page10)

---

### Post by Herbon on 2014-01-29
A little more research revealed simply removing the CMOS battery for 2 min, and turning back on the device than hit F10 to save the new set up, and bang new Linux box!!!

---

