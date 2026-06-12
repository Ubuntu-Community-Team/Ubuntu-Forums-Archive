---
title: "Ubuntu on a USB stick - Live vs Full Install"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by RCC2k7 on 2010-05-11
I was able to make a live USB stick of Ubuntu 10.04 using Ubuntu's built-in tool. But I learned the hard way that updating Ubuntu then results in an unbootable stick. I've read in these forums about users who have performed full installs on USB sticks, but when I run the installer from the Live CD, I don't see the option to install on a USB stick. Yes, I had the 8GB stick plugged in while running the installer from a CD, but all I saw as install locations were the /dev/sd<n> (hard drive) partitions.

Setting aside the debate on how soon the flash memory will wear off, here's what I'm wondering - assuming I can find out how to do a full install onto the USB stick.

Does a full install makes your USB stick un-portable? Can you still plug the same stick on your desktop and laptop PC's and run Ubuntu on either, or is the installation tied to the hardware where you first run from the USB stick?

---

### Post by frostschutz on 2010-05-11
I just use the Live CD on USB. You can make a separate data partition on the USB stick for your home directory. When a new version comes out I just replace the Live CD partition with the new one. However, this only works fine if you're happy with the apps installed on the Live CD by default, since it does not store additional programs you install.

---

### Post by bumanie on 2010-05-11
Startup disc creator is found under System --> Administration --> Startup disc creator. Technically it is a portable distro that should auto-detect changing hardware environments when plugged in to different computers - but it may not work on every computer.

---

### Post by dino99 on 2010-05-11
installing your distro and the bootloader on a usb stick, give you an easy portable system, you only need to be able to plug it :P

there is no difference between a partition on a stick and one on hdd

---

### Post by bumanie on 2010-05-11
> **frostschutz said:**
> I just use the Live CD on USB. You can make a separate data partition on the USB stick for your home directory. When a new version comes out I just replace the Live CD partition with the new one. However, this only works fine if you're happy with the apps installed on the Live CD by default, since it does not store additional programs you install.

Don't believe this is correct - Startup usb creator installs in persistence mode and is meant to save changes - look here for more details - 
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/)

---

### Post by RCC2k7 on 2010-05-11
> **frostschutz said:**
> However, this only works fine if you're happy with the apps installed on the Live CD by default, since it does not store additional programs you install.
Actually, the Startup Disk Creator will let you set aside some space on your USB stick (up to 4GB) for persistent storage. You can then install (or uninstall) new programs and change settings. You cannot uninstall any of the preinstalled programs though. All this is OK, but you also cannot update Ubuntu using the software update tool or Synaptic. Even though the updater won't stop you and will try to install the updates, the result is an unbootable stick afterwards. (Kernel Panic)

---

### Post by oldfred on 2010-05-11
See Herman's site for flash or SSD USB drive install:

Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

### Post by RCC2k7 on 2010-05-12
I was able to do a regular install Ubuntu 10.04 on a USB stick. It turns out that you have to select the Manual Partitioning option and then you'll see the removable USB stick as another hard drive. (/dev/sdf instead of /dev/sda for the built-in hard drive)

Color me impressed, as after installing, updating and configuring Ubuntu on my desktop PC, I was still able to plug the stick to my laptop and run it there too!

---

### Post by pft0 on 2010-05-14
i had install ubuntu on usb since 7.04, but now hal is removed, it did not detect some special hardware when i move the usb to different computer, e.g. sound card, is there anyway i enable hal in ubuntu 10.04?

---

### Post by kansasnoob on 2010-05-14
I prefer Portable Linux installs:

[http://rudd-o.com/new-projects/portablelinux](http://rudd-o.com/new-projects/portablelinux)

> The live removable drives created by this program let you use the remaining disk space on your removable drive to store and transport files between Windows, Mac and Linux computers, as usual. 

---

