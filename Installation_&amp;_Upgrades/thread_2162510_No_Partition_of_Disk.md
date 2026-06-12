---
title: "No Partition of Disk?"
date: 2013-07-14
forum: Installation &amp; Upgrades
---

### Post by Valhure on 2013-07-14
I just installed dual installed Unbuntu onto my laptop which already had Windows 7. The choice for which to run at startup works perfectly, Unbuntu works perfectly and Windows works perfectly. My problem is that when (on WIndows 7) I go to Computer Management->Disk management the only partitions are:
39 Mb Healthy(OEM Partition)
RECOVERY 12.45 GB NTFS Healthy (System,Active,Primary Partition)
OS (C: ) 453.27 GB NTFS Healthy(Boot,Page File, Crash Dump, Primary Partition)

Where is Unbuntu? Did it not partition a part of the disk? If so how is it running? Will it accidently overwrite Windows data? Any help would be greatly appreciated.

---

### Post by ibjsb4 on 2013-07-14
Just possible that windows partitioner cannot see a ext4 linux partition.  Try looking at it in ubuntu, ubuntu can see a ntfs partition.

You may need to install **gparted**, its the ubuntu partition manager and can be found in the software center.

---

### Post by steeldriver on 2013-07-14
... or maybe you did a WUBI install? in which case the Ubuntu system is inside a virtual disk that just looks like a file inside Windows

---

### Post by Valhure on 2013-07-14
I did do a WUBI install. That actually makes a lot of sense. Thank you very much.

---

### Post by ibjsb4 on 2013-07-14
Don't forget

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And welcome to the forums :)

---

