---
title: "ISO install from USB stick. [Not boot install]"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by gypsumwolf on 2009-12-09
Is it possible to mount a Ubuntu ISO file (on a running Ubuntu laptop) from a USB stick and run the installer from there?

---

### Post by phillw on 2009-12-09
> **gypsumwolf said:**
> Is it possible to mount a Ubuntu ISO file (on a running Ubuntu laptop) from a USB stick and run the installer from there?


Yes, you can.

Doing it via the command line is this method ...

> **Using loop Kernel Module**
 First you need to make the directory to put the ISO into using the following command
 sudo mkdir /media/isoimage
 Now you need to add the loop module to your kernel.
 What kernel loop module does?
 I want to give brief introduction to kernel loop module.Using the module loop it is possible to mount a filesystem file. squashfs is a &#8220;loop&#8221; with (de)compression (Compressed Loopback Device) and it is possible to mount a compressed filesystem like a block device and seamlessly decompress its data while accessing it.
 Use the following command to load loop module
 sudo modprobe loop
 **Mount ISO Image**
 If you want to mount you need to use the following command
 sudo mount debianetch.iso /media/isoimage/ -t iso9660 -o loop
 In the above command you can replace debianetch.iso to your own iso image.
 Now you should have your iso file mounted, and accessible from your [desktop]("http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html#").
 **Unmount ISO Image**
 Unmount ISO Image Using the following command
 sudo umount /media/isoimage
If you'd rather add it to your GUI as a saved script then -->  [http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

That has both methods, I just find it quicker to use the Command Line !!

edit ---- ooooh, my 1st post with pre-alpha 10.04 ... Looks like it works :-)

Regards,

Phill.

---

### Post by gypsumwolf on 2009-12-09
Thanks, it is mounted, but I am trying to figure out how to run the installer?

---

### Post by phillw on 2009-12-09
> **gypsumwolf said:**
> Thanks, it is mounted, but I am trying to figure out how to run the installer?

Does it not launch package manager to say new packages have been found ?

/edit  Sorry for being a bit vague - I'm running 10.04 & don't have any of my bookmarks transferred over yet !!

Phill.

---

### Post by gypsumwolf on 2009-12-09
No. It is mounted though. I am using LXDE desktop so maybe that is why its not poping up.

What I want to do, if possible, is install a fresh install of Xubuntu from the ISO file that is on my USB disk. The computer can not boot from USB. The computer has ubuntu running using LXDE desktop. If not I will simply burn a CD, but I am trying to do it this way for the experience and for fun and becuase I will not have access to a blank CD for maybe an hour or 2 LOL!

---

### Post by phillw on 2009-12-09
Ahh, well you can do it this way --> [http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/](http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/)

If that's not exactly what you want - have a look round that site - what they don't get pen-drives doing is most likely illegal, immoral or fattening (Although I'm not too sure about the last two when they start getting usb drives to support 5-10 different operating systems as an O/S selection upon booting)

Regards,

Phill.

---

### Post by phillw on 2009-12-09
> **gypsumwolf said:**
> No. It is mounted though. I am using LXDE desktop so maybe that is why its not poping up.

What I want to do, if possible, is install a fresh install of Xubuntu from the ISO file that is on my USB disk. The computer can not boot from USB. The computer has ubuntu running using LXDE desktop. If not I will simply burn a CD, but I am trying to do it this way for the experience and for fun and becuase I will not have access to a blank CD for maybe an hour or 2 LOL!

You could probably do it by adding the iso file to your list of repositries, but I don't know how to do that for a mounted iso.

---

