---
title: "Best file system  for mdadm, lvm drive"
date: 2018-01-09
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2018-01-09
I am upgrading one of my computers running 16.04 LTS intend to install two hard drives with lvm2 over RAID1 (mdadm) then create 2-3 logical drives to separate the OS from the data and home logical drives.  What is the best file system to use in this situation? Ext3, ext4, ZFS, XFS or something else.

---

### Post by TheFu on 2018-01-09
It depends.  TL;DR - use ext4.

How much storage?
What types of files? How large are the files?
Will more physical disks be added later?
SSDs, SSHD, or old spinning rust disks?
Any DBMS or other transactional performance concerns?

---

### Post by rsteinmetz70112 on 2018-01-09
2 TB of Storage, 4 1 TB hard drives in 2 arrays, 16Gb Ram mostly small files, maybe a small mysql database or 2.
I've been reading up on ZFS which seems to combine all of the above.

---

### Post by TheFu on 2018-01-09
ZFS really needs 6 disks, IMHO.

The drive data doesn't match the first post with the last post.  At least it isn't clear.  What does RAM matter?

MySQL --> MariaDB ; MariaDB is the default now, not mysql. That's a good thing, IMHO.

I don't understand the rest.  ext4 is the default answer. No need for xfs from what you've said.

---

### Post by rsteinmetz70112 on 2018-01-10
RAM matters because some file systems need a lot of RAM, especially if it does a lot of caching.

I see how the drives don't match, I wasn't clear. I was originally thinking 2 raid 1 mdadm devices each with 2 1 TB drives for a total of 4 1 TB drives. I suppose I could use all 4 drives in a single array and take advantage of the increased performance due to striping, as long as I get 2 TB of storage.

I'm curious as to why you think ZFS needs 6 drives, please share your thoughts. 

It seems I could mirror the drives with ZFS, create two pools and then assign my file systems to those pools as necessary. That is not the highest performance but I'm more interested redundancy.

As far as the database, that depends on the applications that will use it and one existing application (not in the Ubuntu repositories) which will be migrated to the new configuration uses mysql and converting to another db simply adds more complexity. Any other db applications are speculative at this point.

---

### Post by TheFu on 2018-01-10
In the OP, you said "intend to install two hard drives with lvm2 over RAID1" and didn't mention any others. Details matter here, sometimes, but not always.

The primary reason that people use ZFS is for RAIDz2, that needs 6 disks.  Also, RAM is only important if you use ZFS **and** use the more advanced features.  ZFS does fine on 1-2G ram if you don't use those.   I've never used ZFS on Linux, just Solaris.

MariaDB is API compatible with MySQL.  The same client API libraries are used.  The MariaDB team is the former MySQL creators, bought my Sun Micro, bought by Oracle, who left Oracle for their own reasons.  By default, a new DB web-app on Ubuntu will install mariaDB.  If you didn't know better, it would look like mysql to you, but without the possible less-than-friendly Oracle things.  Of course, those are my politics, not necessarily everyone else's.

For what you've described, ext4 is still the best option, IMHO.

I would keep the OS on a non-RAID disk, BTW.

---

