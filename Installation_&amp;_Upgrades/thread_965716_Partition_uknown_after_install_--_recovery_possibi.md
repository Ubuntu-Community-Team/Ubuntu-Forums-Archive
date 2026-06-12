---
title: "Partition uknown after install -- recovery possibilities?"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by tamahemi on 2008-10-31
Hi, as usual one is smarter afterwards... If you could help me, you would make one person very happy.. so here we go :D
Excuse me if I let out any important part, as I'm not an expert. I used the newest stable Ubuntu-version.

I first had three partitions:
```
partition 1 / ext3 (primary)
partition 5 /home ext3  (additional)
partition 6 swap
```

As I noticed that ubuntu (for whatever reasons) didn't like the /home being in a partition for itself (PC getting very slow), I decided to shrink partition 5 to make more space for partition 1, and then (once everything was installed) put what was in partition 5 to partition 1 (i.e. the home). The partioning was done with the standard ubuntu CDROM-boot/installdisk.

1. shrinked partition 5 to about 200MB above its current used size.
Then however this looked something like this:

```
partition 1 / ext3 (primary)
partition 5 /home ext3  (additional)  unknown size
empty     ---
partition 6 swap
```

Not really what I wanted, however partition 5 now displayed "unknown (size)". And what's worse, when I went on with the installation (assigning partition 5 to some own mounting point) and making partition 1 the primary partition, then I got an error that partition 5 could not be processed (or something similar). Then I got back to the same partition-screen again.

Canceling everything and starting the PC leads to a grub error. Oh no, what have I done :-(

Any possibilities of recovering the partition, any suggested programs, tools? -- Thanks alot!

tamahemi

---

### Post by tamahemi on 2008-11-01
nobody?

---

### Post by Pumalite on 2008-11-01
Try Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by tamahemi on 2008-11-02
It worked. Thanks!

---

