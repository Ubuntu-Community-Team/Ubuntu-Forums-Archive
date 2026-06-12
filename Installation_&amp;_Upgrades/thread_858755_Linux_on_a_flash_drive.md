---
title: "Linux on a flash drive?"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by patrickaupperle on 2008-07-13
I noticed that fedora has a live usb creator now, and was wandering whether it was possible to make ubuntu install to a usb easily. I was looking around and unetbootin looks like it might work. What do you all think? Should I just put fedora on my usb, or is there a nice and easy way of putting ubuntu on there?

---

### Post by Pumalite on 2008-07-13
You can install Hardy to a 4 GB or bigger Flash Drive as if you were installing to a regular hard drive. Run:
sudo fdisk -lu
You will find the /dev of your Flash drive. In step 8, go to 'Advanced Tab' and change (hd0) for /dev/???

---

### Post by Rallg on 2008-07-13
As an alternative to installing Ubuntu (or any Linux) to a USB drive, you can also install Linux (but NOT the bootloader) to your hard drive, and separately install an alternative bootloader to a bootable USB drive (for example, using Grub4DOS). The advantage of doing it that way: Linux is on your hard drive (would be faster), but your computer's MBR is not changed. You couldn't boot to Linux without the USB.

---

### Post by patrickaupperle on 2008-07-14
> **Pumalite said:**
> You can install Hardy to a 4 GB or bigger Flash Drive as if you were installing to a regular hard drive. Run:
sudo fdisk -lu
You will find the /dev of your Flash drive. In step 8, go to 'Advanced Tab' and change (hd0) for /dev/???

Would that really work? Are there any adverse effects on the flash drive? How much space would be left for programs and customizations on a 4 gig flash drive?

---

### Post by cszikszoy on 2008-07-14
Everything you need to know is here:

[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

---

### Post by patrickaupperle on 2008-07-14
> **cszikszoy said:**
> Everything you need to know is here:

[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

If that is the best way of doing it, then I will just use the fedora  live usb creator. That looks too complicated.

---

### Post by cszikszoy on 2008-07-14
> **patrickaupperle said:**
> If that is the best way of doing it, then I will just use the fedora  live usb creator. That looks too complicated.

What's complicated about it?  Every step is spelled out in detail.  I've done this before and it really only takes about 10 minutes max.

---

### Post by Pumalite on 2008-07-14
I have 3 Hardies in 8 GB Pendrives. I use them everywhere I go.

---

### Post by patrickaupperle on 2008-07-14
> **Pumalite said:**
> I have 3 Hardies in 8 GB Pendrives. I use them everywhere I go.

8 gig? I only have a 4 gig.:mad: Is that enough?

---

### Post by Pumalite on 2008-07-14
I haven't tried it, but there are several post in the Forum that suggest that it is. Try it. If it doesn't work; try this:
[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

---

### Post by cszikszoy on 2008-07-15
4 gig is fine.  I've put it on a 4 gig before.   Actually, 2 gig is fine as well.  I've tried to put it on a 2 gig flash drive and everything was fine.

---

### Post by patrickaupperle on 2008-07-15
> **cszikszoy said:**
> 4 gig is fine.  I've put it on a 4 gig before.   Actually, 2 gig is fine as well.  I've tried to put it on a 2 gig flash drive and everything was fine.

It? Does that mean Hardy installed normally, hardy live w/persistence, or Fedora?

---

### Post by tact on 2008-07-15
There is a much easier way to get a bootable ubuntu install on a USB stick - but what you end up with is just like a liveCD, just on USB not CD.   So no persistence (and in a lot of situations thats good!) plus you can do installs from the USB drive just like from liveCD.

What you need:
- Download the latest hardy liveCD ISO  - v8.04.1
- A USB stick (1GB is plenty)
- go download this handy utility that automatically takes whats on the liveCD and puts it onto the USB stick and makes it bootable: [https://launchpad.net/~probono/+archive]("https://launchpad.net/%7Eprobono/+archive")

(Just add the repo for the hardy version to your software sources, and apt-get it.)

You do not even need a CDROM drive - you can make the liveUSB direct from the ubuntu liveCD ISO without even burning it to a CD. Instead - mount the "ubuntu-8.04.1-desktop-i386.iso" on /media/cdrom

```
sudo mount -o loop /home/your_username/ubuntu-8.04.1-desktop-i386.iso /media/cdrom 
```
(assumes the ISO file is in your home folder)

Then insert your USB stick into a USB port, run the liveUSB install program (System>Admin>Install LiveUSB), make sure that the correct USB device is selected as the target... and watch the magic.

(BTW all data on the USB stick will be wiped off in the process - so make sure you have no treasures stored on it first).

---

### Post by patrickaupperle on 2008-07-15
> **tact said:**
> There is a much easier way to get a bootable ubuntu install on a USB stick - but what you end up with is just like a liveCD, just on USB not CD.   So no persistence (and in a lot of situations thats good!) plus you can do installs from the USB drive just like from liveCD.

What you need:
- Download the latest hardy liveCD ISO  - v8.04.1
- A USB stick (1GB is plenty)
- go download this handy utility that automatically takes whats on the liveCD and puts it onto the USB stick and makes it bootable: [https://launchpad.net/~probono/+archive]("https://launchpad.net/%7Eprobono/+archive")

(Just add the repo for the hardy version to your software sources, and apt-get it.)

You do not even need a CDROM drive - you can make the liveUSB direct from the ubuntu liveCD ISO without even burning it to a CD. Instead - mount the "ubuntu-8.04.1-desktop-i386.iso" on /media/cdrom

```
sudo mount -o loop /home/your_username/ubuntu-8.04.1-desktop-i386.iso /media/cdrom 
```
(assumes the ISO file is in your home folder)

Then insert your USB stick into a USB port, run the liveUSB install program (System>Admin>Install LiveUSB), make sure that the correct USB device is selected as the target... and watch the magic.

(BTW all data on the USB stick will be wiped off in the process - so make sure you have no treasures stored on it first).

Sounds cool, but I really want persistance. Thank you anyway, though.

---

### Post by mikaelstaldal on 2008-07-15
> **patrickaupperle said:**
> If that is the best way of doing it, then I will just use the fedora  live usb creator. That looks too complicated.

It doesn't have to be so complicated has they do.

You don't have to make two partitions on the USB drive, just make one big ext2 partition and use EXTLINUX (part of the SYSLINUX package) to boot from it.

---

### Post by patrickaupperle on 2008-07-16
> **mikaelstaldal said:**
> It doesn't have to be so complicated has they do.

You don't have to make two partitions on the USB drive, just make one big ext2 partition and use EXTLINUX (part of the SYSLINUX package) to boot from it.

I have no idea what extlinux or syslinux are. Could you please provide some more detailed instructions?

---

### Post by mikaelstaldal on 2008-07-18
> **patrickaupperle said:**
> I have no idea what extlinux or syslinux are. Could you please provide some more detailed instructions?

Have a look at its homepage:
[http://syslinux.zytor.com/wiki/index.php/EXTLINUX](http://syslinux.zytor.com/wiki/index.php/EXTLINUX)

The SYSLINUX package is available for Ubuntu, just do:
```
sudo apt-get install syslinux
```

Do like this:
[LIST]
[*]Boot from the Ubuntu install CD-ROM
[*]Insert the Flash disk you want to install to
[*]Select the flash drive during install and create one big ext2 partition on it
[*]Let The Ubuntu install program install onto it.
[*]Remove the CD-ROM and try to boot from the flash disk.
[/LIST]

If the flash disk fails to boot, do this:
[LIST]
[*]Boot from the install CD-ROM again
[*]Select "start without modify computer" (or whatever it is named)
[*]Insert the flash disk
[*]Open a terminal
[*]```
sudo apt-get install syslinux
```
[*]Mount the ext2 partition on the flash disk in /media/usbdisk
[*]```
sudo extlinux -i /media/usbdisk/boot
```
[*]Create a syslinux.conf in /media/usbdisk/boot and point out the kernel and initrd.img
[*]```
sudo -i
```
[*]```
cat /usr/lib/syslinux/mbr.bin > /dev/sda
``` (or whatever device your flash disk uses)
[*]```
exit
```
[*]Remove the CD-ROM and boot from the flash disk.
[/LIST]

---

### Post by patrickaupperle on 2008-07-18
> **mikaelstaldal said:**
> Have a look at its homepage:
[http://syslinux.zytor.com/wiki/index.php/EXTLINUX](http://syslinux.zytor.com/wiki/index.php/EXTLINUX)

The SYSLINUX package is available for Ubuntu, just do:
```
sudo apt-get install syslinux
```

Do like this:
[LIST]
[*]Boot from the Ubuntu install CD-ROM
[*]Insert the Flash disk you want to install to
[*]Select the flash drive during install and create one big ext2 partition on it
[*]Let The Ubuntu install program install onto it.
[*]Remove the CD-ROM and try to boot from the flash disk.
[/LIST]

If the flash disk fails to boot, do this:
[LIST]
[*]Boot from the install CD-ROM again
[*]Select "start without modify computer" (or whatever it is named)
[*]Insert the flash disk
[*]Open a terminal
[*]```
sudo apt-get install syslinux
```
[*]Mount the ext2 partition on the flash disk in /media/usbdisk
[*]```
sudo extlinux -i /media/usbdisk/boot
```
[*]Create a syslinux.conf in /media/usbdisk/boot and point out the kernel and initrd.img
[*]```
sudo -i
```
[*]```
cat /usr/lib/syslinux/mbr.bin > /dev/sda
``` (or whatever device your flash disk uses)
[*]```
exit
```
[*]Remove the CD-ROM and boot from the flash disk.
[/LIST]
Thank you. Is that completely safe for my hd and usb? I won't accidentally screw up my mbr or something stupid will I?

---

### Post by jimv on 2008-07-18
I just installed Hardy on my 4gb thumbdrive yesterday.  I booted from the CD, opened the installer, chose my thumbdrive, and hit install.  It worked just fine.

NOTE:  On the last screen before doing the install, click the advanced button and tell it to install GRUB onto the thumbdrive, not your HD.

---

### Post by Pumalite on 2008-07-18
Before you reboot; edit /boot/grub/menu.lst and make 'groot' and 'root' (hd0,0)

---

### Post by patrickaupperle on 2008-07-18
Thank you everyone, I will be trying this soon.

---

### Post by mikaelstaldal on 2008-07-20
> **patrickaupperle said:**
> Thank you. Is that completely safe for my hd and usb? I won't accidentally screw up my mbr or something stupid will I?

It will alter the MBR of the USB flash disk, but it should not affect your HDD.

(Each disk, also USB flash disks, has an MBR.)

---

