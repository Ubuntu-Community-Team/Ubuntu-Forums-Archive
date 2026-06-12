---
title: "Replacing both drives in RAID"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by subject117 on 2007-12-23
I have two mirrored drives on my Dell machine, and ubuntu is doing the mirroring.  One of the drive died, and the other is dying.  Dell support is sending me two new drives to replace the current ones.

I need to replace the dead drive, then make the mirror make a new copy on the replacement drive, then replace the other old drive, and make the mirror make a new copy a second time.  How do I make ubuntu accept the new drive and rebuild the RAID?  Twice?  Also, I seem to remember some of the boot stuff is on a non-mirrored partition on my remaining drive.  To make all this work, need to transfer that to the a new drive.  How do I move the boot partition from one hard drive to another?

Would it be simpler/faster/better to just take the two drives out, put the two new ones in, and then do a fresh install?  I do have a backup available.  But then I need to reinstall the same software again, which could be tedious.  Is there anyway to export all the packages I have installed, save the list, and then re-import that later to install the same stuff again?

---

### Post by heatpumpcontrol on 2007-12-23
What you might want to do is boot off the Live CD.

Remove one drive at a time and boot off the CD. Use System-->Administration-->Partition Editor to copy the old drive onto the new drive. Do the same with both drives and make sure you know which drive is the boot drive. Not sure if your partition uid will change for the partitions. 

Read up some more and maybe someone here can add to my suggestion or just advice you otherwise.

---

