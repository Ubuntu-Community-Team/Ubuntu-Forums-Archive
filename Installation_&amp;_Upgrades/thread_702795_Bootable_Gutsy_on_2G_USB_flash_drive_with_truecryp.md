---
title: "Bootable Gutsy on 2G USB flash drive with truecrypt"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by crstophr on 2008-02-20
My goal is to install Gutsy on a 2G USB flash drive without using the pendrive casper-rw" persistent partition.  If that works my next step is to try to encrypt the whole thing with truecrypt's new system disk encryption feature. 

I've done similar stuff under gentoo using luks-crypt and a custom initramfs in the past.  

My real question is why use pendrive at all?  I don't care about even write distribution on flash, this is a throw away device I got from a vendor.  I don't need to mount a FAT16 partition on other OSs to carry data around.  Can't I just make my / partition ext3 sized to the whole device and just install ubuntu?  Am I missing something?

--Chris

---

### Post by Pumalite on 2008-02-20
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
Never done it. Follow the instructions.

---

### Post by mrsteveman1 on 2008-02-20
Your work is going to be getting the initrd to run truecrypt and map the root partition before it tries to mount root.

So you are going to have to include the truecrypt kernel module and enough of the other modules so that truecrypts module can load, and then you will have to insert a script in the boot process so that truecrypt runs and tries to map the device, then get it to mount that cleartext root device afterward.

It might actually be easier with 4.3a because that was a real kernel module, 5.0 is a fuse pseudo filesystem.

I've thought about doing this in the past but never got around to it.

---

