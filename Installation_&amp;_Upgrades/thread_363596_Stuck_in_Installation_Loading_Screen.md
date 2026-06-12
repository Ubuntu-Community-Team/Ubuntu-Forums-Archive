---
title: "Stuck in Installation Loading Screen"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by psithyrismos on 2007-02-17
Hi,

I just downloaded the image and burned Ubuntu 6.10 i386 on CD. It will boot my CD succesfully but after chosing "run or install" I see the loading screen for the rest of the time.

I watched the installation progress, by turning the splash-screen off and there seems to be something wrong with my CD drives.

```
drives/usb/input/hid-core.c: v.2.6: USB HID core driver
cp: unable to open '/root/var/log/': No such file or directory
Done.

Begin: Running /Scripts/init-bottom...

mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesnt have /sbin/init

Busy Box v.1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh: can't access tty: job control turned off

(initramfs) now thats a shell
(initramfs) hdf: lost interrupt
(initramfs) hdf: lost interrupt
(initramfs) hde: lost interrupt
(initramfs) ide-cd cmd 0x3 timed out
(initramfs) hde: lost interrupt
(initramfs) ide-cd cmd 0x3 timed out
(initramfs) hde: lost interrupt
(initramfs) ide-cd cmd 0x3 timed out
(initramfs) hdf: lost interrupt
(initramfs) hdf: request sense failure: status=0x51 {Drive Ready Seek complete Error }
(initramfs) hdf: request sense failure: error=0x30 {LastFailedSense=0x30}
(initramfs) ide-cd:cmd 0x1e timed out
(initramfs) hde: lost interrupt
```

I turned it off then, because it would repeat the last lines over and over again...

hde and hdf are my CD/DVD drives. I was installing from hdf but no matter what drive I am installing from I always end up lost in this shell. Anyone knows how I can install ubuntu now? :(

And I almost forgot - My System:

ASUS P5W DH Deluxe
Intel Core 2 Duo E6600
4GB RAM

The two drives are benQ and AOpen.

---

### Post by psithyrismos on 2007-02-17
Noone can help me?

I found some other information on the internet that my mainboard wouldnt be supported by the kernel, but that was supposed to be fixed in Edgy Eft so, I still dont know how to solve this strange thing.

I need some help :(

---

### Post by wpshooter on 2007-02-17
Is this the DESKTOP (live) CD version or the ALTERNATE (text based) CD version ?

Have you checked the integrity of your CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Also, have you run the memtest function found on that same menu ?

---

### Post by psithyrismos on 2007-02-17
it is the Desktop version.

I tried the integrity check and the process aborts quite similar:

```
Begin: Mounting root file system ... ...
.
.
.
```


Then there comes a lot of stuff I do not really understand about my drives, about ide-inputs and sata... it ends with the message:

```

.
.
.
hde: lost interrupt
hdf: lost interrupt
hde: lost interrupt
```

But there was also one thing I found quite interesting:
```
irq 74: nobody cared (try booting with the "irqpoll" option)
<c01499a4> __report_bad_irq+0x24/0x80
<01449a9d> note_interrupt+0x9d/0x270
<f930d854> usb_hcd_irq+0x24/0x60 [usbcore]
<c0149323> handle_IRQ_event+0x33/0x60
<c010408a> common_interrupt+0x1a/0x20
<c0105c89> do_IRQ+019/0x30
```

I don't know what it is or if it is of any relevance to this topic though.

I also did the memtest without any error message.

EDIT: I almost forgot. Both CD/DVD drives are connected via SATA.

---

### Post by wpshooter on 2007-02-17
SATA CD drives.  I am GUESSING that that may be your problem.  Seems I may have seen something regarding that on here before.  Try doing an advanced search for SATA CD-rom drive.  I you have an IDE CD-rom drive, try hooking that to the motherboard and disconnect the SATA CD-roms and see if it will test CD integrity and possible install.

Good luck.

---

### Post by Kinslayer on 2007-04-16
I had a problem with long startup & shutdown times.  The problem was my cd rom & dvd rom weren't mounting properly.  They were attached to the same ide cable.  How I fixed it was I shutdown the system, unplugged the cables from each, & rebooted.  It started right up.  Aha.  I shutdown again, which took less than a minute instead of the usual 5-10 minutes.  I connected one drive, started up, & it loaded quickly.  I repeated this with the second drive, with no problems.  A third time with both booted up quickly, and it hasn't been an issue since, at least for the couple of days since I've done this.

---

