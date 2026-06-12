---
title: "moving ubuntu partition"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by xzero1 on 2010-06-08
The idea is to move an installed ubuntu (Lucid) partition to another drive. It seems to work, but I am wondering if I *missed* anything. Here are the basic steps I took:

**WARNING: NOT A HOWTO**
[LIST]
[*]shrink current partition to fit into new the partition
[*]use gparted to copy paste the partition and make it bootable
[*]boot os and run sudo update-grub (grub2)
[*]boot to new partition
[/LIST]

---

### Post by labinnsw on 2010-06-10
I never fail to be amazed whenever I discover a Gparted capability for the first time.

---

### Post by oldfred on 2010-06-10
Since it is a new partition did you not have to edit fstab? It uses UUID, drives, or labels. Or does a copy also copy UUID but then I would think you have duplicates?

---

### Post by xzero1 on 2010-06-11
> **oldfred said:**
> Since it is a new partition did you not have to edit fstab? It uses UUID, drives, or labels. Or does a copy also copy UUID but then I would think you have duplicates?

I did not edit the fstab. I believe this was due to grub2. Its seems almost too easy, which is why I asked if I missed anything.

---

