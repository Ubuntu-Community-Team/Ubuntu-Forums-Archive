---
title: "UPgrading from 10.04 to 10.10 and override Window"
date: 2012-02-08
forum: Installation &amp; Upgrades
---

### Post by mmistroni on 2012-02-08
Hello all
 i have a dual boot PC which until few months ago was running XP and Ubuntu.
I got tired of windows and delete all data i was using.
I now want to upgrade to Ubuntu 10.10 and take advantage of the space that was used by windows.
If i Update using Update Manager, can i still use the extra space used by Windows, or i can use the window partition only if i install using a CD or an USB?


w/kindest regards
 marco

---

### Post by Paddy Landau on 2012-02-09
You can easily expand into the unused space. Delete the Windows partitions and expand the existing partitions.


[LIST=1]
[*]**Back up your data** in case you accidentally choose the wrong partition.
[*]Boot from a Live CD.
[*]Use GParted to manipulate the partitions. Note that moving a partition from one area of the disk to another will take a long time; expanding a partition can take a long time (depending on specific circumstances).
[/LIST]

It is really that simple. If you are unsure about how to use GParted, start it up and post a screen-shot here with your questions and requirements.

---

