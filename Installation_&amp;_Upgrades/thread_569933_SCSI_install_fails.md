---
title: "SCSI install fails"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by FrankVdb on 2007-10-07
I'm trying to install Ubuntu on a server system involving several types of drives. I've been trying for about two days now and it is driving me nuts.

My rig consists of two Samsung IDE drives in a traditional IDE master and slave setup, a Seagate Cheetah SCSI drive connected to a SCSI card, and a Maxtor IDE drive I've had to connect to an SATA slot using a PATA-to-SATA adapter because the cable from the CD/DVD reader is not long enough to use its second IDE plug...


Now, I'm trying to install Ubuntu on the Cheetah, which as I said is connected to a SCSI card. I discovered that my BIOS fails to see the SCSI drive, which is obviously why Grub is giving me an Error 21 when booting up.

I've been reading for hours about SCSI BIOS, RAID alternatives, LBA, etc. but none of this is offered by my BIOS.

I'm not sure if it's relevant but the motherboard is an Asus P8P800 SE. 

Btw, the drive connected to the motherboard through the PATA-to-SATA adapter goes unnoticed as well.

My first priority would be to get the SCSI drive going. Any enlightened souls in the room?

---

