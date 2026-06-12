---
title: "Change installation folder"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by plenthoz on 2011-01-24
i use **UBUNTU 10.10**,,How can i change application destination folder after i install them??
i mean just like windows if we want to save the space we could change the installation folder in installation wizard,,from default (C:/filesystem/program files) to another drive...

---

### Post by vanadium on 2011-01-24
You probably are limited in space on one partition and want to move data to another?

A system partition of 10 GB is plenty for an Ubuntu install. How large is your system partition?

First look if you can resolve the issue by moving personal user data (Documents, Movies, Downloads, etc.). This is very easy to achieve. After moving the user data, you put links where they originally were, and you can access your data in the same place as before, even though they reside on a different partition or even a different hard drive.

If you really have a very small system partition, you may indeed need to move parts of the system, or repartition. This is less trivial and requires some technical knowledge of the system.

---

### Post by plenthoz on 2011-01-24
i have 13GB partition for ubuntu filesystem,,,but i've install many program and leave me with just 3gb freespace...i plan to move some of my application to another drive so it will give more freespace to the filesystem, can you help me?? thanks a lot

---

### Post by vanadium on 2011-01-24
It is quite hard to believe that you filled 10 GB only with applications. I guess there will be other data there as well.

You might want to analyse the disk usage (Applications - Accessories - Disk Usage Analyser) to see where the data are mostly located. This will indicate which data you might want to move.

You can have a brief overview of disk usage with the command

```

df -h

```
You might post that here. It shows which partitions are mounted where, and how much space of them is used.
Another command that gives a textual output of where the bytes went, is
```

du -chs /* 2>/dev/null

```
The output of these commands might provide more insight in what the issue is and how you could address it.
[/code]

---

### Post by plenthoz on 2011-01-24
hehehe my internet speed superfast, so i download many games like nexuiz, fretsonfire and many more,, and a bunch of programming ide...

thanks a lot sir i owe you:D

---

