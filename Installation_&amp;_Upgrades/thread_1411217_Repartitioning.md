---
title: "Repartitioning"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by bryanismynamo123 on 2010-02-19
I was wondering, 
If I could use the Ubuntu CD, add more space to the Windows partition, continue (so it reformats it) and not installl Ubuntu, leaving Windows XP, unharmed.
 
Thanks :KS

---

### Post by SuperSonic4 on 2010-02-19
No, reformatting the XP drive will wipe XP.

I would use the excess space to create an NTFS partition for data, in XP you can then move your data to the new partition making room on the original

---

### Post by darkod on 2010-02-19
You are talking about extending a XP partition? Yes, you could do this as long as there is unallocated space after the partition. Or if you create unallocated space by shrinking another partition.
You can use Gparted from the live desktop and you don't need to install ubuntu.
But don't forget to boot XP few times after every partition resize operation so it can figure out the new size and do its disk checks.

---

### Post by bryanismynamo123 on 2010-02-19
Unallocated space?
So extend the XP partition, and then leave some space over?

---

### Post by darkod on 2010-02-19
No, before expanding there has to be unallocated space next to it to expand into. It can't overlap another partition.

If you have for example:

part1--part2--part3

you will need first to shrink part2 to create unallocated space in front

part1--unallocated--part2--part3

and then expand part1 into that space

part1--part2--part3

---

