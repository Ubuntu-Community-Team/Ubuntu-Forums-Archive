---
title: "Stalls at ata1.01 on initial boot up"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by TheSauce on 2010-03-03
I have a machine running Windows XP.  I have my DVD-ROM as Primary master, my main hard drive as Primary slave, and another hard drive as Secondary master.

I have installed Ubuntu 9.10 within Windows XP using wubi.  After it finishes installing it tells me I need to reboot.  If I try to boot into Ubuntu it stalls.  I then tried Verbose mode and the last three lines on the screen are as such:

ata1.00: ATAPI: TSSTcorpCD/DVDW SH-S182D, SB03, max UDMA/33
ata1.01: ATA-6: WDC WD2000JB-00GVA0, 08.02D08, max UDMA/100
ata1.01: 390721968 sectors, multi 16: LBA48

So, last time I tried to install Ubuntu with wubi (8.04) it would stall after the exact same drive except back then I had three hard drives in my system and the Western Digital drive was on my Secondary slave.  If I disconnected it then it would boot up fine.  Before installing this time I imaged my C: drive onto the Western Digital drive (because it was bigger) and got rid of my original C: to see if maybe it didn't like having four IDE devices (strange, I know, but I figured I would rule that out).

So, now it seems that it doesn't like the Western Digital drive for some reason but I have no idea why.  I can't try removing it again because it's the drive that Ubuntu is installed on.  Does anyone have any suggestions of things to try?  I'm fairly new to Linux but I know my way around a computer.

Thanks,
Jared

---

