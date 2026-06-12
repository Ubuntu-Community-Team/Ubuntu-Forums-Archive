---
title: "mdadm disaster"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by radams58 on 2007-12-09
Howdy folks.

I was trying to move a 3 drive raid-5 array from one machine to another


I ran mdadm --create instead of --assemble

I shutdown, moved it back to the old machine....

and now it's trying to repair itself.

All of this was on 7.10 server machines (both of them)
Sil Image controller, Samsung Sata 500gb drives


Am I out 1tb of data?

Thanks for any and all help

---

### Post by george_koss on 2007-12-09
It depends.   You've forced it to replace the raid superblocks, and to treat the whole array as if it were dirty...  do you know if you specified the disks in the same physical order?    If you were lucky, then it will re-assemble the same data set...  if not, your data may be scrambled in a way that's pretty tricky to undo, given the parity striping.   I hope you've got backup for the data, since that's far & away the easiest way to repair things.     Bottom line, if you can't mount the array right now (even with the array not finished rebuilding), then your data is probably scrambled because the physical order is different this time around.   Good luck.

---

### Post by radams58 on 2007-12-09
DOH, suck!!!!
Not again!

Any way to figure it all out?

If I do this two more times..... reordering the drives.... maybe it'll find them?

---

