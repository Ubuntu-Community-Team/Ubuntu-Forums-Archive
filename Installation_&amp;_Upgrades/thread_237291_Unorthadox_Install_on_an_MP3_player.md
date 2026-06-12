---
title: "Unorthadox Install on an MP3 player"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by chuckdsanders on 2006-08-15
Alrighty, well I have an Archos Gmini 120 MP3 player.  For those of you that aren't familur with this beast, it is a 20 gig hard drive based MP3 player that works just like an external HD.  So here is the catch, I need to have a FAT32 partition as the first partion so the MP3 player functionality still works, and then create a 2ndary and 3rd partition for the root and swap partion.  Atleast that is my impression.  So I go through the live CD, make the partions as listed above, or rather 6gig primary partion 1 FAT32, 2nd partion 10gig root ext3, and finally a 2gig swap.  After the instaltion, when booting from the USB, it hangs at the waiting for root mount.  I would like to use this as a pendrive like solution where I can take the MP3 player anywhere, hook it up to a PC and use at as my own portable OS, and still have the MP3 player functionality.  I know I am a picky guy, but I think it would be neat.  Any ideas?  Anyone already done such a thing? Is this like a normal USB HD install?  Thank you for any input that you can offer.

---

### Post by orb9220 on 2006-08-16
Well the first thing I can think that has to be verified is that fat32 really has to be first on usb HD ? If not then it makes the job alot easier.

Search forums on booting from usb and partitioning usb that should help. As  I havn't seen anything that says a usb hd has to have fat32 first. And windows sees my fat32 no matter what partition they are on.

Sorry I couldn't be more help.

---

### Post by chuckdsanders on 2006-08-16
Its not that the HD requires the FAT32 partion to be first, its that the Firmware on the MP3 player requires the first partion to be FAT32 in order to work.  IE, I format the whole drive to NTFS or anything non fat 32, the MP3 player when in MP3 player mode says invalid file system.  When I make multiple partitions, say a 5 gig Fat32 as Partion 1, and then a 10 gig ext3 partition, and then a 1gig swap partion, the MP3 player still fuctions, just no dice on the loading after reboot.  So what do you think? Possible?  Do I just need to change where grub is looking for the boot partion some how?

---

