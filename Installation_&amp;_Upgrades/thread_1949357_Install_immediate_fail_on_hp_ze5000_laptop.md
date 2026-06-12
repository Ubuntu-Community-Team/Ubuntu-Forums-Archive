---
title: "Install immediate fail on hp ze5000 laptop"
date: 2012-03-30
forum: Installation &amp; Upgrades
---

### Post by sharper47 on 2012-03-30
I would dearly love to install Ubuntu on my older HP laptop.  Have tried  three or four different versions of 11.10 (regular, alternate, lubuntu,  etc.) and the result is exactly the same for all.  It starts the boot  CD, displays one line,
  
 ISOLINUX 4.04 20110518 ETCD Copyright (C) 1994-2011 H. Peter Anvin et al

and  freezes. Windows recovery CD's work just fine, by the way.  If I do the  install in WinXP and Wubi, the install process seems to run ok, but  when I reboot and select Ubuntu to start, I get this:
 
Try (hd0,0): FAT16: No WUBILDR
Try (hd0,1): NTFS5: No wubildr
Try (hd0,2): invalid or null
Try (hd0,3): invalid or null
Try (fd0): invalid or null
Error: Cannot find GRLDR in all devices, press ctrl+alt+del to restart.

What's going on, and how do I fix it?
  
Here's the system:

hp Pavilion ze5000 (production proto, actually did not sell under this model number, not sure the actual )
Intel P4M 2.2G, 1G Ram, Hitachi 80G HDD (HTS541680J9AT00), LCD 1400x1050, DVD/CD-RW QSI SBW-161, STD FDD
  ALi PCI-AGP Controller, Display adapter ATI Mobility M6 (Radeon) 32MB PCI bus 1, dev 0, fcn 0, irq 10
IDE ATA/ATAPI ALi M5229 PCI Bus Master IDE Controller PCI bus 0, dev 16, fcn 0
Ali FIR controller, 1394, modem, acpi, parallel port, serial port, svideo out
  Wireless Lan-Express IEEE802.11 PCI adapter PCI bus 0, dev 9, fcn 0, irq10
Ethernet Nat. Semi  DP83815 10/100 MacPhyter 3v PCI adapter PCI bus 0, dev 18, fcn 0, irq 11
PCMCIA (2 slots) TI PCI-1520 Cardbus Controller PCI bus 0, dev 10, fcn 0,1, irq 11
  USB 1.1 ALi PCI-USB OpenHost Controller PCI bus 0, dev 2, fcn 0, irq 10

Any  help or pointers would be appreciated.  The unit has lots of  sentimental value.  I was the lead hardware design engineer on this  series of laptops.  And I admit to knowing not too much about software  in general and especially being a Linux newbie...

---

### Post by bcbc on 2012-03-30
For the Wubi problem...
You can review this: [http://ubuntu-with-wubi.blogspot.ca/2011/01/wubildr-wubildrmbr-and-grldr.html](http://ubuntu-with-wubi.blogspot.ca/2011/01/wubildr-wubildrmbr-and-grldr.html)

And also this more recent bug report: [https://bugs.launchpad.net/wubi/+bug/961707](https://bugs.launchpad.net/wubi/+bug/961707) 
In this bug report the attached video shows the same error. The workaround was to mount and copy wubildr to the first partition. For reasons not yet established the wubildr was not detected on the ntfs partition.


For the CD problem... 
not sure. I'd guess that the CD is bad. Can you confirm that it works on a different computer?

You might also need to supply [nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132") for your video card (but this won't explain it hanging so early in the boot process).

---

