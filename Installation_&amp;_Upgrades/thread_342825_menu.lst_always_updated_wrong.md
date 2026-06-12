---
title: "menu.lst always updated wrong"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by steve0921 on 2007-01-20
I'm having trouble whenever I upgrade my kernel and /boot/grub/menu.lst gets updated. The problem is that the updated version always contains:
```
root (hd0,5)
kernel /boot/vmlinuz.... root=/dev/sda6 ...
```

When my Ubuntu partition is really on the partition (hd0,6) (or /dev/sda7). Also, since upgrading to edgy UUIDs have been used which just complicates things a bit more.

Is there somewhere that I can tell Ubuntu what partition it's actually on (so I can avoid digging out my restore cd whenever I upgrade)?

Also, out of curiosity, how do I find the UUID of a partition? (For now, I just found it in /etc/fstab which was also updated to use them.)

---

### Post by steve0921 on 2007-01-27
Ooops,

I just noticed in all of the commented bits in menu.lst there are options for the autogenerator in the comments. No kernel to update to, but I assume this will fix my problem.

Just posting the solution to add closure; I hope nobody else is as silly as me.

---

