---
title: "Why to create new partition if i already have 2?"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by aarohanb on 2007-09-23
I have a 1.9 Ghz intel processor with 256MB RAM and 40GB HDD.
Win XP is already installed on C: drive(10GB) and i have a D: drive(30GB)  for other stuff...

Is it necessary to create new partitions? Or will Ubuntu install in D: drive?

---

### Post by logos34 on 2007-09-23
no, you can't install on those partitions, you will have to shrink D: (by at least 4GB) and create two new partitions / (root) and /swap out of the freed up space.

---

### Post by vinutux on 2007-09-23
yes it si needed because linux and windows file systems are too diffrent........

but ......no prob    when u install ubuntu it will partitionning the last availabe partition (in u r case D) automatically........................

:guitar:

---

### Post by logos34 on 2007-09-23
> **vinutux said:**
> when u install ubuntu it will partitionning the last availabe partition (in u r case D) automatically

right, if you use guided install it *should* resize D: for you automatically (if there's enough unused space, that is)

---

