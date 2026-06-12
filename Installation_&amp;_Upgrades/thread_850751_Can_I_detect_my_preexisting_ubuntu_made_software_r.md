---
title: "Can I detect my preexisting ubuntu made software raid with a new install?"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by Squish on 2008-07-05
Hey so I have a desktop.

I had installed ubuntu studio alternate edition, and set up a 2 terrabyte raid 0 software raid using the ubuntu installer. Because I need a 32 bit, I did a re install of ubuntu 8.04.1, however my friend forgot to download me the alternate installer. So I installed my system on a singular 250 gb using a live desktop enviroment (thus no raid options).

Now i have this installed system, but I cannot detect my raid 0 despite it being made with a linux raid. 
Its mount point was /home/Video
Is there anyway I can redetect it?

---

### Post by vpsville on 2008-07-06
If you formatted or created partitions on the same disk that held part of the RAID 0, then its gone forever.  If you wrote files to the disks that had the raid partitions you're probably screwed as well.

If it was on another disk from your new install then the installer can detect it and resurrect it.  

You can also try using the same install disk that you used to create the raid in the first place, that will have the best chance of seeing the partition.

---

### Post by sdennie on 2008-07-06
If you are sure you've haven't overwritten part of your RAID array, this might help you: [http://ubuntuforums.org/showthread.php?t=850229](http://ubuntuforums.org/showthread.php?t=850229).

---

