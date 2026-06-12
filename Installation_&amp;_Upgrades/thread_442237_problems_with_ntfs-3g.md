---
title: "problems with ntfs-3g"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by rpw on 2007-05-13
Hello, 
 
I've got 2 ntfs-partitions, one for the Windows-installation and another one on a second harddisk for my data (so I can use it from Windows and Kubuntu Feisty). Both are mounted with ntfs-3g, even if I had not used write access on the Windows-partition so far.

Until 2 days ago everything worked fine, but then, all of a sudden I could not write to my data partition/disk anymore. Kubuntu did not crash, and the harddisk/partition is ok - I can use it from Windows without any problems.

I just did a test with my Windows-partition, and I can write to it! 

As you can see, the entries in fstab are identical, so it's really strange to me: 
 
/dev/hda1 /media/hda1 ntfs-3g defaults,locale=de_DE.UTF-8 0 0 
/dev/hdc1 /media/DATEN ntfs-3g defaults,locale=de_DE.UTF-8 0 0 
 
Tried with umask=0, tried also uid=1000 and gid=1000, everything without success. I also tried to write with sudo-command, and even this fails. So it seems, there is another (big) problem and I can not write to this ntfs-partitions at all anymore!?

Anyone else having this problem or an idea what to check or how to fix this problem?
 
Regards, 
 
rpw

---

### Post by rpw on 2007-05-13
Problem solved. In the logfile I found the following error message:

Mft record 0x1ba44 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately!

After I ran chkdsk under Windows the problem was solved.

rpw

---

