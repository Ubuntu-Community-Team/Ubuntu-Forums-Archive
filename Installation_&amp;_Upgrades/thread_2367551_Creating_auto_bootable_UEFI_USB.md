---
title: "Creating auto bootable UEFI USB"
date: 2017-07-31
forum: Installation &amp; Upgrades
---

### Post by masas2 on 2017-07-31
Hi!  Okay, so UbuntuLive USB autoboots, in almost all computers I've tried.  UEFI works properly.

But... when I "install Ubuntu" to a USB, it does not autoboot the same way.  Yes, it will autoboot on the machine I've installed from, but not on other machines.

I have to create a boot link in UEFI, telling the UEFI where to find shim.

But this step is not necessary on ubuntuLive....


How can I create a universally bootable ubuntu?

---

### Post by oldfred on 2017-07-31
UEFI only boots USB external drives from /EFI/Boot/bootx64.efi. On the Ubuntu installer that has a lightweight shim/grub boot loader, just configured to boot installer.

For a full install to a flash drive, we have to copy the entire /EFI/ubuntu from internal drive's ESP to /EFI/ubuntu on flash drive's ESP. And then copy again to /EFI/Boot and rename shimx64.efi to bootx64.efi. Then UEFI can find a bootable file. The full version of grub/shim looks for more supporting boot files in /EFI/ubuntu, so you also need that on flash drive also. 
  I then updated fstab to have correct UUID for ESP on external drive. 


More details in link in my signature.
       Full install
[https://askubuntu.com/questions/906857/installing-ubuntu-on-usb-and-booting-from-destop-with-uefi](https://askubuntu.com/questions/906857/installing-ubuntu-on-usb-and-booting-from-destop-with-uefi)
[URL="http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi"]http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi
[/URL]
 UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad 

[URL="http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi"]
[/URL]

---

### Post by sudodus on 2017-08-01
If you ***remove the internal drive***, and then boot into a live drive with Ubuntu (in UEFI mode), you can install Ubuntu to a USB drive, and it will install 'everything' including the complete content of the EFI partition to the USB drive.

This way your USB drive will be bootable in UEFI mode (but not in BIOS mode), also after you have plugged the internal drive back into the computer.

Please avoid proprietary drivers, if you the system to be portable between computers.

[hr][/hr]
It is also possible to create installed systems that are portable and bootable in both UEFI and BIOS mode. See these links and links from them, if you want more details

[help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

