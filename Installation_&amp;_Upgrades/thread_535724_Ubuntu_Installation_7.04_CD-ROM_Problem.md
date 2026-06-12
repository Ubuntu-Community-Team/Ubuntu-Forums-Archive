---
title: "Ubuntu Installation 7.04 CD-ROM Problem"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by emnahirn1 on 2007-08-26
I am trying to install Ubuntu 7.04, on an older P3 based system.
- VIA Chipset
- ASUS CU4VX Motherboard
- 768 MB RAM
- 80 GB HD
- CD-ROM/DVD-ROM

I get the following error after booting the Server Edition of Ubuntu from the CD-ROM, and into the installation sequence.

"Your installation CD-ROM couldn't be mounted. This probably means that the CD-ROM was not in the drive.
Try again to mount the CD-ROM?" 

I have validated the CD-ROM, and the iso image to ensure the quality of the CD-ROM.  I've noticed a number of other posts with the same problem, with inconclusive results.  Would appreciate any suggestions to try and get the install to work.

---

### Post by Pumalite on 2007-08-26
If you checked your iso, then get in your BIOS and make sure that all the settings for your CD are OK.

---

### Post by emnahirn1 on 2007-08-26
BIOS settings seem to be ok.  I tried all the PIO modes and tried disabling DMA.  All have no effect.  The CD does boot up and the system auto detects the hardware.  The system fails with the following error though when it tries to mount the cdrom part way through.

mount: Mounting /dev/hdc on /cdrom failed Invalid Argument.

There are some old posts in the forum with the same problem, but it looks like its never been resolved?

---

### Post by Pumalite on 2007-08-26
Do you have a floppy in your system?

---

### Post by jporter182 on 2007-10-12
I am having the same problem with a Dell Optiplex GX260, slimline desktop.  I suspected the problem was with the PCMCIA DVD/CD-R drive not being recognized by Ubuntu.  It even gives a suggestion around this for Dell laptops during the install, but it doesn't work for the GX260.  The curious thing is that I can successfully install Fedora 7 on the PC.  I have tried both the Live and Alternate versions of Ubuntu 7.04.  Fedora is ok, but I'd really like Ubuntu, and I'm curious why it won't work.  My PC does have a Floppy drive so I'd like to know what your solution may be.

Thank you.

---

### Post by phr0ze on 2007-10-12
The first suspect if the controller the CD rom is on. If it's one with raid capabilities, then I suggest you change the cable to another controller, or find the drivers.

---

