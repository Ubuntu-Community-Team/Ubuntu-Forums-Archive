---
title: "Timeshift - &quot;Not enough disk space&quot;"
date: 2021-06-16
forum: Installation &amp; Upgrades
---

### Post by aavar on 2021-06-16
Hi
I am having issues with timeshift on my server (ubuntu 20.04). It has been working great for a long time, but recently the snapshots have taken a very long time (hanging at typically 99.XX%).
So I started investigating and I ended up removing all my snapshots hoping that that would solve the issue. But after I tried again it only shows "Not enough disk space (< 1TB)".
I have a few large disks mounted, but I have excluded them (I even tried to unmount them). No luck.
My / is a 250GB SSH with only 75GB used and my snapshot drive is a drive with 464GB free.
I am using Rsync.

I have tried to exclude everything that I can think of and I even excluded /*** for testing, but no luck...

Any idea?

---

### Post by scorp123 on 2021-06-16
Can you please post the output of this:

```
df -h
```

---

### Post by oldfred on 2021-06-16
Did you houseclean trash?
 Space is still used until trash emptied.

---

