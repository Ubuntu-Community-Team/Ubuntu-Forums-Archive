---
title: "Bugs in 7.04 Install"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by Howard Kaikow on 2007-06-03
On a multiboot Windows 2000 system, I decided to imstall Ubuntu 7.04.

I ran into the following, which seem to indicate some bugs in the install process.

I created some unallocated space on a SCSI drive and allowed Ubuntu to format an ext3 for / and a linux swap partition.

I specified that the GRUB loader was to go into the first sector of the ext3 partition, not in the MBR, so I specified /dev/sdc10 for the GRUB installation.

I then used dd to get a copy of the GRUB loader, and placed that copy on the C drive, modifying boot.ini accordingly.

Wel. I got GRUB GEOM errors.

After much discussion, a workaround was discovered by Adrian at [Hardware Guys Forum]("http://forums.hardwareguys.com/ikonboard.cgi?act=ST;f=21;t=5731;st=40").

The first problem was that the install had incorrectly referred to hd3, when it should have referred to hd2, in menu.lst.

Using LiveCD or SGD, I forget wich, I was able to edit menu.lst, and then boot to my Linux using the SGD.

However, I still could not get to Linux thru the NT boot menu.

Adrian came up with the following (quited from Hardware Guys):

```
Boot your Linux distribution.
Open a terminal
$ sudo grub
type your password
grub> device (hd0) /dev/sdc
grub> device (hd2) /dev/sdc
grub> root (hd2,9)
grub> setup (hd0,9)
grub> quit
$ sync
$ reboot

Once rebooted... boot again your Linux.

Make that dd thing... and get yourself your partition boot sector. Something as:

$ sudo dd if=/dev/sdc10 of=/path/to/win/boot.lnx count=1 bs=512

Edit boot.ini if needed so that it chainloads the boot.lnx file.

Boot into Windows and select Linux.
```

It would seem this this is a rather convoluted process, necessitated by bugs in the 7.04 install.

How does one avoid this problem?
Is Adrian's solution the only way to get arond this?

---

### Post by Howard Kaikow on 2007-06-13
I have added a new hard drive, to which I again installed Ubuntu.
In this case, the trick used in te previous post did not work.

Why?

The cause is the programmers of the LiveCD not taking into account that the order of the ennumeration of drives is not predetermined. In some cases, the SCSI controller ennumerates first, in other cases, the USB controller ennumerates first. Proper prograamming would take this into account.


So during the install, as the USB drives had been ennumerated first, the install was to /dev/sgd.
However, booting with the Super GRUB  CD, one sees tat the install was to /dev/sdd. sdd is correct if the SCSI hard drives are ennumerated prior to the USB drives, but LivecD does not take into account that th ennumeration is not predetermined, whereas, the installed Linux appears to properly take this into account.

---

