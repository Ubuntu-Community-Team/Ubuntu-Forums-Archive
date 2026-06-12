---
title: "Reintall Ubuntu?"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by pfx on 2007-03-23
A friend of mine would like to go from 64bit Edgy to 32bit Edgy. We were wondering if he could just delete the partition in Windows, with Partition Magic, and then reinstall with the i386 live CD. I guess the main question is, will GRUB need to be erased, or will the new installation of Ubuntu take care of that?

---

### Post by zvacet on 2007-03-23
What for he needs two versions of same distribution?If he is decide to work on 32bit then he don´t need 64bit.if that is a case erase 64 and install 32.

---

### Post by pfx on 2007-03-23
Yes, the question is that if he were to delete the 64bit's partition, would he need to fix the mbr (as in case with completely removing Ubuntu) or will a fresh install of 32bit Edgy take care of that without requiring to fix the mbr? Sorry if that wasn't clear.

---

### Post by lvleph on 2007-03-23
from my experience the fresh install will take care of it. But, if you have the Live CD you don't need to use partition magic. The live cd will see the current partitions and ask if you want to reformat them under the manual format option. Just reformat the ext3 and swap. Everything will work.

---

