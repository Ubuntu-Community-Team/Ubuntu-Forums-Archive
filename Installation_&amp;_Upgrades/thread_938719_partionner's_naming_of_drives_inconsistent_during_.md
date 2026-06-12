---
title: "partionner's naming of drives inconsistent during alternate install  messing up grub"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by streamsanddragonflies on 2008-10-05
After having to reinstall hardy with the alternate install DVD, which could I then boot into hardy and chainload windows XP, I noticed that this time the nomenclature for my drives was reversed.  For the first install, my first drive, as is in bios boot order and the ubuntu partitionnner, was sda, my second drive, sdb and my 3rd, sdc.  My  /boot  partition is situated on the first drive which is actually an IDE.   I had succesfully installed grub on sda1 (my first drive) with the ability to boot into hardy.

For my re-install of hardy, the partitionner reversed the order; calling my first drive sdc, my second drive sda and my third sdb.  So when I was asked where to install grub, I opted for sdc1 following the partionner naming scheme as such and it installed.  But when I try to boot into any entry now, I get error 15, file not found or no such partition exists (for my gutsy install).  In gparted, all my installations and data partitions seem to be there but I can't access any of them now!  (My new suse that I installed just before ubuntu, my windows and my gutsy which I had lost the boot path or files).  

I suppose that my boot partition to install grub on, is really on sda1 then, thus ignoring the sdc designation by the partitionner...  Also my IDE is called a SCSI1  (0,0,0) and my second drive SCSI3 (0,0,0)  and my third SCSI3 (0,1,0) .  I hope that these are the right designations by the installer.
  
I should add that it is an alternate install DVD of Ubuntu Studio. Any one can help me confirm that this is where to put /boot after I re-install yet a 3rd time?  I tried recovery but can't re-install grub without renaming and designating all the other partitions, it seems.  I really hope I can be helped becuase I've not used Ubuntu now in weeks and I'm stuck back in windows...

:confused:

---

