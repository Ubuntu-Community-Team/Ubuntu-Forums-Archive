---
title: "how delet a partition??"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by anujv73 on 2007-07-23
hi ,
   i have four partition in computer i wanted to delet one partition and merge free space into remaining partition
pls help me

---

### Post by Espreon on 2007-07-23
Do you have Gparted installed if not do this in a terminal:

```
sudo apt-get install gparted
```

Then start GParted, and right-click the partion and hit delete and apply.

Then resize the partion you wanna make bigger and add n space.

n=The amount of space that the partion you deleted had.

---

