---
title: "Simple Backup Suite (sbackup) produces no backup."
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by Nibinaear on 2010-06-26
My second issue with backing up my system is when using Sbackup. I've set the folders I'd like to backup, clicked save, then Backup now. A dialogue is displayed telling me that the backup is initiated in the background with process ID x. But if I look at the process list using the top command or using system monitor then that process is not there. I've waited for about half an hour but no backup has appeared in the chosen directory and there is no hard drive activity. What's up with sbackup?

**Edited**

Have since found this post which was quite useful: [http://wwww.ubuntuforums.org/showthread.php?t=1480520](http://wwww.ubuntuforums.org/showthread.php?t=1480520)
I tried the fix by recluse but no look. Will try command line suggestion next. Any other suggestions welcome.

---

### Post by waynemeat on 2010-06-26
Are you trying to backup system folders?
I use a program called Back In Time. Haven't had any problems with it.

---

### Post by Nibinaear on 2010-06-26
> **waynemeat said:**
> Are you trying to backup system folders?
I use a program called Back In Time. Haven't had any problems with it.

Not really, just trying to backup my personal folders before a format of the hdd. Also trying to backup a list of my installed software (see other topic by me).

---

### Post by Nibinaear on 2010-06-27
bash

I'm not really very good with the command line so I don't know how to use the sbackupd function. I had a look at the man sbackupd page but I find the descriptions of all the different uris confusing. I had a look on google for info but found no good explanation of how to use it.

**Edited: **The sbackup program seems to be working again now. Perhaps it was the fix by recluse in the link I posted, maybe it just needed to be flushed through at some point. Also for anyone else, don't set the backup directory to the desktop as you won't see the backup file, the file seems to look like this (please can someone confirm this is the backup file?:

2010-06-27_14.05.56.837044.ubuntu.ful

---

