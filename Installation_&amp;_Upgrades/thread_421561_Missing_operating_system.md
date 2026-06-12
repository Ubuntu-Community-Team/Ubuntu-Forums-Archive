---
title: "Missing operating system"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by likerice on 2007-04-24
newbie here.

i attempted to upgrade from edgy to feisty last evening but ran into GRUB problems. not wanting to mess with GRUB, i decided to simply "wipe" my drive and install feisty fresh from dvd, thereby writing over my previous kubuntu and windows partitions. now, after installing feaisty, and upon reboot, i'm confronted with a "Missing operating system" message, presumably from GRUB.

i've scoured the web for solutions, but most advice seems related to the rescue of existing dual-boot systems. all prior existing partitions have been obliterated on my system (my important data was backed up, of course). all i want now is to install feisty, fresh from dvd.

can anyone help, please?

thanks!

---

### Post by psusi on 2007-04-24
Sounds like grub did not get installed at all.  That message usually comes from the bios, or maybe it was the msdos boot sector -- I forget.  

Either try then install process again or manually install grub.  How did you install in the first place?  Using the desktop cd?  How did you partition the drive?  One big root using ext3?

---

### Post by mannukio on 2007-09-24
> **psusi said:**
> Sounds like grub did not get installed at all.  That message usually comes from the bios, or maybe it was the msdos boot sector -- I forget.  

Either try then install process again or manually install grub.  How did you install in the first place?  Using the desktop cd?  How did you partition the drive?  One big root using ext3?

Hello! I installed a XUbuntu on a SATA 250GB hd and, after reboot, says "Missing Operating System". I install it with a large root partition. Now i started the Desktop-Disc and mounted the large ext3 partition, and the GRUB appears to be configured.

Any clues?
Thanks

---

### Post by psusi on 2007-09-24
Do you have more than one disk?  What is the output of sudo fdisk -l?

---

