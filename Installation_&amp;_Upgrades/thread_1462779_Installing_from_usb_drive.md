---
title: "Installing from usb drive"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by Munyua on 2010-04-26
Hi am using a Defendo Internet Appliance Server and want to install ubuntu 9.10 server edition. Am unable to access the usb cd rom even after setting it as the first boot. 

The system is currently running on Redhat linux and I want to completely migrate to ubuntu, I am a novice in the linux administration and prefer the gui.

Regards,
Denis Munyua

---

### Post by Herman on 2010-04-26
I don't know what resources you might have available to you, but if you can access some other computer with a working CD/DVD drive, you should be able to install Ubuntu to a USB flash memory stick.
After that, install a miniature copy of your server installation in another USB flash memory stick.
Go to the computer you want to install the server in.
Boot the regular Ubuntu USB installation.
Use Ubuntu to perform any partitioning work you may need to do first.
Plug in the other USB stick, the one containing the server installation.
Use a series of dd commands to copy the server partitions from the USB to the hard drive.
Resize your new file systems to fill the partitions they are in.
Install the server's GRUB to MBR in the server's hard disk.

Will those ideas be any help? :)

---

