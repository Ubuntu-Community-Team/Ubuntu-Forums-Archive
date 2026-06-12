---
title: "Recover data after incorrect drive added to RAID array"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by elliott6 on 2010-01-16
Hey All,

Running Mythbuntu, I had decided to upgrade my storage to use hardware RAID.  With a Perc 5i, I have one set of inputs connected to 3 1TB drives, and 2 of the other set of 4 connected to 1.5TB drives.  There is a third 1.5TB drive to add so I can have 2 RAID5 arrays, but it currently has/had my recordings on it.

I may have messed up and incorrectly connected the 1.5TB drive with my current recordings to the Perc RAID card.  And yes, I (getting ahead of myself) did create a virtual disk on the Perc card with the 2 1.5TB drives as RAID0 with the intention of adding the third disk once I copied the recordings to the 3x1TB RAID5 array, thus creating and converting to the 3x1.5TB RAID5 array.  NO, I did not format, copy, or anything else with the 2x1.5TB RAID0 array.  I didn't get far enough, as I was looking for my recordings so I could transfer them.

I am now getting the following - 

fsck died with exit status 8
File system check failed
Please repair the file system manually
A Maintenance shell will now be started
CONTROL-D will terminate this shell and resume system booy.

I know my UUID is incorrect, but when I connect the 1.5TB drives separately (off the mainboard), Partion Editor shows they are empty with no partitions, as I know 1 of the 3 1.5TB had a XFS partition with my recordings on it.  

My question is whether it is possible to get my recordings back as it appears I may have wiped the "table of contents" boot record when it was added to the hardware RAID array?  I believe, in my search, mention was made to try e2fsk as well as some others, but I thought I would write this out for suggestions before I go aimlessly executing commands from responses read on the internet, ultimately making it worse/totally unrecoverable.

Appreciate everyone's time and help!  Sorry (and thanks if moved) if this is the wrong forum for this. 

Sean

---

