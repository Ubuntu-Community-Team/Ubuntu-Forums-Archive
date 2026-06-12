---
title: "Install/Installed Hangs/Dumps To Console"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by 290 on 2007-02-13
AMD Opteron 165
2GB DDR 4400
DFI CFX3200-DR
2x WD Raptors SATA
Lite-On CD/DVD
ATI X1900 A-I-W

Ubuntu 6.10 x64

First id like to say i love Ubuntu. Ive been trying linux on and off for years and this is by far the easiest to manage so far which is why ive installed it as my main OS on my laptop (Dell Latitude c610). But now i want to do the same to my main rig listed above. The problem im having is that the install hangs when detecting my SATA drives:

ata1: SATA link up 1.5 Gbps (SStatus 113)
ata1: dev 0 ATA-6, max UDMA/133, 145226112 sectors: LBA48
ata1 dev 0 configured for UDMA/133
scsi0 : ahci
(to save type ata2 gives same)

Heres where the problem starts

ata3: SATA link down (SSatus 0)
ata3: dev 0 failed to IDENTIFY (I/O error)
scsi2: ahci

Hangs here for a good 5min or so then moves on to ata4 and hangs another 5min or with the same thing. I dont have anything pluged into sata ports 3&4 and are marked as Not Installed in the BIOS

Now it moves on with booting and hangs again here:

Begin: Waiting for root file system... ...

Its will hang here for a while then error with this:

ALERT! /dev/hda1 does not exist. Dropping to a shell!

Then it dumps me there.

Ubuntu 6.10 i386

Detecting SATA goes the same as above with ati3&4 stalling the install/boot

However now i get this when booting the install disc:

hda: command error: status=0x51 { DriveReady SeekComplete Error}
hda: command error: error=0x54 {AbortedCommand LastFailedSense=0x05
ide: failed opcode was: unknown
end_request: I/O error, dev/hda, sector 1430256
Buffer I/O error on device hda, logical block 357564
ide-cd: cmd 0x3 times out
hda: lost interrupt

this happens over and over again then eventually moves on with the install like nothing happened. Any help would be nice id like to get Ubuntu running on my desktop. Thanks

Dan

---

### Post by teaker1s on 2007-02-17
search forums for raid or array, secondly you will need to sort out driver for ati card as from forum postings it's not working straight out the box

welcome to forums

---

