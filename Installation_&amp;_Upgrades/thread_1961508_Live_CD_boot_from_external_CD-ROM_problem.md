---
title: "Live CD boot from external CD-ROM problem"
date: 2012-04-19
forum: Installation &amp; Upgrades
---

### Post by erable on 2012-04-19
Hi,

My (old) system no longer boots from the integrated CD-ROM drive since quite a while. The drive is operational otherwise, i.e. it is recognised by the system and disks are readable. 
I can boot from an external CD-ROM drive connected via one of the USB 1 ports.
Trying to boot several live CDs (Ubuntu, Lubuntu, Gparted, ...)always failed until - by pure luck - the native drive contained also a copy of the live CD I was booting with from the external drive.

The linux load process seems to be oblivious to the initial boot drive and happily completes the load accessing both drives.
At least I can bring up Ubuntu etc. but it ain't very elegant.

I thought it worthwhile to signal this.

Regards from

an absulute linux beginner

---

### Post by mastablasta on 2012-04-19
what does failed mean? can the BIOS boot from USB? Does the BIOS know you have external drive or are certain drivers necessary to install it/get it recognised.

---

### Post by erable on 2012-04-20
Hi,
Thank you for your interest in helping me out and sorry I wasn't clear enough.

The BIOS does not explicitly show USB as one of the boot options, but I can boot from an external CD-ROM drive connected to the USB1 port. Booting from a USB1 pen-drive doesn't work but maybe HP can help me getting a proper Bios version other than the current revision KAM1.16.

The 3 boot options I have in the Bios are "removable media" (I guess this covers floppy & USB), "CD-ROM" and "Hard drive".

Anyway, when I boot Ubuntu from the live-cd in the external CD-ROM drive I get as far as the _**UBUNTU .....**_ screen.

After a while I get:

[I]Busybox V.1.18.4 etc...
(initramfs) unable to find a medium containing a live file system[/I]

My interpretation is that at this point in time linux wants to access a live file system on the native CD-ROM rather than using the one present in the external drive used to boot. 
When I put a second live-cd in the system's CD-ROM drive the boot completes. At some points in time both drives seem to be active.

Hope this is clear enough.
Cheers,
Erable

---

