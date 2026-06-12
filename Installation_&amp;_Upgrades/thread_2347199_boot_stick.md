---
title: "boot stick"
date: 2016-12-22
forum: Installation &amp; Upgrades
---

### Post by pete1977x on 2016-12-22
usually you put one version of linux on a boot usb stick. Can you have 2 iso and will your bios let you pick one to install??

---

### Post by sudodus on 2016-12-22
Yes it is possible to have multiboot USB sticks. There are several tools available. You can do it yourself more or less from scratch for example according to this link,

[One pendrive for all PC (Intel/AMD) computers - single-boot dual-boot multi-boot](https://ubuntuforums.org/showthread.php?t=2259682)

-o-

I wrote that tutorial, but to be honest, I don't use it very much. Instead I consider USB sticks to be temporary devices. I store several iso files, and when I want to run a system live or install that system, I [clone](https://help.ubuntu.com/community/mkusb) it from the iso file to a USB pendrive. It is a fast process, and much more flexible than to have a multiboot pendrive, that must be kept up to date with new versions of several linux distros.

---

### Post by yancek on 2016-12-22
You can put as many iso files as you have room for on the usb stick and boot them.  You will need to install the Grub bootloader to the device and manually create boot entries unless you have a full install of some Linux on it.  The BIOS won't let you pick one to install, you select the usb drive in the BIOS and then select the distribution you want from the Grub menu.  If you indicate your intentions. someone might have a simpler way to accomplish whatever it is you intend.

---

### Post by oldfred on 2016-12-22
I usually keep several ISO on a flash drive just for emergency repair.
It is just like installing to any second drive, but drive, partition and path are the regular issues I have even though I think I understand system. I have had drives change device like sdf flash drive becomes sdb drive on reboot.

 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive) 

I also do not combine my older BIOS only flash drive with my newer UEFI boot drives. But have kept both.

---

### Post by C.S.Cameron on 2016-12-22
I am a big fan of mkusb but the easiest way to put multiple systems on a USB stick is MultiBootUSB: [http://multibootusb.org/](http://multibootusb.org/)
I have been using my MBUSB utility stick for over seven years.

---

