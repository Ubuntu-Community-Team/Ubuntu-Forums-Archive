---
title: "Install Gutsy from a pendrive instead of a CD"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by neymac on 2007-10-18
Is it possible to install Ubuntu 7.10 [COLOR="Red"]from[/COLOR] a pendrive instead of a CD, recording the image file on the pendrive?
How to do this? (my computer can boot from USB pendrive)
I'm running out of CDs.

---

### Post by foresto on 2007-10-18
Have you tried the procedure(s) on this page?

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by neymac on 2007-10-18
I'll try.
But now I'm finishing download the Desktop iso. Is there any way to use the Desktop iso or only the Alternate does work?

---

### Post by grogger13 on 2007-10-21
i followed the instructions in that thread, but when i booted to the usb it said: kernel could not be found: linux

what files am i missing?

---

### Post by bobwonderful on 2007-10-21
The link below works well. 

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

I'm a newbie at this and it worked easily.

---

### Post by jpnurmi on 2007-10-28
Hi

I'm trying to install Kubuntu 7.10 (kubuntu-7.10-alternate-i386.iso) from an USB-stick (because my CD/DVD-drive is broken). I've been following this guide: [https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

Booting to the installer works fine but I have problems while trying to mount the USB-stick on /cdrom:
> 
    # mkdir /cdrom /dev/cdroms
    # cd /dev/cdroms
    # ln -s ../sdb1 cdrom0
    # mount -t vfat /dev/cdroms/cdrom0 /cdrom
    mount: Mounting /dev/cdroms/cdrom0 on /cdrom failed: No such device

In fact, any mounting attempt gives same error: "No such device"
> 
    # mount -t vfat /dev/sdb1 /test
    mount: Mounting /dev/sdb1 on /test failed: No such device

    # mount -t ext3 /dev/hda2 /test
    mount: Mounting /dev/hda2 on /test failed: No such device

, where /dev/sdb1 is the USB-stick and /dev/hda2 is an ext3 partition.

Any ideas?

---

### Post by jpnurmi on 2007-10-30
The solution was easier than I thought. I simply switched to **kubuntu-7.10-desktop-i386.iso** (instead of alternate) and everything worked flawlessly.

Oh, and the installation was actually much easier than what [https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick") describes.

All I did was
[LIST=1]
[*]made the usb-stick bootable with syslinux (3.52)
[*]copied contents of kubuntu-7.10-desktop-i386.iso on the usb-stick
[*]renamed /isolinux -> /syslinux, isolinux.bin -> syslinux.bin, isolinux.cfg -> syslinux.cfg
[*]voila!
[/LIST]
So no need of moving files to root, editing syslinux.cfg, nor mounting the usb-stick on /cdrom..

---

### Post by snickers295 on 2007-10-30
yup, those are basic a should work with every iso because i have tried it with DSl, slax, ubuntu, mandriva and fedora.

---

### Post by orangey on 2007-10-31
> **bobwonderful said:**
> The link below works well. 

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

I'm a newbie at this and it worked easily.

Thanks bob!  That worked wonderfully well for me.  What stumped me early on with the other guides was the partitions and such.  Fantastic.

---

### Post by stueegeek on 2007-11-01
I was able to follow these instructions to make the PC boot, but there is no persistence in the settings.  

> **bobwonderful said:**
> The link below works well. 

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

I'm a newbie at this and it worked easily.

The Pendrivelinux web site is a little unclear about persistence working.  They claim it's fixed, but still offer a patch for "historical" reasons, which is fine by me, except I can't tell if the version I have has the fix.

They do claim:
"In addition to installing Ubuntu to a USB device and then booting Ubuntu from USB, this tutorial will enable you to automatically save your changes and settings back to the stick and further restore them on each boot using a second "casper-rw" persistent partition. "

Did you do anything special to get persistence to work?  Thanks.

---

### Post by jimsmith80220 on 2007-11-01
I also followed the pendrive linux instructions, I just wanted to be able to run Ubuntu from USB, not install it, and it worked till I started getting "Gnome unable to lock .ICEauthority" or similar message, when booting in persistence mode. I can boot in safe graphics and live modes. I may need to modify the shutdown procedure 
Also, upgrading Ubuntu never seems to persist, as I do it anew every boot with the same upgrades. I do not understand the basic casper rw set up and how it is supposed to work.
The lilo instructions also did not work for me completely as I could not run liloconfig with fstab errors, there is unionfs in the fstab.
If someone can get persistence to work please post; I will also if I get anywhere. Thanks.

---

### Post by tafsen on 2007-11-01
I can't seem to get the FAT 16 partition to work. When I try to mount I get this error.

"Mount: /dev/sdb1 : can't read superblock"

---

### Post by tafsen on 2007-11-07
Is there no one who can help me?

---

