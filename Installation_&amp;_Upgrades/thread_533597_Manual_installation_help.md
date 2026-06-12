---
title: "Manual installation help"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by durkhrod chogori on 2007-08-24
I am helping here a friend who wants to install Ubuntu using about a quarter of a 100GB empty drive and I needs the specific codes for a manual install. I mean details for:

1. Swap file
2. Boot
3. Root
4. Home

I know that swap is swap. Easy. I will allocate 256MB to it. No dramas, it is "use as" swap and no need of mount point.

Boot is /boot. Here I'll give 95MB.
Root is /. Here I'll nominate 10GB.
Home is /home. Finally it will take 20GB.

The rest of the 100GB will remain as unused space.

Now my question is specific for the rest of the aforementioned components: boot, root and home. And here I need to know what to type in in"USE AS" and "MOUNT POINTS" for each of those components.

Please list here all these details so I don't muck up the install process.

I hope my question is clear enough.

Thanks a lot for your advice. 

:)

---

### Post by solar george on 2007-08-25
In use as you need to select the filesystem that you will use on the partition.
I would suggest that you use ext3 as it is the default that the automatic installer would have used.

Mount Points,

Home is /home
Boot is /boot
Root is /

Its as simple as that.

---

### Post by Univocal on 2007-12-29
I have XP installed system, i want to make this dual boot, Steps i followed;

1. out of 80 GB disk i create a separate partition for its installation
2. i tried to boot with CD of Ubuntu, when it completely showed desktop to me, then i click install button at desktop

but during installation i do create 

"/" partition with 2 GB space 
"/boot" partition with 2 GB space
"Swap" double to my system memory i.e 2GB


but this shows error that no root mount point is defined... 

CAN anyone explain me about mistake !!!

Regards,
JD

---

### Post by bharadwaj on 2007-12-29
First you need to delete the partition I mean you must keep it raw ulike emtying it in NTFS partition or FAT32. The easiest way to make it raw is insert gparted or windowws installation disc and highlight the partition you want to install Ubuntu and delete it. Then restart and boot the pc ubuntu

---

