---
title: "Ubuntu showing incorrect partition use space"
date: 2013-07-17
forum: Installation &amp; Upgrades
---

### Post by oscar2k23 on 2013-07-17
Hello Guys,

I have a partition to hold all my media files. The only thing that worries me is that linux is showing that the partition is only 1% used but I am sure its atleast 40% used. I can go into the partition and browse and play all the files, so I know it is not corrupted.

```
df -T

/dev/sdb2      ext4     1827391512    200484 1734364868   1% /media/Media


```

```
df -H
/dev/sdb2       1.8T  196M  1.7T   1% /media/Media
```

Anyone know why, or how to fix this? A un-mount and remount doesn't change it.

---

### Post by Snowhog on 2013-07-17
On what basis are you claiming that 40% of the 1.8T /media/Media (mounted) partition is used? From the output you provided, 196M (Megabytes) is used.

---

### Post by oscar2k23 on 2013-07-17
I know all the files that I have there, I can go them and play them.

---

