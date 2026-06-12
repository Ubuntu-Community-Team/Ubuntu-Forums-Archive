---
title: "how can i remove ubuntu and its uefi ?"
date: 2015-08-03
forum: Installation &amp; Upgrades
---

### Post by Coder88 on 2015-08-03
I barely know what UEFI is, but someone it has mucked up my system. I just installed Ubuntu 14.04 to an empty partition on my C drive, chose to also install bootloader there. Now my BIOS no longer has the ASUS All in One built in DVD drive listed as an option for a device to boot from; thus i can no longer boot from a liveDVD of any flavor of linux. The Ubuntu installed also did not recognize wifi and I have no long usb cable so my current Ubuntu install has no internet access thus i can not install any additional linux software. This really stinks how I have somehow lost my ability to boot a CD or DVD from the dvd drive, I really do not understand how Ubuntu mucked this up. What can I do to possibly get back a working BIOS that has a choice to boot from the dvd drive?

---

### Post by oldfred on 2015-08-04
Did you change settings in UEFI from/to UEFI or CSM?
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Ubuntu should not have changed UEFI settings on booting other devices. But turning on/off UEFI may have. If you turned on UEFI secure boot it may limit booting other devices unless you specifically allow it by changing settings in UEFI.

Have you tried a full cold boot. Where you unplug system, if laptop remove battery and hold power key for 10 sec or so to drain all power. Then when booting immediately press correct key to get into your UEFI/BIOS.

      
 Screen shots of secure boot settings Asrock, Asus, HP, Acer
[URL="https://neosmart.net/wiki/disabling-secure-boot/"]https://neosmart.net/wiki/disabling-secure-boot/

[/URL]
 UEFI may have setting that is Windows 8 or Windows 7, which probably is to turn off secure boot
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)

[URL="https://neosmart.net/wiki/disabling-secure-boot/"]
[/URL]

---

