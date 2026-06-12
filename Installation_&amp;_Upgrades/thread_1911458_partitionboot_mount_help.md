---
title: "partition/boot mount help"
date: 2012-01-18
forum: Installation &amp; Upgrades
---

### Post by qgroff on 2012-01-18
Hi guys!  I've searched and found a couple related posts but I want to ask the question as it *directly* relates to my system because I really don't want to mess anything up!

I want to install ubuntu alongside Windows 7, on a 100GB partition I've prepared (which I'm pretty sure is /dev/sda6).  Here's what I have available to me:
```
/dev/sda 750.2GB   ATA WDC WD7500BPVT-8
  /dev/sda1 fat32  26.8GB Windows Recovery Environment
  /dev/sda2 ntfs  300.1GB Windows 7 (loader)
  /dev/sda5 ntfs  318.4GB <nothing>
  /dev/sda6 ntfs  104.9GB <nothing>
```
So if I want to be able to dual boot, keep Windows 7, and install ubuntu on the 100GB partition, what settings do I want for
a) the /dev/sda6 device (my options are a bunch of file system types I don't recognize plus fat16, fat32, ntfs, and swap; this is a 64-bit machine, in case that matters), and
b) the "Device for boot loader"?  Should this just be /dev/sda or do I want it to be /dev/sda6 also?

Thank you so much, I'm excited to get started!

---

### Post by zvacet on 2012-01-19
Install Ubuntu on sda6 and mark it as /root and format as ext4.Install bootloader on sda and Ubuntu will be first OS on boot.If you want to change that you can use [https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)  or [http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html). I think 100GB for root is too much and it is good to have separate home partition.In case you decide you want to do it that way 

1. root=~20GB                                                           mountpoint /root
2.swap=2G
3.home=rest of free space                                          mountpoint /home

If you have separate home you can reinstall,fresh install...without losing your files & setings.

---

