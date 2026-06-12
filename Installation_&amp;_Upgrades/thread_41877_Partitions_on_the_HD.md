---
title: "Partitions on the HD"
date: 2005-06-15
forum: Installation &amp; Upgrades
---

### Post by phend-one on 2005-06-15
The last time I installed ubuntu was 4.10 and that was a long time ago.

I have a few questions about 5.04.

Is this going to be okay? :
[primary]
10gb (ntfs) winxp partition
[extended]
logical drives: 
2gb (ntfs)
50gb (ntfs)
50gb (ntfs)

I am clearing space out of the last 50gb partition to make room for ubuntu (will be partitioning 40/10 gb).
Does it matter that it's in a extended partition?
Does it matter that ubuntu will be in the last partition on this drive?

I plan on dual booting.

Thanks for any help!

---

### Post by defkewl on 2005-06-15
No it does not matter. My Linux partition is located on extended partition.

---

### Post by Alexander Kirillov on 2005-06-15
[QUOTE=phend-one]The last time I installed ubuntu was 4.10 and that was a long time ago.

I have a few questions about 5.04.

Is this going to be okay? :
[primary]
10gb (ntfs) winxp partition
[extended]
logical drives: 
2gb (ntfs)
50gb (ntfs)
50gb (ntfs)

I am clearing space out of the last 50gb partition to make room for ubuntu (will be partitioning 40/10 gb).
Does it matter that it's in a extended partition?
Does it matter that ubuntu will be in the last partition on this drive?

I plan on dual booting.

Thanks for any help![/QUOTE]
 It is OK except that Linux can't write to ntfs filesystem - so you won't be able to exchange files between windows and Linux. I always create a fat32 partition  for this purpose and put things like music, photos, etc on it.

---

### Post by ubuntu_demon on 2005-06-15
[QUOTE=Alexander Kirillov]It is OK except that Linux can't write to ntfs filesystem - so you won't be able to exchange files between windows and Linux. I always create a fat32 partition  for this purpose and put things like music, photos, etc on it.[/QUOTE]
 Or use an other machine as a fileserver ... ubuntu(using samba) or windows 2000 / XP / 2003

---

