---
title: "Install 10.04 from external hdd"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by Bluestars on 2010-08-30
Can anyone tell me how or if it is possible to install Ubuntu from an external harddrive? Also I will be installing on an eMachines m2352, does anyone know if Ubuntu runs well on those?

---

### Post by Experimental on 2010-08-30
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

In step 2 Select usb stick and click show me how

---

### Post by oldfred on 2010-08-31
I like using flash drives.

Is your external a bootable drive? The standard USB flash erases the entire flash drive and installs a boot loader and the ISO.

If the external has data you may not want to erase all the data. You can directly install grub2 and boot the ISO using loopmount without erasing the drive.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864&highlight=ISO](http://ubuntuforums.org/showthread.php?t=1535864&highlight=ISO)

---

