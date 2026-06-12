---
title: "Hardy on a USB with a custom kernel..."
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by uraidi on 2008-06-30
Can someone shed a light on this please. I got myself a new Gigabyte motherboard thats built on the nvidia 8200 chipset. Connected a 2GB USB with 8.04 hardy on it as per instructions from 

[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

When trying to load Ubuntu - it'd crash. When trying to install it, - it'd crash. Googling around, found this [Cracking ubuntu 8.04 to work with nVidia 8200 chipset motherboard]("http://coyotesg.blogspot.com/")  from coyote that managed to fix the problem by upgrading the kernel to 2.6.25.5

I tried following the guide for creating [LiveCD customization]("https://help.ubuntu.com/community/LiveCDCustomization") - and was hoping to upgrade the kernel in the installation cd then loading that up. But, the whole thing crashed.

Can someone please advise on how to go about, creating a Ubuntu LiveCD, with a 2.6.5.9 kernel, to which I can then follow the instructions for putting onto USB. Ohh, yeah, 1 more thing, I've got a RAID 5 setup from the motherboard, - I should remember to load the raid drivers to access the drives.

anyhelp guys, or direction, much appreciated thanks.

---

### Post by Licurgo on 2008-07-01
Uraidi:
I've read that the Ubuntu 8.04 can itself be installed directly to the USB, fist you select the drive go on with the installation and in the Step 7 you select options or something like that and select to install the grub to the MBR of the USB; but your problem probably is lack of space because this tutorial says that you need at least USB of 4 GB
:lolflag:

---

