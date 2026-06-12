---
title: "install Feisty without rewriting MBR (keep using NT Loader)"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by nothingworks on 2007-04-23
I have 4 hard drives, two on ide0 (80GB,200GB) and two (120GB, 120GB) on a PCI ULTRA66 controller card.

On one of the 120GB drives I made two new primary partitions (10GB for root,1.5GB for swap) using acronis disk director suite.

Currently I have XP Pro installed on the 80GB HDD.

So i installed fiesty and at the last setup page, just before clicking "install", I chose to have grub installed on /dev/hde3  (the  primary partition where feisty was installed, 10GB)

I then added a new entry into ntloader's boot.ini using bootpart.exe (I've done this several times in the past with no issues (fedora,suse))
During boot, choosing to boot feisty causes a "No operating System found, Please insert system disk and press any key" error.

My questions:
1) why is there still no option to install grub on a partition rather than on the MBR of the primary HDD ?
     I feel this is critical since 90%+ of users are coming from a windows world and want to try Ubuntu.
2) What did I do wrong ?  XP still works. 
     Can someone who has done this provide some insight?

thanks

---

### Post by rich.bradshaw on 2007-04-23
why do you want to? Grub will allow you to boot Windows automatically?

I think that the "Alternative Install CD" lets you do it differently.

---

### Post by nothingworks on 2007-04-23
I'm trying to keep NT Loader so that I can install vista in the future.
Note that Feisty did not detect XP (no option to choose boot options), and the migration screen was blank.

I'll try the alternate cd, last time i tried it was too intimidating.

---

### Post by nothingworks on 2007-04-24
The problem must be because of the Promise UltraAta66 controller card.

I'll try installing Feisty on one of the HDDs thats connected to the motherboard IDE ports......

---

