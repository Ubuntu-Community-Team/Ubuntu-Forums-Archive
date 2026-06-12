---
title: "After every kernel upgrade grub tries to boot from wrong partition"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by ireneshusband on 2008-02-18
Every kernel upgrade I find that the grub menu gets mashed and it tries to boot from (hd0,5) (the swap)  instead of (hd0,4). I then fix menu.lst only to find the same thing happen at the next kernel upgrade. Presumably there is a file somewhere that is telling grub to do it all wrong. Anyone know where it is?

This history behind this, in case it is useful, is that I manually partitioned the disk, creating the swap first at the end of the disk, so this became partition 5 and root ended up being partition 6. Then at some point Ubuntu spontaneously reordered the partitions so that root ended up being 5 and swap 6.

---

### Post by zvacet on 2008-02-18
```
 cat /boot/grub/menu.lst

```

Post output here.

---

### Post by ireneshusband on 2008-02-19
Many thanks indeed! Your post pointed me in the right direction. I took another look at menu.lst and found  the following line:
```
#groot=(hd0,5)
```
This is the line I was looking for. Even though it is commented out  to prevent grub from reading it, it is still treated as an instruction by the program that writes the new menu.lst.  I have now changed the line to read
```
#groot(hd0,4)
```
which I hope will solve the problem.

---

