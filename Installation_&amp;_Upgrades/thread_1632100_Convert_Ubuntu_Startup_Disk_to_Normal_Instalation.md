---
title: "Convert Ubuntu Startup Disk to Normal Instalation"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by theroadside on 2010-11-27
I have a very old laptop with no CD and no Floppy and a BIOS that won't boot from a USB device.  I wanted to install Ubuntu on it though so I pulled the hard drive and connected it to my Macbook via a USB-to-PATA adapter.  I booted the Macbook off the live CD and tried to install Ubuntu to the USB drive but the install wanted to update the boot partition on my Macbook which I would prefer not to do (I run Ubuntu on the Macbook in a VM).  Instead, I used the Startup Disk Creator in Ubuntu 10.04 to make the hard drive from the old laptop an Ubuntu Startup Disk.  I put it back in the laptop and it works fine, but when you boot it asks if you want to install Ubuntu and of course you can't because there is no available disk.  I thought about pulling the drive and doing this all again but splitting the drive into two partitions so I could make one partition the startup disk and install to the other, but I was not sure this would work.  The disk in question is only 12 GB so I don't have a lot of space to work with.  Also, this particular laptop is a huge pain to get the drive out of so if I can somehow fix this without removing the drive again that would be awesome.  If there was some way to just convert the startup disk to a "regular" installation that would be ideal.

---

### Post by infowars on 2010-11-27
Sorry but I'm new to linux, also, but  the drive should show up as a "fixed" drive, in Mac, or maybe you could try free "UNetbootin" Mac to get the distro on to the attached drive, again only if it shows as a "fixed" drive.

Hope someone who knows more about this will show up soon for you! :P

---

### Post by efflandt on 2010-11-27
When doing a regular install to a USB drive, there is a way to put grub on the USB drive instead of your internal hard drive, I have done that numerous times. But you have to pay attention and know where to look for that.

For 10.10 at the **bottom** of the page where you manually set up or select which partitions for Ubuntu is a drop down list to select where you want to put grub.  Just make sure that you select the same drive where you are installing Ubuntu (/dev/sdb or whatever).

The only thing I am not sure of is how a Macbook works, and whether you would end up with a Mac setup instead of Intel on the hard drive.

---

### Post by C.S.Cameron on 2010-11-27
I would like to add to Efflandt's comment:
At at "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
And then confirm device to install to is the 12GB drive.
Before leaving partitioning confirm "Device for boot loader installation" points to the 12GB drive.

I don't know of a way to convert a Startup Disk Creator install to full install but I use a tweeked persistent Unetbootin install on my old 4GB EEE PC without much problem.

---

### Post by theroadside on 2010-11-28
Thanks.  This worked perfect.

> **C.S.Cameron said:**
> I would like to add to Efflandt's comment:
At at "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
And then confirm device to install to is the 12GB drive.
Before leaving partitioning confirm "Device for boot loader installation" points to the 12GB drive.

I don't know of a way to convert a Startup Disk Creator install to full install but I use a tweeked persistent Unetbootin install on my old 4GB EEE PC without much problem.

---

