---
title: "[SOLVED] Doesn't recognise SATA drive"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by Armaron on 2008-09-12
I'm installing ubuntu 8.04 on a new computer. I just got past the annoying BusyBox interface into the LiveCD part. Now that I want to install it, the partitioner only shows my 250GB IDE harddisk and doesn't show my 1TB SATA disk. I intended to use the IDE disk for backups and to store several types of files. Is there any way to install ubuntu on the SATA drive?

I'm kinda new to ubuntu, so don't go all techie on me.

PC specs:

mobo: Gigabyte GA-EP45-DS3P
gfx card: Gigabyte PCI-e GeForce 9800GX2
cpu: Intel Core 2 Duo E8500
hard disks:
  Western Digital 1TB SATA300
  250GB IDE drive (old one from previous pc)

Thanks for the help!

---

### Post by prshah on 2008-09-12
> **Armaron said:**
>  the partitioner only shows my 250GB IDE harddisk and doesn't show my 1TB SATA disk. 

From Ubuntu 8.04 onwards, SATA drivers are built in; previous versions didn't have them. Windows too had the same issue (no driver recognized in installer) so many manufacturers enable a kind of "IDE" compatibility mode in the BIOS.

You should look in your BIOS for settings related to SATA: Eg; "SATA Native mode", "Legacy Mode", "Compatibility mode", "IDE mode", "RAID" etc. Since this option varies from BIOS to BIOS, there is no exact step to follow. You will have to find a suitable-looking option and play with it. You can post whatever options you think look likely, if you'd like confirmation before doing anything.

This is one possible solution/workaround.

You should also check that the 1TB is recognized fine in BIOS (Eg, no power issues, etc).

Finally, if you can, try getting a 8.04.1 CD.

---

### Post by Armaron on 2008-09-12
Found out I just had to create a new index or something like that. Then it showed up. /blush

---

