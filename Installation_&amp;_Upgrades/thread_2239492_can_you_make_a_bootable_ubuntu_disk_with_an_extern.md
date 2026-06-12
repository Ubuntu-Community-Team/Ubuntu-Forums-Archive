---
title: "can you make a bootable ubuntu disk with an external hard drive instead of usb stick?"
date: 2014-08-14
forum: Installation &amp; Upgrades
---

### Post by drzcoyotex3 on 2014-08-14
If it can be done, is there a tutorial out there how to do it?

---

### Post by matthewrhodes227 on 2014-08-14
[http://www.linuxbsdos.com/2013/10/23/how-to-install-ubuntu-13-10-on-an-external-hard-drive/](http://www.linuxbsdos.com/2013/10/23/how-to-install-ubuntu-13-10-on-an-external-hard-drive/)

---

### Post by oldfred on 2014-08-14
If already running Ubuntu so you can install grub2 easily or have grub on external drive, you can just copy as many ISO as you like into a folder and directly boot using loopmount with grub. ISO does have to be configured for that type of booting, but most Linux ISO are now.

 This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

You can also use scripts.
      
 These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
[https://sourceforge.net/projects/multibootusb/files/](https://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
[http://ubuntuforums.org/showthread.php?t=2175738](http://ubuntuforums.org/showthread.php?t=2175738)
Uses grub4dos to boot many ISO and other bootable files
[http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1](http://www.rmprepusb.com/tutorials/72---easyboot---a-grubdos-multiboot-drive-that-is-easy-to-maintain/e2bv1)

 See yumi for multi-boot versions
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

You may be able to use unetbootin, but have to be extremely careful to have correct settings. Default is erase entire drive and place installer on it like any smaller flash drive.

---

### Post by C.S.Cameron on 2014-08-14
You can install to external drive just like to internal,If your first time, disable your internal drive first.

---

### Post by uRock on 2014-08-14
It'd be a waste of an HDD, but you can run a simple dd command to copy the ISO to the HDD and make it bootable or use Startup Disk Creator.

---

