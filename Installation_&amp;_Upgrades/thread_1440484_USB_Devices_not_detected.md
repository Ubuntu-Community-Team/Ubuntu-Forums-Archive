---
title: "USB Devices not detected"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by Sly1972 on 2010-03-27
Hi,
 
I am the absolute newbie, having just switched today from Windows to Ubuntu.
 
Eveything has gone smoothly, all applications are up and running, but I have a major hiccup: 
 
My PC has 3 USB ports which (according to themanufacturer) are all 2.0. When I run lsusb, I get:
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
Now, when I plug ANY USB device (printer, scanner, NTFS, FAT, Flash drives...), absolutely nothing happens, and the lsusb message stays the same.:(
 
CORRECTION: It took several minutes, but My printer and scanner Have been detected and installed. Still nothing on USB Flash or external hard drives.
 
I have installed the pmount and usbmount packages, rebooted a few times: no changes.
 
Anyone would have an idea of what I did wrong? Any suggestion for generic pilots for USB Flash/External drives?

---

