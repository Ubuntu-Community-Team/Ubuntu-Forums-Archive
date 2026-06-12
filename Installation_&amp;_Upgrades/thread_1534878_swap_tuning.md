---
title: "swap tuning"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by sulekha on 2010-07-20
Hi all,

The following is what i have read  in a magazine named "linux for
you" ,  To what extent this is true ?

ideally dedicate a set of high performance disks spread across two or
more controllers .

if swap space resides on a busy disk, then to reduce latency, it
should be located as close to a busy partition
like (/var) as possible to reduce seek time for the drive head

while using different partitions or hard disks of different speeds for
swap, you can assign priorities to each partition so that the kernel
will use higher priority hard disk first.

in addition , the kernel will distribute visit counts in a round robin
fashion across all devices with equal priorities

Ex:-
         /dev/sda6 /swap swap pri=4 0 0
        /dev/sda8 /swap swap pri=4 0 0
       /dev/sdb3 /swap swap pri=1 0 0

---

