---
title: "Can't install dapper to boot from USB HD"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by awperk on 2007-03-10
I have a laptop that has a 60gb internal hd that i need to leave relatively intact. I want to be able to run ubuntu on my laptop but boot from my usb. I can't even get the installation to begin because it says that there isn't enough space for the installation. I know thats not true because i have dapper installed on a desktop on a 20gb partition and the usb drive has 233gb of free space. I can't write to the disk on ubuntu because it says it is read-only. The usb drive reads/writes on windows. I'm thinking the fact that it wont allow me to write is halting the creation of a partition during installation. I'm desperate because i'm going away tomorrow for 2 months and want to be able to take ubuntu with me.

---

### Post by awperk on 2007-03-21
Just as a follow up, i got my laptop to boot perfectly from my ext hard drive. I had to make sure it was ejected and not mounted anywhere before starting the installation. After that it was as basic as following the graphic installation on the liveCD. One thing to keep in mind is to make sure you are only partitioning your external drive and not the internal one. I even went back after the installation and used a Gparted liveCD to reformat my partition with all my data on it (after backing it up on my fixed hard drive) to FAT32 so that i can now read and write from both windows and ubuntu. I couldn't be happier because after reordering the boot list in BIOS to have my USB drive boot before my internal drive, all i have to do to boot in linux is turn on my ext. hard drive.

---

### Post by dcstar on 2007-03-21
> **awperk said:**
> Just as a follow up, i got my laptop to boot perfectly from my ext hard drive. I had to make sure it was ejected and not mounted anywhere before starting the installation. After that it was as basic as following the graphic installation on the liveCD. One thing to keep in mind is to make sure you are only partitioning your external drive and not the internal one. I even went back after the installation and used a Gparted liveCD to reformat my partition with all my data on it (after backing it up on my fixed hard drive) to FAT32 so that i can now read and write from both windows and ubuntu. I couldn't be happier because after reordering the boot list in BIOS to have my USB drive boot before my internal drive, all i have to do to boot in linux is turn on my ext. hard drive.

Your Grub menu should also have your Windows system as a boot option, if it doesn't you should be able to manually add it in fairly easily (do a forum search for detailed instructions).

---

### Post by Sonic Reducer on 2007-03-22
i had a similar problem with a 120GB western digital passport, WD has an app on their webpage that writes all 0's to the drive. i did a complete wipe and ubuntu installed beautifully, its what i'm typing right now.

don't forget to set your boot priority so a USB HDD is above the first HDD. i got it set so whenever i plug in the drive and reboot it goes straight to ubuntu, boot without the drive and windows loads fine

---

