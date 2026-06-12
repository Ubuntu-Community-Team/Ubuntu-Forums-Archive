---
title: "Installation of a persistent system to USB thumb drive"
date: 2011-11-29
forum: Installation &amp; Upgrades
---

### Post by TaleRix on 2011-11-29
Hi guys,

I need some help installing a version of Kubuntu (11.10) to a USB flash drive.

I started the installation using the Startup disk creator utility, resized (created) the persistence partition using Gparted... all went thru as expected. However when I get to the installation part after rebooting the system and booting from the USB drive, the install only gives me the option to install the system to my HDD (SCSI 500gb).
The flash drive is in but the install program doesnt recognize it. I tried fdisk -l and the USB drive is detected. Then I tried mounting the USB drive to some dummy folder but the install still doesn't detect it.

What can I do??

Thanks a lot!:confused:

---

### Post by TaleRix on 2011-11-30
OK, I managed to find a fix to this; maybe it'll be useful to someone else.

I tried to install the thing via Startup Disk Creator- to no avail, it only let me an option to install it on my HDD.

I then booted from a live CD. I tried to install it via the Install option - same result as the above. I then booted it again, clicked on Try Kubuntu. I mounted my USB flash via the GUI and then clicked on Install. Amazingly then the USB flash was listed among the install target options and I managed to install it there. :guitar:

---

### Post by Megaptera on 2011-11-30
Thanks for sharing!

---

