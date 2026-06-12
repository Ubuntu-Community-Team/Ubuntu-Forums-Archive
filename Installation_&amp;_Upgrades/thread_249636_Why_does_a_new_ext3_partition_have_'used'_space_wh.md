---
title: "Why does a new ext3 partition have 'used' space when it is empty?"
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by boon on 2006-09-02
I have partitioned a new external hard drive into a number of partitions, fat and ext3.

One thing puzzles me. In my ext3 partitions I which are 77.62gb in size, they show in gparted as 1.40gb used and 76.23 unused.

What is this 1.4gb used space? There is nothing in the partitions at all except a lost+found folder (which is empty). I checked hidden files and there are  none of those either. These are freshly formatted partitions, shouldnt they be empty?

By contrast a fat32 partition sized 10.13gb shows 10.12gb empty.

---

### Post by meng on 2006-09-02
ext3, which is essentially adding journaling to ext2, has a higher baseline space requirement. The benefit is that you can recover from a crash better. fat32 has no journaling.

---

### Post by boon on 2006-09-03
> **meng said:**
> ext3, which is essentially adding journaling to ext2, has a higher baseline space requirement. The benefit is that you can recover from a crash better. fat32 has no journaling.

Thanks for your reply, that explains it for me. 

By the way I might mention that there appears to be a bug in the gparted program when using Ubuntu 6.06 as a livecd to resize and make partitions.

I successfully downloaded and made use of the gparted livecd instead:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

This is only a 30mb download and easily burns onto a CD for the purpose.

This resource among others was also useful:

[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

It takes a little messing about to get your disks and partitions the way you want but gparted is easy and intuitive to use. 

Each disk you have seems to only allow four 'primary' partitions with just one of these primary partitions being allowed to be made 'extended' and then divided into additional 'logical' partitions. Once you understand this schema you can get as many partitions as you like.

Of course, when using gparted you do have to be careful not to accidentally delete or format a partition which contains valuable data. Backups are prudent...

---

### Post by deanjm1963 on 2006-09-03
ext3 adds a "buffer" space between files, average format of 5%. it helps to prevent file fragmentation, so when files are overwritten, e.g. system files especially, it gives them a little room to grow.

---

