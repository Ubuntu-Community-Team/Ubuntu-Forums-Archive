---
title: "New Hard Drive Bad Partition Table / Altered Geometry"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by Hamarabi on 2010-02-07
******Edit****The Bad Partition Table and the bad sector count was too much for me to overcome, so I decided to send the hard drive back for replacement since it is brand new and still under warranty. **

I royally screwed up my Partition Table and/or hard disk geometry during, what I thought was, a routine restore of a WindowsXP partition from an old hard drive to a new hard drive.

[LIST]
[*]I bought a new hard drive (WD Caviar Black 750GB) which is larger than my old one (WD Caviar Black 640GB).

[*]I used a "ImageCenter Drive Image" backup to restore the WindowsXP partition from the old hard drive on to the new hard drive.  The program said that the partition back up is not the same size as the new partition.  The backup was of a 200GB WindowsXP partition and I wanted to put it on a 300GB partition of the new hard drive. I told it to resize automatically to fit.  I planned to use the rest of the hard drive for backups and personal files.

[*]Partition Magic gives an error code #110.  Symantec's website says to delete the partition and start over which was accomplished, but that did not fix the Partition Table problem that Partition Magic reported.

[*]The problem has something to do with "altered hard disk geometry as reported by the drive's Partition Table" which is beyond my current understanding of hard drive architecture.  I have been working on this problem non-stop for two days, so far.

[*]After hours of research and feeble attempts to fix this problem, I read somewhere that sfdisk could repair the Partition Table, so I first used an **Ubuntu Live CD**, but that was to no avail.  I then decided to install the full **Ubuntu 9.10** and see if I would have any better luck, again to no avail.  I just do not understand how to proceed with restoring/rebuilding the original "factory new" Partition Table of this new hard drive.

[*]Testdisk reports bad sector count.
[/LIST]

**Anyone willing to help me track down the problem and find a solution?**

I don't care about data loss, since there is nothing to lose on the new hard drive.  I just want to save the hard drive itself.

---

