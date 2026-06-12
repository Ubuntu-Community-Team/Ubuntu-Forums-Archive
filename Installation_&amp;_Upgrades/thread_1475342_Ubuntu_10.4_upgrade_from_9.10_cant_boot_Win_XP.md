---
title: "Ubuntu 10.4 upgrade from 9.10 cant boot Win XP"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by kdehaven on 2010-05-06
As others have posted, I upgraded from Ubuntu 9.10 to 10.04 & due to the way the installer works, I installed Grup2 to the windows partition rendering it unbootable. I'm attaching a copy of "results.txt" so someone with knowledge can help me repair this mess I made. Windows is partitioned using NTFS and can be mounted from within Linux so I can access the data. Just want to make XP boot AGAIN!!!

---

### Post by quixote on 2010-05-07
Fixing this is actually easy, if you have a windows bootable cd or any windows boot medium.  Boot using that.  Once you're at the command prompt, type ```
fixmbr
```.  That will reinstall the windows bootloader and wipe out grub.

Then you [reinstall grub]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202").  The hardest part is figuring out what linux decides to call the various partitions.  Once you're over that hurdle (which is useful to know in general), it's just a matter of copying files from Place A to Place B.  Come back with your questions if something confuses you.

---

