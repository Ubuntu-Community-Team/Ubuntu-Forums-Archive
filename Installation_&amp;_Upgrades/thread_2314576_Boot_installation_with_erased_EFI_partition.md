---
title: "Boot installation with erased EFI partition"
date: 2016-02-22
forum: Installation &amp; Upgrades
---

### Post by giovanni24 on 2016-02-22
Dear all,
I correctly installed ubuntu 15.10 on a dell xps 9350 (everthing working except DA100 video converters) with legacy mode on and secure boot off.
Later I run boot-repair and the system was not able to boot in any way. So I formatted everything with gparted (erasing all the partitions) and tried to reinstall ubuntu 15.10 from usb but it was unable to install the boot loader.
I think that I erased the EFI partition when I used gparted so may be ubuntu is not able to reinstall correctly the boot loader?
I tried to install Opensuse Leap 42.1 and it installed without problem the boot loader.
There is any solution for this problem? How can I installa again the right boot loader in order to make working ubuntu 15.10?

Giovanni

---

### Post by yancek on 2016-02-22
I'm not clear about your statement in the first sentence above.  If you correctly installed Ubuntu, why did you run boot repair?
If you had Legacy mode on then you are not installing EFI and there would be no EFI partition.  If you are using EFI, you need Legacy mode off as I understand.
You should have the option to install EFI if that is what you want when you boot the Ubuntu installation medium.

---

### Post by oldfred on 2016-02-22
You should be able to install in UEFI boot mode.

But Dell seems to be booting from /EFI/Boot/bootx64.efi which Ubuntu's grub does not create.
Boot-Repair may add it. And I normally suggest that everyone add it as a backup way to boot anyway.

 Install Ubuntu 15.10 on Dell XPS 15 2015 9550 with Nvidia 960
[http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960](http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960)
Dell XPS 13 9343 Needs /EFI/Boot/Bootx64.efi to boot
[http://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13](http://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13)
[https://bugs.launchpad.net/dell-sputnik/+bug/1499323](https://bugs.launchpad.net/dell-sputnik/+bug/1499323)
Black Screen on Install (15.04 & 15.10) Dell XPS 8900 
[http://ubuntuforums.org/showthread.php?t=2303880](http://ubuntuforums.org/showthread.php?t=2303880)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)

---

