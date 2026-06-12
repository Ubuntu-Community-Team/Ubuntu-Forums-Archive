---
title: "gutsy install problems - ata_piix driver dies"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by jdude1284 on 2007-10-18
Hi - 

I am installing gutsy on an *old* server system [an Acer Altos G610]. The specs are roughly:
pentium 3,
adaptec scsi adapter with 1 scsi disk,
a tape drive, 
a floppy, 
and a cdrom drive. 

I am using the alternate installer and doing a text mode installation. The installation starts fine, I select the keyboard layout and the installer attempts to pull some data from the CD-ROM drive.

Then, without warning, gutsy displays an error dialog that it cannot read from the cd-rom. 

When I check my dmesg, I notice that gutsy is complaining about ata1 being too slow to respond. The device is not ready, a hard reset is issued, then a slow reset and the drive fails to identify.

This happens several times until it just gives up. 

The older (and now deprecated) piix driver worked perfectly for me before on this system - the new ata_piix driver does not.

I've seen lots of threads on the forums about this, but no conclusive answer has been found. 

This issue is also seen on a more modern core2 system with a p5w dh deluxe (my other computer). 

Any advice at all on how to get that ata_piix driver to be happy?

Thanks.

---

### Post by jdude1284 on 2007-10-19
A shameless bump.

---

### Post by jdude1284 on 2007-10-25
Shameless bump 2.

---

