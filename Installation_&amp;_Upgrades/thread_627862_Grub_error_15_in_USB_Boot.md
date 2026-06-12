---
title: "Grub error 15 in USB Boot"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by samurailink3 on 2007-11-30
I'm getting a grub error 15 while trying to boot 7.10 from a USB drive. Where is grub located on here (it appears to be using the same format as the live cd)? Any ideas on how to correct this? I followed the tutorial here "http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/"
Any help would be appreciated. Thanks!!

---

### Post by RogerDodger on 2007-12-08
Hi,
I'm in the same boat as you.  Just installed Ubuntu 7.10 on a USB drive and put GRUB on the same USB drive.  No problems.  If I try to boot from that drive I get a choice of 3 variations of Ubuntu, or two variations of Windows.  Trying to boot any of the Ubuntus results in:
 GRUB Error 15: File not found

Trying either of the Windows boots (which are located on another drive) 
also results in an error.

Mike

---

### Post by samurailink3 on 2007-12-09
I just got another USB drive the other day just so I could mess around with this issue... no luck so far.. but I'll keep trying.

---

### Post by Pumalite on 2007-12-09
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)
This error can also occur if the files needed to boot with are missing or corrupt in the /boot/grub directory. Refer to Grub loading stage1.5 for how to completely delete possibly corrupted GRUB files and restore them again from /sbin/grub.
[http://users.bigpond.net.au/hermanzone/p15.htm#GRUB_Loading_stage1.5_Read_Error](http://users.bigpond.net.au/hermanzone/p15.htm#GRUB_Loading_stage1.5_Read_Error).

---

### Post by Pumalite on 2007-12-09
Try installing to USB with all internal drives disconnected.

---

