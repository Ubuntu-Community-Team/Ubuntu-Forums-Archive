---
title: "Need advice for building a new file server"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by Svenstaro on 2008-10-23
Hi everybody,

so for me the time has finally come to upgrade my server to a bigger bugger. With HDD prices rapidly decreasing and storage sizes increasing, I decided to build myself a brand-new file server and media storage. 
My current one is pretty much built from scrap components and runs a 4-year-old Debian system that has gone through all imaginable pain a Linux system could possibly take. I was pretty green back then and so I decided to take a clean approach this time. 

My old system uses an LVM array which eventually reached a size of 1.5TB by adding and replacing hard disks over time. Since it's all IDE drives from different centuries it obviously doesn't yield the best performance.

For the new server I ordered 3x750GB SATA2 Samsung HDDs rated for 24/7 usage. 

Basically, my question now is what kind of array I should form. I've got good experiences with LVM since it's quite easy to expand and recover failures but I was looking at a possibility to form a RAID to improve performance. I heard that RAIDs aren't easily expanded though and a bit of Googling didn't disprove that. It seems that LVM on-top of RAID is a common choice but I keep wondering why nobody just does an LVM2 with built-in striping. Is it unreliable or slow (or slower compared to RAID)?

Enlighten me please :)

---

### Post by ilrudie on 2008-10-23
Striping alone will increase the chances of data loss.  This is because a logical volume can fail if any of the underlying physical extents fail unless there is some sort of data redundancy (parity or mirror).  With 3 disks your best bet will probably be building a raid 5 array with mdadm and adding LVM2 on top.  Newer kernels (2.6.17 and newer) have better raid tools that allow easy resizing of raid 5 arrays.
[Resize RAID5]("http://lkml.org/lkml/2006/3/20/105")
[LVM HOWTO]("http://tldp.org/HOWTO/LVM-HOWTO/index.html")

---

### Post by Svenstaro on 2008-10-23
To be honest, I'm not too afraid of hard disk failure since I do regular backups on tape. 

With the possibility of resizing RAID, why would I still need an LVM?

---

### Post by ilrudie on 2008-10-23
To gain the advantages of logical volumes (grow, shrink, add logical volumes; snapshots).  If you don't think you will need those advantages then you don't need LVM2.  I personally prefer to use it in case I need or want a new file system without having to add another drive or build another array.

If you are not worried about data loss then raid 0 (striping) is fine.

---

