---
title: "ASUS P5W DH Ubuntu 7.04 Solved!"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by _max_ on 2007-05-10
Long version:

After trying to installl Ubuntu 7.04 beta releases for ages, but failing every time the only thing i could run was Ubuntu 6.10, and barely that, it ran really badly on this crap motherboard.

My personal opinion is if you havn't already bought it, dont! its a friggin hack for a motherboard, the problem resaults in that they have taken one of the 4 ICH8 s-ata ports and hacked a bus onto to it leading to a "EZ BACKUP" chipset, its basicly a poor chip that automagicly creates a raid1 when 2 drives are attached, creating simple redundancy so you wont loose files.

however when ubuntu installation tries to probe /dev/sdb it borkes out, since its expecting a hdd or alike, but finds some voodoo chip.

I tried both Ubuntu 7.04 i386 and amd64 with no luck, suddenly i got the idea to plugin a 40gb s-ata disc i had laying around in the friggin ez-backup port, (just one disc, didn't create the raid1). and voila.. it works! flawlessly.

Short version:
So to get this motherboard working with 7.04 Feisty i386 you need to plug a hdd (that wont be usable) into one of the EZ BACKUP (orange) connectors.

I currently have 3x320gb hdd's on the ICH8R chipset, and a 40gb seagate s-ata disc on the EZ BACKUP circuit and installation goes through perfeclty without hicups.

---

### Post by Syirrus on 2007-05-10
Right on, I will have to try that.  When I tried installing I get he infamous I/O error halting my system instantly.
Syirrus

---

### Post by MCSE_Crossover on 2007-06-13
appending "irqpoll" to the end of the kernel boot parameters also seemed to fix the instability issues...although I am unclear what effects using IRQPOLL actually has. I have a post out there regarding it, but no one has replied unfortunately. to me, it seemed that when I had irqpoll in the boot paremeters, my data transfers between the sata drives were significantly slower - but I could just be crazy.

---

### Post by jdude1284 on 2007-12-16
You aren't crazy.

IRQPOLL means that the kernel will not use DMA when transferring data to or from the device but will POLLED I/O instead.

At a highlevel, DMA basically frees the processor from having to shuffle data from disk to RAM -- the disk controller puts the data into RAM then raises an interrupt (pokes the kernel) and says "HEY that data you wanted is over in ram at location X"

Polled I/O , again at a high level, disables that. So instead the processor has to walk around asking the device if it has more data that it wants to hand off.

The problem with polled I/O is *usually* that the amount of data that is transfered is EXTREMELY small. 

So in DMA, the device could say "here is 16mb of the data you wanted"

whereas in polled I/O, the processor will be like "ok give me 8 bytes of data now" - over and over and over again sucking up CPU, slowing the transfer rate, and making your life pain and suffering.

If possible - avoid IRQPOLL like the plague.

---

### Post by chill on 2007-12-30
I am unable to install 7.10 on my new Asus P5W DH Deluxe.

But, let me get this right... I can't get it running unless I plug that extra SATA HDD to te ez-backup slot? Rigth?

Anyway. Can't test the hack at the mo 'coz I don't have an extra SATA drive but...

So far I am pretty disappointed that can't install Ubuntu 7.10 on my new PC.

--
EDIT:
I got it working... did some mambojambo in BIOS and sucessfully installed the 7.10

---

### Post by cometcomputing on 2008-01-07
Can you let me know the exact settings you used to be able to install Ubuntu on this board? Also did you use the 64bit or 32bit version of Ubuntu?

---

