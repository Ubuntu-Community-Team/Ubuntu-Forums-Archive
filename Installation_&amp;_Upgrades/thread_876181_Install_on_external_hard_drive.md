---
title: "Install on external hard drive"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by blahbah7 on 2008-07-31
I have Ubuntu on my laptop and want to install Kubuntu on my external hard drive.  I have made 12gb for the OS and 2gb for swap so far.  Now what do I have to do, just pop in the live cd and install it or is there anything else I have to do to run it on the external hard drive?

---

### Post by dstew on 2008-07-31
You can install to an external USB drive using the Live CD. The problem is booting the external drive.

First, you have to figure out how you want to use the external drive. Do you want to take it with you, and boot it on other computers, or always have it plugged in to one computer? If you want to take it to other computers, you will need to make the USB drive bootable. That is, you will need to install grub on it. This is not the default behavior of the Ubuntu installer, so you will have to instruct the installer to install grub there at the last installation step, in the Advanced menu. If you are not sure of the grub-name of the external disk, you can just tell the installer not to install grub at all, and install it later at your leisure, when you have time to figure out exactly what to do.

If you install to an external disk, and create a dual-boot system, accepting the default installation choices, you will end up with the situation where the external disk needs to be plugged in or you will not be able to boot your computer at all. This is because the grub stage2 file (the main part of grub) is installed on the external drive, but the stage1 file (the boot loader) will go into the MBR of your internal hard disk. If the external drive is not plugged in, the stage1 will report an error, because it cannot find the stage2 file it was configured to use.

I would recommend telling the installer not to install grub, and then install grub later by hand when you can figure out exactly how you want to boot the external disk. Or, you can use the grub booter and menu you already have, adding the external drive system as a menu item. You will have to edit the /boot/grub/menu.lst file to do this. You can look at [this guide]("https://help.ubuntu.com/community/Installation"), the external disk section, but I don't think it applies to your particular question. But, there is some info there that might be helpful.

---

### Post by linux_tech on 2008-07-31
This article covers a Ubuntu 8.04 USB Hard Drive install

[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

---

