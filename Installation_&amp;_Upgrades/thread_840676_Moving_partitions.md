---
title: "Moving partitions"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by jdestruel on 2008-06-25
I have 3 partitions: XP, 7.10 and 8.04.

I want to remove 7.10 and move 8.04 to where 7.10 is so that XP and 8.04 are next to each other.

I don't think I can backup 8.04, delete 7.10 and copy back 8.04 where 7.10 was because of the cluster numbering.

Do you have any suggestions?

---

### Post by chewearn on 2008-06-25
Boot into ubuntu livecd, and use the Partition Editor to rearrange the partitions.

Afterwards, grub might failed to load, because you have delete one partition in between.  While still in livecd, run grub to fix it.

```
sudo grub
```
```
find /boot/grub/stage1
```

You will get a location, e.g. (hd0,1):
```
root (hd0,1)
setup(hd0)
quit
```

Then, edit /boot/grub/menu.lst, find the hardy kernel and change the location to (hd0,1).

Do all these within the livecd.  If boot fails with grub error, reboot back to livecd to fix the problem.
.

---

### Post by jdestruel on 2008-06-26
Thanks

---

