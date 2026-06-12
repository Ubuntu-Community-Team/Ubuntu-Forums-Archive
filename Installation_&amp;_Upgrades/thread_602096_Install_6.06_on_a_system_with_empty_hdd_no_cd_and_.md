---
title: "Install 6.06 on a system with empty hdd no cd and no loppy drive"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by spraygun on 2007-11-03
Hi,

I have quite a problem. I want to install Ubuntu on a 133mhz 16mb ram laptop, that has no floppy and no cd drive and no usb. But an pcmcia network card

I have an Adapter so i can copy files to the laptop HDD. I downloaded the alternate CD and copied it to a seperate partition on the hdd.
My plan was to somehow install grub on the hdd and then make an entry to start the alternate-cd-partition. But how do I install grub on that hdd. I already tried /usr/sbin/grub-install /dev/sda1 but it said that there was no BIOS corresponding to that drive.
 
Does anyone know a way to do that or a better way to get ubuntu on that laptop?

I already created a swap partition with 512 mb and the alternate-cd-partition. Now there is only 800mb left. Will that fit anyway? 

Thanks in advance
spraygun

---

### Post by zvacet on 2007-11-04
You have just 16MB of RAM,wich is not enough to install Ubuntu.

---

