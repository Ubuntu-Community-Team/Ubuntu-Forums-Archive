---
title: "[SOLVED] Max number of partitions"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by Raccoon1400 on 2008-01-14
I went to create a new partition on my hard drive. It wouldn't let me. I have 4 ntfs partitions. I think I have reached the partition limit. Does the ext3 ubuntu partition also put me over the limit? I'm not sure because it is a different filesystem.

Thanks

---

### Post by taurus on 2008-01-14
You can only have four primary partitions whether you run windows or Linux.  And if you need to create more partitions, you need to convert one of those primaries to extended and then you can create logical partitions under that extended partition.

---

### Post by Raccoon1400 on 2008-01-14
I bought a dell computer with 4 partitions already on it. One is a dell utility partition. The next is a recovery partition, which i shank from 10 GB to 5, the OS partition, and a MediaDirect Partition, Which I will probably delete to allow me to create  a Ubuntu partition.

---

### Post by Gina on 2008-01-14
You'll need to create an extended partition, then logical partitions within that, because Ubuntu needs a minimum of 2 partitions - system and swap.  Ubuntu is quite happy on logical partitions.

---

### Post by cirorodrigues on 2008-04-01
> **Raccoon1400 said:**
> I bought a dell computer with 4 partitions already on it. One is a dell utility partition. The next is a recovery partition, which i shank from 10 GB to 5, the OS partition, and a MediaDirect Partition, Which I will probably delete to allow me to create  a Ubuntu partition.

I got a Dell desktop already partitioned pretty much like yours: there's a recovery one, another for Win, and another, quite small (69 MB), which I don't know the purpose. And you refers to MediaDirect - what's it ?
I'll redo the partitions to install Ubuntu and I'd like to keep Win and Dell recovery, but I plan to get rid of the small one, but I'm not sure yet.

---

