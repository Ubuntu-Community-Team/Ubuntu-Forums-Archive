---
title: "Live USB not booting"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by benutne on 2010-11-13
I've tried two methods of creating a live USB stick for 10.10 on a Patriot X-Porter 4GB stick.  The first I tried was the usb-creator.exe on the install disc.  The second was the Universal USB installer from pendrivelinux.com.  Both seemed to work fine, no errors when creating the live USB, but when I reboot and tell my computer to boot from the stick, nothing happens.  Just a blinking cursor in the upper left corner.  This has happened on two separate machines too, my desktop and Dell laptop.  I don't happen to have any blank CDs laying about to burn the ISO.  

Any ideas?  

Thanks

---

### Post by C.S.Cameron on 2010-11-13
This might be due to a bad iso download, check the MD5SUM.

---

### Post by benutne on 2010-11-13
> **C.S.Cameron said:**
> This might be due to a bad iso download, check the MD5SUM.

MD5 checks out OK.

---

### Post by benutne on 2010-11-13
Issues resolved.  The partition was not marked as bootable.  The built in usb-creator.exe and the tool from pendrivelinux.com both are incapable of marking a partition bootable for some reason.  Used diskpart.exe under Windows to create the partition and set it to active (bootable).

---

