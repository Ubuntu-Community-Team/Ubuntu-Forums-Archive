---
title: "Putting more than one mount point on a single partition"
date: 2012-07-24
forum: Installation &amp; Upgrades
---

### Post by BiggC on 2012-07-24
My new laptop came with an 8GB integrated SSD, and I'm trying to figure out how to install Ubuntu 12.04 with the following setup:

HDD:
/home
/var
/opt
/tmp

SSD:
Everything else

However, if possible, I do not want to create 4 separate partitions for the HDD. Is this at all feasible? Is my aversion to excessive partitioning unreasonable?

---

### Post by dino99 on 2012-07-24
[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by BiggC on 2012-07-24
I know how to put home, root and swap on separate partitions, and I know that I could give var its own partition, and opt its own partition, etc.

But what I want to do is put /var, /home and /tmp (and maybe /usr) together on a SINGLE partition. While putting everything else on a second one.

---

### Post by matt_symes on 2012-07-24
Hi

I have never tried what you are doing, so no guarantees, but take a look at 

```
mount --bind ....
```

You can add bind to fstab, as bind is just another option for fstab option, which is what you will want to do.

Something along the lines of this may work.....

```
UUID=<UUID> <mount_point> <filesystem_type> <other_options>,bind 0 1
```

Make sure the partition is mounted correctly before you bind the directories you want in that partition.

Kind regards

---

