---
title: "Why ext3?"
date: 2005-08-10
forum: Installation &amp; Upgrades
---

### Post by fresco on 2005-08-10
Here are my arguments:

$As I have noticed, every fs may be incurred by fragmentation. But ext3 does not have defragmentation tool, only if it is converted back to ext2. However, why should users take additional problems with these things? If machine is running for several months (or even years) without defragmentation, is there performance loss possible?

$ Am I understanding things correctly? If not, give me an advice!  :smile:  

$Is it okay to use ext3, or maybe there are other better possibilities? (XFS for example)

$What filesystem are YOU using? Why?

Many thanks for your thoughts,
peace!

---

### Post by awtomlinson on 2005-08-10
i use reiserfs.  simply because i read many, many articles stating that it would perform better for a workstation, non server, environment.  of course, this is all subjective, but almost all articles i read preferred reiser for such an environment.  of course, when ubuntu boots, i get a "cant find ext3 file system" message, but its just an annoyance.

---

### Post by fresco on 2005-08-11
Any other opinions?

---

### Post by Stormy Eyes on 2005-08-11
Fragmentation is only a performance-impairing issue on Windows, because FAT32 and NTFS are poorly-designed filesystems.

---

### Post by az on 2005-08-11
Also, you do not have to convert an ext3 filesystem to ext2.  Actually, you just mount it without the journaling and there you go:  ext2.  This is not an irreversable thing.  It just depends on how you mount it.

---

### Post by baustiech on 2005-08-12
get another cheap HD

cp-a * to new drive, sequentially.

rm -fr * original (except /, obviously)

cp -a * back

poof, defragged

---

