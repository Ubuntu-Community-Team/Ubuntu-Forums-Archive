---
title: "Installing Ubuntu 8.04.1 FROM a usb key"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by waspinator on 2008-07-04
Hi,

I would like to install Ubuntu FROM a usb key. (most guides show me how to install TO a usb key) My computer can boot from a USB key, but I'm not sure how to 'burn' the ISO to a usb key instead of a CD. It may sound a bit weird but it seems like it should be possible to do. 

Thanks,
Waspinator

---

### Post by Matt Yun on 2008-07-04
> **waspinator said:**
> Hi,

I would like to install Ubuntu FROM a usb key. (most guides show me how to install TO a usb key) My computer can boot from a USB key, but I'm not sure how to 'burn' the ISO to a usb key instead of a CD. It may sound a bit weird but it seems like it should be possible to do. 

Thanks,
Waspinator

Basically, instead of burning the *.iso file to a usb keydrive, you have to copy files from the *.iso file to the usb key, then make the usb key bootable.  

The usb key will then act like a live CD, provided that your computer can boot from usb devices.  Once you've booted with your usb key, you can install Ubuntu from it, just like from a live CD.  I've done this myself.

Here is a tutorial on how to do it:  [http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux).  This tutorial assumes that you already have access to a computer with Linux.

If you don't, and have to go through Windows, then pendrivelinux.com has another tutorial:  [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial).  However, this necessitates burning the *.iso to a CD.

Browse the pendrivelinux.com site:  there's lot's of good tutorials and articles on creating bootable usb key drives.

---

### Post by waspinator on 2008-07-04
> **Matt Yun said:**
> Basically, instead of burning the *.iso file to a usb keydrive, you have to copy files from the *.iso file to the usb key, then make the usb key bootable.  

The usb key will then act like a live CD, provided that your computer can boot from usb devices.  Once you've booted with your usb key, you can install Ubuntu from it, just like from a live CD.  I've done this myself.

Here is a tutorial on how to do it:  [http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux).  This tutorial assumes that you already have access to a computer with Linux.

If you don't, and have to go through Windows, then pendrivelinux.com has another tutorial:  [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial).  However, this necessitates burning the *.iso to a CD.

Browse the pendrivelinux.com site:  there's lot's of good tutorials and articles on creating bootable usb key drives.

Thanks for the info. It's too bad that you NEED linux to do it, but luckily I have an older version of Ubuntu already installed. It would be nice if there script that would make this easier, or that there was some sort of option in WUBI to make a bootable pendrive in windows.

Thanks
Waspinator

---

### Post by Matt Yun on 2008-07-05
> **waspinator said:**
> Thanks for the info. It's too bad that you NEED linux to do it, but luckily I have an older version of Ubuntu already installed. It would be nice if there script that would make this easier, or that there was some sort of option in WUBI to make a bootable pendrive in windows.

Thanks
Waspinator

Apparently, Ubuntu will support [USB installations]("http://arstechnica.com/news.ars/post/20080629-horny-for-ubuntu-8-10-first-look-at-intrepid-ibex.html") in future versions.

Regarding the difficulty of creating a USB key version of a Linux CD; have you ever tried making a bootable Windows (Barts PE) key drive?  Linux is a piece of cake compared to that.  

Although Ubuntu does not have a utility for creating USB key installations, [other]("https://fedorahosted.org/liveusb-creator") [distros]("http://www.eeextra.com/linux/mandriva-linux-one-2008-live-usb-creation.html") [do]("http://www.puppylinux.com/flash-puppy.htm").

---

### Post by KamalGurung on 2008-07-05
I have created WindowsXP Bootable Disc using Nero, I went through the above urls but I cant understand them well :D.

---

### Post by waspinator on 2008-07-05
> **Matt Yun said:**
> Apparently, Ubuntu will support [USB installations]("http://arstechnica.com/news.ars/post/20080629-horny-for-ubuntu-8-10-first-look-at-intrepid-ibex.html") in future versions.

Regarding the difficulty of creating a USB key version of a Linux CD; have you ever tried making a bootable Windows (Barts PE) key drive?  Linux is a piece of cake compared to that.  

Although Ubuntu does not have a utility for creating USB key installations, [other]("https://fedorahosted.org/liveusb-creator") [distros]("http://www.eeextra.com/linux/mandriva-linux-one-2008-live-usb-creation.html") [do]("http://www.puppylinux.com/flash-puppy.htm").

The Fedora usb creator looks perfect. Just as I would of imagined it. Too bad it doesn't work with an ubuntu iso. I hope ubuntu will make something that nice.

Thanks
Waspinator

---

### Post by Matt Yun on 2008-07-07
Here's something that I just stumbled upon:  [UNetbootin]("http://unetbootin.sourceforge.net/").

"UNetbootin allows for the installation of various Linux/BSD distributions to a partition or USB drive, so it's no different from a standard install, only it doesn't need a CD. It can create a dual-boot install, or replace the existing OS entirely... UNetbootin can install to your local hard disk or make a bootable liveUSB drive. It can also load floppy/hard disk images, or kernel/initrds, or (some) ISO (CD image) files, for installing other distributions."

It's a distro-agnostic utility for installing Linux to a hard-drive or usb partition.  The screenshots show that you can create a bootable usb directly from an *.iso file.  UNetbootin has both Windows and Linux versions.

You should try it; it looks exactly like it fits your needs.

(2008 July 22):  Ubuntu Community Documentation Project has an article on how to [Install From USB Stick]("https://help.ubuntu.com/community/Installation/FromUSBStick").

---

### Post by issih on 2008-07-07
[http://www.teamteabag.com/2008/03/07/install-ubuntu-804-hardy-heron-from-usb/](http://www.teamteabag.com/2008/03/07/install-ubuntu-804-hardy-heron-from-usb/)

That link gives a pretty complete description of how to make a bootable usb from which you can install hardy heron using windows tools.

Hope its useful

---

### Post by lotus49 on 2008-07-08
You should try this [http://klik.atekon.de/liveusb/](http://klik.atekon.de/liveusb/).  It's a graphical tool to create a live USB from a live CD.  Once done, just boot from the USB drive and installation is exactly the same as using a CD.

I haven't used it with 8.04.1 but it worked very well with 8.04 and it was super easy to use.

---

