---
title: "convert mdadm 4 disk raid5 to 4 disk raid10 without data loss?"
date: 2016-09-16
forum: Installation &amp; Upgrades
---

### Post by alex351 on 2016-09-16
hi all,

the title basically says it all. I currenty run 4 SSDs in a raid5 but dont really need the space and thus would like to convert it to a raid10 for increased performance and failure protection. is there a way to this without removing the data from the drives, destroying the raid and recreating the raid10?

thanks in advance

---

### Post by TheFu on 2016-09-16
no.

---

### Post by Jimysbil on 2016-09-17
I have never used raid on my own but I think what you are asking for is partially impossible.Raid5 is using a parity flag to calculate the data on your disks and it needs 3 or more disks to set it up.On the other hand Raid1 is an exact copy of a drive to an other (or more drives).On Raid5 you can detach only one disk from your raid system or your raid will collapse and you will lose your data.Also on Raid1 you can detach drive(s) but you should always have a working one or the raid collapses.If you have not an extra disk to put your backups it's impossible to convert a raid5 into two raid1 drives.
So you have to move backups of your data to an extra drive , destroy your previous raid5 and build two raid1.
And as long as you want raid10 you have to make a raid0 with your two new raid1 drives.

---

### Post by TheFu on 2016-09-18
RAID is never a replacement for backups.

RAID solves 2 problems.  
1) HA
2) Performance (if using HW RAID)

Backups solve 1,000+ problems, including a number of problems with RAID deployments.

---

