---
title: "Messed up partitions scheme"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by slink on 2007-10-30
Hi. I am attempting to clean install Gutsy while keeping WinXP. The Installer just does not recognize any partitions. Parted from LiveCd just can't start:

```
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Error: Can't have overlapping partitions. 
```

So I started fdisk. I believe that scheme is bad: 2 swap partitions, hda3-4-5 have bad starts-ends.

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc97dc97

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5943    47737116    7  HPFS/NTFS
/dev/hda2            5944        9779    30812670   83  Linux
/dev/hda3            9780        9964     1486012+   5  Extended
/dev/hda4            9873        9964      738958+  82  Linux swap / Solaris
/dev/hda5            9780        9872      746959+  82  Linux swap / Solaris
```

I just need someone that can confirm if this partition scheme is bad and I need to delete partitions /dev/hda2 /dev/hda3 /dev/hda4 /dev/hda5, to be able to install. There is no valuable data on there. Thanks.

---

### Post by Herman on 2007-10-30
Yes, those partitions are definitely very sick and sorry.
You should delete all those partitions but not the Windows partition if you want to keep Windows.  At the very least you should delete that /dev/hda4 swap area, that looks to me like the one that's causing all the trouble.
You can use the Ubuntu installer's partitioner to make new partitions for you when you are installing.
GParted Live CD is also good, or any 'Parted based partitioner, such as QTParted.

For all kinds of information about installing and getting started with Ubuntu look in this website, [COLOR=#3333ff][B][http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

[/B][/COLOR]Regards, Herman :)

---

### Post by slink on 2007-10-30
Thank you very much !

Slink

---

### Post by slink on 2007-10-30
[SOLVED]


It worked! I deleted the wrong partitions with fdisk and installed Gutsy Gibbon. \\:D/

Thanks!

---

### Post by Herman on 2007-10-30
Okay, good! :)

You used fdisk to delete you partitions and clean up your partition table so GParted could 'see' it?
Cool! :KS
 Hey that's an idea that might help some other people around here who complain that they can't install Ubuntu because GParted can't start.

It seems as if some of those people might have possibly used a different partition editor previously that may have left their partition table in a state that is incompatible with GParted.

In many instances they should be able to do something similar to what you did and solve their problem. Not just anyone would be smart enough to figure out how to use fdisk by themselves though, most people would need some help I would imagine.

Thanks slink, I think you have given everyone a useful tip. :)

Regards, Herman :)

EDIT, I'm bookmarking this link, this could help others. Thanks again, slink. :)

---

### Post by slink on 2007-10-31
(g)parted drove a little crazy because it couldn't even list partitions. I read somewhere to try  (x)parted at first, but then fdisk. I followed those simple steps:

[http://www.cyberciti.biz/faq/linux-how-to-delete-a-partition-with-fdisk-command/](http://www.cyberciti.biz/faq/linux-how-to-delete-a-partition-with-fdisk-command/)

I absolutely agree giving fdisk a try after parted failed could save some headaches.

---

