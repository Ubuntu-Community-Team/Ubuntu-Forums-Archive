---
title: "Unable to boot live/alternate CD for 7.04"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by MemoryFault on 2007-08-17
Hi,

I just decided to try returning to Linux after a foray into the world of OS X and have been trying to install 7.04 onto a 3yo AJP laptop. I've got a problem with hardware detection with the installer not being able to detect the CD-ROM. I've tried most things from my googling (noacpi, nolacpi, acpi=force, irqpoll etc in various combinations) but I'm kiinda stumped as to what to try next.

The machine specs are:
80G Fujitsu HD
Intel 8280 1FBM Ultra ATA controller
Ricoh R/RL/5C476(II) PCMCIA controller
TSSTcorp CD/DVDW TS-L532A DVD rewriter
Intel Pentium M proc @ 2Ghz.
Nvidia GdForce Go 6600 graphics

Any help would be appreciated...

---

### Post by merlinus on 2007-08-17
The cd or drive may have defects, or it was not burned correctly.

Also, make sure your machine is set to boot from the cd drive before the hdd.

Perhaps you can test the disk in another computer.

-merlin

---

### Post by MemoryFault on 2007-08-17
Both ISOs were verified as correct and it's definitely booting from the CD before the HD (the system was supplied with XP pre-installed). When I try the alternate boot CD, it gets as far as CD-ROM detection, then stops telling me that it can't detect it. I'm sure it's something strange with the brand of laptop. Ubuntu seems to want to install a floppy disk driver, but there's no floppy in the machine. PCs seems like a nightmare of arcane designs...

---

### Post by dabl on 2007-08-17
> **MemoryFault said:**
> 

 PCs seems like a nightmare of arcane designs...



Yeah, there's some truth in that!

Is that optical drive IDE/PATA or SATA?  In your BIOS settings for that drive, you may have some choices in the "mode", and you probably need to try some of the alternate settings (but don't forget what its present mode setting is!). :)

---

### Post by MemoryFault on 2007-08-18
The drive is IDE according to the BIOS (v2.56 AMI). Oddly, the BIOS reports the HD as Primary Master and the DVD as Secondary Slave - and there doesn't seem to be much in the way of control via the BIOS. All I can change is the PIO Mode (currently Auto) and DMA mode (also auto).

---

### Post by dabl on 2007-08-18
> **MemoryFault said:**
> The drive is IDE according to the BIOS (v2.56 AMI). Oddly, the BIOS reports the HD as Primary Master and the DVD as Secondary Slave - and there doesn't seem to be much in the way of control via the BIOS. All I can change is the PIO Mode (currently Auto) and DMA mode (also auto).

If you can change the DVD to "Primary Slave" that might (or might not) help it boot the installation CD.  If that doesn't do it, then go crazy and set the DVD as "Primary Master" and the HDD as "Primary Slave".  Don't forget to verify your boot sequence in BIOS, which needs to have the DVD drive as the first boot device.

---

### Post by MemoryFault on 2007-10-12
Thanks. And sorry for taking so long to get back - I've had to start using the laptop as a PC thanks to some windows only drivers that I need. Ubuntu plans have had to go on hold :(

---

