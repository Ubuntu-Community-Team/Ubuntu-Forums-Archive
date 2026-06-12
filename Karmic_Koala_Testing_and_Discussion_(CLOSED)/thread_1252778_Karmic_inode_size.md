---
title: "Karmic inode size?"
date: 2009-08-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by spongypants23 on 2009-08-29
When you format a partition with ext4 using the Karmic installer, what is the default inode size?

I ask because I'd prefer to have 128 since it's more compatible with things than the newer 256.

---

### Post by VMC on 2009-08-29
It defaults to 256
Try this

mkfs.ext4 -I 128 <device>

read man mkfs.ext4

---

### Post by spongypants23 on 2009-08-29
Thank you.

---

### Post by dino99 on 2009-08-30
Looking at kernel.log, i see "ext3_orphan_cleanup: deleting unreferenced inode " several times; what does that means ?

---

### Post by taavikko on 2009-08-30
> **dino99 said:**
> Looking at kernel.log, i see "ext3_orphan_cleanup: deleting unreferenced inode " several times; what does that means ?

Filesystem is just cleaning itself up. 
Unless you suffer from data_loss then there's something to worry about.

---

### Post by dino99 on 2009-08-30
thanks man, i feel better :lolflag:

---

