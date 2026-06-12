---
title: "BusyBox problem on USB install"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by Legendário on 2008-07-17
Hi, i am following an alternative method of installation of Ubuntu, which is on the wiki page: [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

I am trying to install Ubuntu with an USB stick with a Compaq EvoN1020v laptop, which doesn't have the bios boot option for usb. To do that i have created a boot Cd as described on the page above.

The problem is that i fall on the BusyBox v1.1.3 built-in shell(ash) (initramfs) issue. I found some posts here regarding that, but i believe that none of them were trying to install with a usb image. The method used to created the image was the one on: [http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/](http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/)

Besides that, i have tried to add the **all_generic_ide** parameter on the grub boot, as suggested on some of those, but with no success. If someone can help me here, that would be very nice.

Thanks

---

### Post by knappyroot on 2008-08-21
I've had the same issue installing Ubuntu 8.04 on a 16Gb SanDisk Cruizer, trying to boot up on an IBM ThinkPad laptop.  Only had this problem when I tried installing the Lilo bootloader though; previously tried using Grub as a boot loader but kept getting Error Code 15.  Lilo seems to allow you to boot up but can't find some OS files...

---

