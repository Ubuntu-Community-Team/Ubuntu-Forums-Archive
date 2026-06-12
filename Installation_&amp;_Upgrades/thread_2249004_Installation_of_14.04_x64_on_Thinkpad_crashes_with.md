---
title: "Installation of 14.04 x64 on Thinkpad crashes with error"
date: 2014-10-18
forum: Installation &amp; Upgrades
---

### Post by ChrisLX on 2014-10-18
Since some years I use Dualboot to install Ubuntu-Versions without problems on my Thinkpad  (L520, Core i3-2310M, 4GB RAM, Intel HD Graphics 3000 IGP,  Fingerprint-Reader, [BIOS 1.23 10/8/2013]("http://support.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-l-series-laptops/thinkpad-l520//downloads/DS013593")). Now I want to install LXLE 14.04 x64 (I like Lubuntu,  LXLE maybe even better). As in the past I used [YUMI - Multiboot USB Creator]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/") to write the Live ISO-Image on an external bootable USB-HD. The Live-System started always without problem und also the access to the existing Linux partition (Ubuntu 13.04 + /swap) on the HD (Samsung HN-M750MBB 750 GB) was possible.  One after the other I tried different flavors of 14.04 and all Installations crashed with the same error at the end:

* LXLE 14.04 x64 to the existing Linux-Partition with YUMI - Multiboot USB
* LXLE 14.04 x64 to the existing Linux-Partition with Live-DVD
* Lubuntu 14.04 x64 to the existing Linux-Partition with YUMI - Multiboot USB
* Ubuntu 14.04 x64 to the existing Linux-Partition with YUMI - Multiboot USB
* Ubuntu 14.04 x64 to the existing Linux-Partition with Live-DVD
* LXLE 14.04 x64 to a formated empty HD (Samsung HM641JI 640GB) with YUMI - Multiboot USB
* Ubuntu 14.04 x64 to a formated empty HD (Samsung HM641JI 640GB) with Live-DVD

               I was able to make a Screenshot of the error (see attachment PNG and last part of the message below), but could not copy the text in the box with 3 viewable lines. Is there a command (tried Ctrl + C) to copy this text or where can I find this text in the live system? I have added the logfiles (ZIP) on the internal HD. I can not believe Ubuntu will not work anymore on my system (starting the system leads to an endless bootloader screen). 

...
```
source ID 6530 was not found when attempting to remove it
GLib.source_remove.rows_changed_id)             
```
               [HR][/HR]

---

### Post by ChrisLX on 2014-11-15
The same install error occurs in 14.04.1 and I have confirmation from a Thinkpad L412 user that this happens for him also (both on 14.04 and 14.04.1). 
In contrast I was however able to install 14.10 without a problem. 
Please let me know the correct place to report this serious LTS bug for a major Laptop platform.

---

