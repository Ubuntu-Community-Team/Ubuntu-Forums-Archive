---
title: "partition structure/layout"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by sulekha on 2009-12-26
Hi all,

       I have recently read in some tutorials that structure/layout of a linux partition is as shown here :-

[http://i529.photobucket.com/albums/dd339/aarklon/partition.png](http://i529.photobucket.com/albums/dd339/aarklon/partition.png)

now is this same layout/structure used for both primary and logical partitions ?

---

### Post by phillw on 2009-12-27
> **sulekha said:**
> Hi all,

       I have recently read in some tutorials that structure/layout of a linux partition is as shown here :-

[http://i529.photobucket.com/albums/dd339/aarklon/partition.png](http://i529.photobucket.com/albums/dd339/aarklon/partition.png)

now is this same layout/structure used for both primary and logical partitions ?

Hi, and welcome 

Partioning made easy:

a) You can only have 4 Primary Partitions **maximum** (including an Extended partition).

b) You can have as many partitions as you like in an Extended Partition.

So, typically Ubuntu will use an extended partition to put swap on This need not worry you as you'll be within the 4 maximum level.

For dual booting it becomes a little more tricky.  As some manufacturers are eating up the primary partitions and filling them with backup & restore stuff (because they're too bone idle to do it correctly) you can rapidly  run out of primary partitions. It is here where the extended partition comes to the rescue.

On a 'normal' Win + ubuntu install you'd typically see
```

/dev/sda1   *           1        4464    35857048+   7  HPFS/NTFS
/dev/sda2            9601        9729     1036192+   f  W95 Ext'd (LBA)
/dev/sda3            4466        9600    41246887+  83  Linux
/dev/sda5            9602        9729     1028160   82  Linux swap / Solaris

```
sda1 is primary and holds Win
sda2 is primary and is an extended partition
sda3 is primary and holds ubuntu
sda4 is primary and not used -- it's a spare !!!!
sda5 is an extended area from sda2 (It's holding the /swap area)

anything with a number greater than 4 is living in an extended partition.

Now, for speed reasons, it is recommended that ubuntu live on a primary partition - if your system has only one primary partition left, it is possible to put ubuntu & swap onto the extended area.

If, like me, you want a seperate area for /home (handy for up-dating & easy backups) and more than one operating system (I'm writing this in the development 10.04 alpha test, but still have my 9.10 area in case things go wrong)

You can end up with
```

/dev/sda1   *           1        4464    35857048+   7  HPFS/NTFS
/dev/sda2            6654        9729    24707970    5  Extended
/dev/sda3            4466        6653    17575110   83  Linux
/dev/sda5            6654        8037    11116948+  83  Linux
/dev/sda6            8038        9587    12450343+  83  Linux
/dev/sda7            9588        9729     1140583+  82  Linux swap / Solaris

```

You can see that sda2 is still my extended area, and my 9.10 system still lives on sda3 as before.
But, i now have /home and /10.04 along with /swap on the extended area.

I hope that makes sense to you as to how partitions work.

Phill.

---

### Post by sulekha on 2009-12-27
nope you are not getting my point

i meant this:-

[http://www.csie.ntu.edu.tw/~pangfeng/System%20Programming/Lecture_Note_2.htm](http://www.csie.ntu.edu.tw/~pangfeng/System%20Programming/Lecture_Note_2.htm)

---

### Post by fancypiper on 2009-12-27
I believe the quick answer to your question is yes.

[Filesystem HOWTO]("http://tldp.org/HOWTO/Filesystems-HOWTO.html")

---

