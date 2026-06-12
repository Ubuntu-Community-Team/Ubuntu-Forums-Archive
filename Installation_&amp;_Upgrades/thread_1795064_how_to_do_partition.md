---
title: "how to do partition"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by samitrimal on 2011-07-02
Hi i am new to linux . I formatted all my  hard drive , i  have installed ubuntu only . Now  can i do partition  after installing in a linux partition?

---

### Post by tommcd on 2011-07-02
The best time to partition your hard drive is *before* you install Ubuntu. 
If you want to create new partitions in unallocated space, or shrink existing partitions in order to create space for new partitions, then you can use GParted from the Ubuntu live CD to do that.

If you only have Ubuntu installed, then the simplest partitioning scheme is to have 3 partitions: root (for the OS), swap, and home (for your data).

What are you trying to accomplish by partitioning your drive?

---

