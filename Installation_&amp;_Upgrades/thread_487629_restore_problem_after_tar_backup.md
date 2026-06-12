---
title: "restore problem after tar backup"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by graphicgolem on 2007-06-29
Does anyone know where I have might have gone wrong in following?

I have Fiesty and Winxp dual boot setup with each OS on separate hard drives. The / and /home are on separate partitions on primary (hda). 

I have backed up my / system with tar. The /home folder is backed up to another tar. I used heliode's guide: [http://ubuntuforums.org/showthread.php?t=35087&highlight=heliode](http://ubuntuforums.org/showthread.php?t=35087&highlight=heliode)) to make the archives.

To test the backup I swapped in a new formated identical primary HD and installed from the Live CD with an identical partition structure. I then copied by tar backup to the / of the system and extracted it. On rebooting the dual boot seems to work fine and I can select Fiesty, and shows the latest release in the boot menu list-which seems to indicate that the tar has extracted properly to the / of hda. However the splash loader hangs on the start of progress bar. I am thinking maybe the /home tar needs to restored as well because the / system doesnt recognise the settings in /home? 

Any ideas about how to solve this would be gratefully received. Thanks.

---

