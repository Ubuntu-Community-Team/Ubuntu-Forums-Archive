---
title: "Filesystem for root and home partition"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by Enigmatic on 2008-07-10
Any recommendations on what to use?

---

### Post by avtolle on 2008-07-10
I'd use ext3 for those partitions.

---

### Post by ibutho on 2008-07-10
Ext3 or Reiserfs should be fine. Reiserfs is particularly good if you have lots of small files.

---

### Post by Enigmatic on 2008-07-10
In terms of overall apparent speed, does Reiserfs offer an advantage over ext3?

---

### Post by wpshooter on 2008-07-10
> **Enigmatic said:**
> In terms of overall apparent speed, does Reiserfs offer an advantage over ext3?

My guess is that you would not be aware of any "apparent" speed.

---

### Post by Enigmatic on 2008-07-10
Ok. For some reason (and it's probably my imagination), I thought Reiserfs felt faster than ext3.

---

