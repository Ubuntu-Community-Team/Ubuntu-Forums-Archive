---
title: "Xubuntu &amp; old dell - installation hangs"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by Skippy_X on 2007-03-08
I have an old Dell Latitude Cpi D300XT laptop that I picked up on the cheap. It has 300 MHz, 96 megs RAM, 30 gig hdd, preloaded w/ w2k on a fat32 partition. I'm planning on using it as a way of accessing wireless hotspots in town. Living in a *very* rural area relegates me to dial-up (I'm lucky if I get 28k). It seemed to me to be a perfect candidate for Xubuntu.

I downloaded the xubuntu alternate install disk from one of the mirrors, burned the ISO (md5 checksum was OK), and tried to install Xubuntu. I got past the language, country, and keyboard sections. The liebar came up saying the OS was detecting disks. The install stopped at that point. There was a large blue square in the middle of the screen, the cdrom spun, and nothing else happened.

Is there anyone that can tell me what to do at this point? W2K on this machine (w/ zone alarm & avast anti-virus) is s....l....o....w - and I was hoping for a nice, clean fast linux install.

---

### Post by Kateikyoushi on 2007-03-08
You do not have enough memory to run the live disc, you can install from the alternate cd though.

> To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM, when using the Alternate Install CD you can do with 64 MB. 
To install Xubuntu, you need 1.5 GB of free space on your hard disk. 
Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to use at least 128 MB RAM.

---

### Post by Skippy_X on 2007-03-08
I was using the alternate install disc.

---

### Post by Kateikyoushi on 2007-03-08
I see, then try to boot from the cd at the menu press F6 and press E to edit the startupline  then add these options to the end of the line.

noapic
nolapic
pci=irqroute
pci=noacpi
acpi=off
pci=acpi
framebuffer=false
linux irqpoll

---

### Post by Skippy_X on 2007-03-08
OK - that got me further along. 

After inputting that string I got:

[17179590.184000] PCI: Unknown Option 'irqroute'
[17179560.184000] PCI: Unknown Option 'acpi'

Chose the language, selected the U.S. English keyboard, detecting hardware to find CD-ROM drives, scanning CD-ROM (OK), "Loading additional components" - and it now hangs on "Retrieving binutils-static-udeb".

I get a screen reading:

"[! !] Load installer components from CD

There was a problem reading data from the CD-ROM. Please make sure it is in the drive. If retrying does not work, you should check the integrity of your CD-ROM. Retry? (y/n)"

---

### Post by louieb on 2007-03-08
Much as I like Ubuntu.  On a low ram machine like you have I would be inclined to  run Puppy or DSL Linux. Puppy has a nicer desktop and DSL a little better at hardware detection.  
There both made to be used as Live CD and should run in 96 meg. I know both will run from the CD with 128 meg. and both can be installed on a hard drive.   Just my 2 cents worth.

---

### Post by jonthysell on 2007-06-20
The problem is DMA. The installer defaults to using DMA for all drives, and for some ungodly reason DMA won't work on that CD-ROM.

I once had Xubuntu 6.06 running on a Dell Cpi D266XT, but I reformatted at one point and I can't remember what I did. Something along the lines of stopping the boot process to disable DMA.

---

