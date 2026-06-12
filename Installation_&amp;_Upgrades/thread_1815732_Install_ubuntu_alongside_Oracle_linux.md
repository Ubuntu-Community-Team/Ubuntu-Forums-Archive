---
title: "Install ubuntu alongside Oracle linux"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by 7cardcha on 2011-07-31
I have Oracle linux installed and I would like to install Ubuntu alongside it. My questions are.

1.When I install it using Ubuntu's partitioner to set aside a partition for it will it automatically move any files on that partition to the Oracle Linux partition?


2.How will I switch back to Oracle Linux from Ubuntu and vice versa?


3.Are there any other problems I am overseeing?


Thank you for your time.

---

### Post by Kooothor on 2011-07-31
> **7cardcha said:**
> 
1.When I install it using Ubuntu's partitioner to set aside a partition for it will it automatically move any files on that partition to the Oracle Linux partition?

nope, install on a clean partition.
> **7cardcha said:**
> 
2.How will I switch back to Oracle Linux from Ubuntu and vice versa?

with two entries in your grub
> **7cardcha said:**
> 
3.Are there any other problems I am overseeing?

don't share the same /home for both
but you can share the swap

---

