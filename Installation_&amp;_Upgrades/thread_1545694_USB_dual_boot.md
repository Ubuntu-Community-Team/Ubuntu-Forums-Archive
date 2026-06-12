---
title: "USB dual boot"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by movega on 2010-08-04
Hi,

I have just finished installing a LAMP sandbox (Ubuntu 10.04 LTS - aka Lucid Lynx, Apache2, MySQL5, php5 and Joomla) on a 16GB USB drive. The installation was smooth, the Lucid Lynx release is brilliant very easy to install, installing the additional packages was not too much of a problem.

Now there is a slight problem, the installation program has installed Ubuntu 10.04 LTS as dual boot (Windows 7 and Ubuntu 10.04 LTS). I am fine with this as I intend to resize my hdd and install Ubuntu 10.04 LTS on a dedicated partition.

The problem is that the installer has done something weird with GRUB2. It has created a GRUB partition on the main HDD and another on the USB drive, and somehow split GRUB2 between both disks. The end result is that if the USB key is not connected to the laptop, the laptop would boot straight into the GRUB2 rescue command line. Obviously the GRUB2 menu (and something else) is on the USB key.

What I want to do is simple, have GRUB2 on the laptops main hdd. So how can I move it without breaking anything.

Lastly, I would not expect the installer to do this. Although I may have missed something during the install.

Thanks for your help

---

### Post by oldfred on 2010-08-04
Welcome to the forums:

You missed the advanced button that lets you choose which MBR to install grub to.
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

You need to install grub to the external and reinstall a windows boot loader to the internal drive. Or install Ubuntu to internal, so its grub controls the internal drive.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by movega on 2010-08-13
Sorry for the delay oldfred but I have been quite busy, and still am, updating a website for the Ladakh Emergency Appeal.

I have gone through the steps in [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive) (installing Lilo, as I don't have time to find the disks that came with the laptop).

The laptop now boots from the internal drive without having to have the external drive connected. But the external drive does no longer boot, the MBR must be damaged.

I will boot from Live disk when I can find some time, hoppefully this weekend.

---

