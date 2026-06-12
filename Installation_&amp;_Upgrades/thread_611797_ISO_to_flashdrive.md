---
title: "ISO to flashdrive"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by elvinatom on 2007-11-13
I want to write a bootable image to a memory stick (/dev/sdb1) ... tried wodim, but it only writes to CD/DVD; in fact no burner-software I tried supports usb-sticks. What tool can do that (ISO or IMG => Flashdrive)?

---

### Post by solar george on 2007-11-13
You do not write an ISO to a flash drive - to make it bootable you must use a boot loader similar to on a hard drive. You will have to google for a howto.

---

### Post by elvinatom on 2007-11-13
Thank you for the reply,
I don't dispute what you say, but I find it a little strange.  I remember that about half a year ago I took a fedora core iso image (maybe 20-30MB) of the net and followed some instructions how to get that to the flashdrive (in order to initiate an internet installation).  That worked just fine and I thought that could be done with any bootable iso therefore.

---

### Post by solar george on 2007-11-13
Hmm,

```
dd if=*path to image* of=/dev/*usbdisk*
```

I think.

---

### Post by elvinatom on 2007-11-13
That rings a bell - thank you, I'll try that right now!

---

### Post by elvinatom on 2007-11-13
Absolutely fabulous!
Worked like a charm!

---

### Post by solar george on 2007-11-13
[SIZE="4"][COLOR="Red"]A warning to anyone who tries this - It will erase all data on your USB Disk[/COLOR][/SIZE]

---

### Post by Superdelphinus on 2007-11-13
Hello

I think i'm trying to do the same thing! 

I have an iso image of 7.10, windows xp and a blank 2gb usb memory stick. Could someone give me easy steps to make it load the iso when i boot the computer (i've already set the bios)..

Thanks

---

### Post by solar george on 2007-11-13
Try googling for it.
I can't help as the dd method requires a working linux as do any others I  can think of although [this]("https://help.ubuntu.com/7.04/installation-guide/i386/") may help.

---

### Post by kelvin spratt on 2007-11-13
use this [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
it give details of how to to it. u end up with a persistant gutsy on a pendrive if use follow the linux link that means you can save all your changes and it does work may take a few attempts to get it right the first time, i personally used gparted live for the partitions making the 1st a bit larger 900mb. and the rest of a 4gb stick for 2 partition.Then picked up from step 8.

---

