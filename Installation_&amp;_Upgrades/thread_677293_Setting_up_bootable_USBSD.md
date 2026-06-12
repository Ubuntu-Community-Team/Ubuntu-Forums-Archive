---
title: "Setting up bootable USB/SD"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by yosh1 on 2008-01-24
Hello out there,

First things first, I am almost completely new to Linux and therefore a little lost with the terminology and procedures around here. What I am trying to do: Setting up a bootable USB  Device, or alternatively a bootable sd card in order to install ubuntu on my eee pc.

I was using this guide:
[https://help.ubuntu.com/community/EeePC](https://help.ubuntu.com/community/EeePC)

which workes like a charm untill I got to this point

> Before we can run this script on your soon-to-be USB based installer, we'll need to set the partition to bootable. Do this via the parted tool:

sudo parted /dev/sdX set 1 boot on

You'll also need to make sure that the device has a filesystem label. Use one of the following to create a label on the device:

If your usb device is formatted to ext2/3 use:

sudo e2label /dev/sdX1 ubuntu

If your usb device is formatted to msdos/vfat use:

sudo dosfslabel /dev/sdX1 ubuntu



So I used fdisk -l and i figured that 

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         960      967613+   6  FAT16


must be the sd card im trying to get it on.

Trying the next step it gives me this

ubuntu@ubuntu:~$ sudo parted /dev/mmcblk0p1 set 1 boot on
Error: The flag 'boot' is not available for loop disk labels.             
Information: Don't forget to update /etc/fstab, if necessary. 

In the guide its saying I have to make sure it has a filesystem label, and since its fat formatted I tried:

ubuntu@ubuntu:~$ sudo dosfslabel /dev/mmcblk0p1 ubuntu
sudo: dosfslabel: command not found

So thats where im Stuck - how do I get that thing bootable? What am I doing wrong?

P.S. Im running ubuntu via live cd if that is any help.

Thanks in advance for helping me out in this mess

---

### Post by yosh1 on 2008-01-25
does nobody out there know what I can do about 

sudo: dosfslabel: command not found

?! Come on your better than that ;)

---

### Post by GMP on 2008-01-26
I also recieve the same problem:
dosfslabel: not found

I am a Unix geek from years back, but am new to Ubuntu.
I have a clean install of Gutsy (7.10).

Does anyone know where dosfslabel is packaged in the installation, and ultimately how we can re-install dosfslabel ?

My work around was to install the USB back into a Windows PC and label it there.  This was just for neatness, as I guess the actula fslabel is not critical.

GMP

---

### Post by schwieb on 2008-02-10
I don't know if you are still stuck on this, but these commands work for me on Gutsy.  I was not able to get the 'dosfslabel' command to work either.

  mkfs.vfat -F 16 -n usb /dev/sdx1
  mkfs.vfat -F 32 -n usb /dev/sdx1 (doesn't always work)

Both commands will format your drive, so make sure nothing is important on there.  Just replace 'sdx1' with the location of your device.  You'll also need to unmount your thumbdrive before this will work.  A pretty good guide for the whole general procedure is here:

[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/]("http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/")

After that the guide you referenced works great. Overall, I could not be happier with my Eee PC running Ubuntu 7.10!

---

### Post by rykel on 2008-06-22
Hi,

I am trying to make a thumbdrive bootable. However, Ubuntu cannot seem to deal with its sector size... please help?

[INDENT][B]$ sudo syslinux -s /dev/sdc1
syslinux: only 512-byte sectors are supported
[/B][/INDENT]

The device is a Creative Micro (MuVo) N200 MP3 Player and currently formatted to FAT16.

I do NOT have anything important on the drive.

---

