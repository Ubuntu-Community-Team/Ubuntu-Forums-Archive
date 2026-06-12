---
title: "What filesystem for SSD?"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by afton on 2011-08-21
If you're installing [X]ubuntu on SSD, what filesystem do you use?

---

### Post by dino99 on 2011-08-21
ext3 or ext4

---

### Post by sanderd17 on 2011-08-21
> **dino99 said:**
> ext3 or ext4

I agree: [http://robert.penz.name/137/no-swap-partition-journaling-filesystem-on-a-ssd/](http://robert.penz.name/137/no-swap-partition-journaling-filesystem-on-a-ssd/)

---

### Post by recluce on 2011-08-21
EXT3 or EXT4 are the only choices that support TRIM. You need at least kernel 2.6.35 and you have to add the "discard" option to your fstab. You may want "noatime" to reduce write operations. You also need to align your partitions, many guides are available here and elsewhere.

---

