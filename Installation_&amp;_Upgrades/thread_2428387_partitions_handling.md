---
title: "partitions handling"
date: 2019-10-03
forum: Installation &amp; Upgrades
---

### Post by yovelcohen on 2019-10-03
hi,
I'm new to ubuntu.
after experimenting for few weeks with it, i decided to say goodbye to my windows 10 and add it's partition to the existing Linux one (ext4).
after learning a bit i successfully booted in gparted live cd from USB , after already deleting the windows partition.
so that partition is just a free space now, but i still can't resize my ext4 partition, even if boot from USB to gparted live.
kind of lost right now.
thanks

---

### Post by ubfan1 on 2019-10-03
Step 0 -- backup everything.  Partitioning can go very wrong, very easily.  Some more information, like the layout of the partitions would be useful, because where the free space is in relation to the ext 4 you want to expand makes a big difference in difficulty of the merge.  On the right (end) easy, on the left (start) very hard.  On the left, the usual recommendation is to just backup everything, reset the partitions the way you want, and restore.

---

### Post by Rubi1200 on 2019-10-03
Hi and welcome to the forums yovelcohen :-)

As ubfan1 mentioned, backups, backups, backups.

What would help us is either a screenshot from GParted of your partitions or the output of this command from a terminal:

```
sudo fdisk -l
```

Lowercase L not 1

Thanks and good luck.

---

### Post by yovelcohen on 2019-10-03
thanks for the help.
here's my gparted

---

### Post by oldfred on 2019-10-04
You have the old BIOS/MBR configuration with 4 primary partition limit. So additional partitions are in the extended partition which acts as a container for all the logical partitions.

You must first unmount all your partitions. The little key icons show them mounted. You have to use live installer in live mode. It may mount swap, and if so, unmount swap to also unmount the extended partition.

Then you can move extended partition left to include all the unallocated space.
I do not particularly like moving partitions left as it is very slow and any interruption totally corrupts that partition, or why you must have backups. Then you can expand right.

You may want to consider making a new logical partition and make that /home.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

