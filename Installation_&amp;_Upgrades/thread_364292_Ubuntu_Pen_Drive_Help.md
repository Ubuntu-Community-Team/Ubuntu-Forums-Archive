---
title: "Ubuntu Pen Drive Help"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by Falcon- on 2007-02-18
Hey guys, I could use a little advice dealing with booting Ubuntu on a flash drive.  I've been able to get knopix to work, just because they provide a nice usb-formatting tool - but the ubuntu one is a bit more complicated because it uses multiple partitions to save the data.

I've followed the directions on pendrivelinux.com , and I have trouble when I try to write the new partition table on my flash drive.  I gives me a warning about dos x6.0 and when I do fdisk -l it still only shows one partition.  If I do fdisk /dev/sdb1 and then p to show partitions it will show both partitions.  How can I do the the mkfs steps 1 and 2 if I only see /dev/sdb1 and not a second partition that is formated as the linux file format.

[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610)

tutorial I'm trying to follow.

Thanks in advance!

---

### Post by Falcon- on 2007-02-18
Bump - if thats alright.  Any help please?

---

### Post by falsedust on 2007-02-22
I have the exact same problem,  I followed the instructions perfectly. I got Damn Small Linux to work in my Oti 128Mb usb key just fine.
Oh another thing is when I plug my new Sandisk Cruzer 2Gb usb key in after going through [http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/](http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/) I now get an extra CD-ROM drive icon on my desktop ??

**update**
Ok so the U3 software was the main problem so  i had to goto a Windows machine and uninstall it, which did get rid of the extra CD-ROM icon from my desktop. Although I am still not able to make it bootable.

---

### Post by inoxllor on 2007-09-09
Is it possible to install UBUNTU (or any related version) in a 512 mb usb pen?

---

### Post by Pumalite on 2007-09-09
[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

[http://pendrivelinux.com/2007/01/25/usb-x-ubuntu-610](http://pendrivelinux.com/2007/01/25/usb-x-ubuntu-610)

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

