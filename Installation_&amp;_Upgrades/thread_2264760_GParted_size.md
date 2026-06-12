---
title: "GParted size"
date: 2015-02-10
forum: Installation &amp; Upgrades
---

### Post by andy122 on 2015-02-10
Hi all, I've added more logical partitions to my system using GParted - there was some unallocated space in the existing exended partition, and some at the primary partition level. I shrunk one of the existing logical partitions (happened to be the last one), added most of the "primary partition level" unallocated space to the existing extended partition, and then used all this to create three new logical partitions. Everything seems to work, except that GParted now shows these new partitions as having a large amount of space "used". For the new 4GiB partition, there's 134MiB "used", and for the new 166GiB partition, there's about 2GiB "used". I mounted the 166GiB partition, and in the file manager it apparently is (practically) empty. Where does this discrepancy come from?Thanks!

---

### Post by MAFoElffen on 2015-02-10
What filesystem type? If ext4, then you have a percentage of it reserved for journaling... As I remember, rule of thumb estimate on that is about 5%. So would be around 51MB per GB. So what you reported, aligns with those estimates.

---

### Post by andy122 on 2015-02-10
Thanks for the answer!

---

