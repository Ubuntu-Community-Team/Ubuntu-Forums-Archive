---
title: "[SOLVED] How to resize unallocated partition?"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by ratmandall on 2008-11-01
I deleted my NTFS partition thinking it would give me back the space that it was using but it didn't and now it's "unallocated" and I can't resize/move it.
[img]http://s4.tinypic.com/5wf77o.jpg[/img]

---

### Post by Partyboi2 on 2008-11-01
Right click on swap and turn it off and then resize your extended partition to use the unallocated space. Or format the unallocated space and use it has extra storage or create a new ext3 partition and move your /home folder to its own partition.

---

### Post by ratmandall on 2008-11-01
> **Partyboi2 said:**
> Right click on swap and turn it off and then resize your extended partition to use the unallocated space. Or format the unallocated space and use it has extra storage or create a new ext3 partition and move your /home folder to its own partition.

I turned swap off and it doesn't give me the format option for the unallocated space:(
Btw I'm using ubuntu 8.10 live cd

---

### Post by Partyboi2 on 2008-11-01
Turning off swap should allow you to increase the size of the extended partition, its been awhile since I have had to do this so memory is not the best, try turning off swap then right click on your ext3 partition and unmount if it is mounted then do the same for the extended partition. Then try and resize your extended or your ext3 to use the unallocated space one of those partitions should allow you to increase its size. (sorry memory is like a sieve at the moment)  
If you have decided to create a new partition of the unallocated space instead of resizing your ext3 partition to use the unallocated space then rightclick on the unallocated space and choose "new" and choose  "filesystem"  and select ext3 and the size you want for it.

---

