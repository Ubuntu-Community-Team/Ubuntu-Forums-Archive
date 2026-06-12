---
title: "logical block errors"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by gammyhand on 2006-11-14
I downloaded the alternate CD after the desktop one failed and the partitioner is reporting that there are logical block I/O errors...Is there any way around this? The machine did have windows on the 100gb partition but I formatted that to HDS3 the other day when installing hoary and now it seems my disk is broken. 

It is reporting the error on HDA5 which is the 150gb partition which I have removed from fstab.

What can I do? I can't see how my disk can be working fine one day and knackered the next, it still reads fine in hoary with no clunks bangs or breaking noises.

---

### Post by ReaderRat on 2006-11-14
I don't really understand your problem. Does the disc have anything else on it (Windoze) ? If not, I would suggest that you run the partitioning phase, remove all partitions, and then, let the partitioner install to the empty disc.

---

### Post by gammyhand on 2006-11-15
> **ReaderRat said:**
> I don't really understand your problem. Does the disc have anything else on it (Windoze) ? If not, I would suggest that you run the partitioning phase, remove all partitions, and then, let the partitioner install to the empty disc.

Ubuntu hoary is already on the 100gb partition.

My backed up stuff like work and MP3's are on the 150gb NTFS partition.

I installed hoary over xp the other day on the 100gb partition. The partitioner ran fine. I now want to upgrade to edgy. I ran the installer and it crashes at the partitioner with logical block errors on the hdd.

There must be something I can do like format the 100gb partition and then run the installer.

But all I want to do is install edgy on the 100gb partition and not lose anything on the 150gb partition.

I don't see how you don't understand my problem but to clarify; my hdd is reporting itself as spent/kaput/goosed or good old fashioned broke and I don't believe it is.

---

### Post by gammyhand on 2006-11-15
It seems that if I leave it long enough it eventually gets over its I/O errors and allows me to format. However, now it has formatted and it said "no root filesystem defined" which is a problem as I have lost hoary and can only use the edgy live CD. Can I fix this??

---

### Post by ReaderRat on 2006-11-15
You can't fix Hoary. 
Run this code in Terminal and post the results so I can see what's what:
```
cat /etc/fstab
```
and
```
sudo fdisk -l
```

---

