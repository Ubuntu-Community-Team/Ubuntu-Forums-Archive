---
title: "always create the locations that need frequent I/O /home,swap.. on the outer tracks ?"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by sulekha on 2010-07-17
Hi all,

The following is what i have read  in a magazine named "linux for
you" ,  To what extent this is true ?

The general rule is that you should always create the locations that
need frequent I/O -/home, swap on the outer tracks , the easiest way
to achieve this is to create these partitions first when partitioning
your hard disk ?

Reason all modern  H.D.D's use a concept called ZCAV(zonal constant
angular velocity). this takes advantage of the fact that more linear
space is available on the outer tracks of the disk platter rather than
on the inside tracks. now since the disk spins at a constant rate ,
which is also known as CAV (constant angular velocity) the read/write
I/O speed will be greater at the outer tracks as compared to the inner
tracks

---

### Post by _Mark_ on 2010-07-17
While maybe true (I am no HD or partitioning expert)I'm betting the speed increase is negligible and in the real world no difference would be noticed

---

### Post by oldfred on 2010-07-17
+1 for _Mark_ comments.

Now if you have lots of RAM (over 2GB) you may never  use swap except for hibernation or extreme cases of every program running or video editing.

Will you be able to type faster or download from INTERNET faster? Those are the main bottlenecks.

Now if you have a server with large databases or millions of users hitting it, like google does, then fine tuning to that level may make a difference. Perhaps if you spend a lot of time compiling programs it may make a difference, but if it is that important then you should have SSD drive.

---

