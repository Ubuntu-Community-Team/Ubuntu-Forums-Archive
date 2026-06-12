---
title: "Will /home as 2nd partition on 2nd hard drive = loss in performance?"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by Kilgore_Trout on 2008-09-04
I switched completely to linux about 6 months ago, but now I need to go back to a dual-boot with Windows so that I can run AutoCAD 2008.

I have two IDE HDDs in my system, one 30GB and one 120GB.

They are currently partitioned as follows:

30GB(IDE1)
/ (ext3):        10GB
/home (ext3):   ~16GB
swap (swap):     1.5GB

120GB (IDE2)
/AVclub (ntfs): ~110GB

For the dual-boot, I'm considering moving /home to the 120GB drive and adding /windows in its place.  So they would look more like this:

30GB (IDE1)
/ (ext3):        10GB
/windows (ntfs): 12GB
swap (swap):      4GB (upgraded the RAM)

120GB (IDE2)
/AVclub (ntfs):  80GB
/home (ext3):   ~30GB

Will putting /home as the second partition on the second hard drive cause a loss in performance?  Would it be better to reformat that drive with /home as the first partition?

Any suggestions for a more ideal method (performance-wise) of arranging these partitions?

Thanks.

---

### Post by lmno149 on 2008-09-04
[ddo platinum](http://astore.amazon.com/ddo-platinum-20)[eve isk](http://astore.amazon.com/eve-isk-20)[everquest 2 plat](http://astore.amazon.com/everquest-2-plat-20)[ffxi gil](http://astore.amazon.com/ffxi-gil-20)[gw gold](http://astore.amazon.com/gw-gold-20)

---

### Post by kidders on 2008-09-05
Hi there,

> **Kilgore_Trout said:**
> Will putting /home as the second partition on the second hard drive cause a loss in performance?No. Mind you, there's a case to be made (at least in theory) for preferring primary partitions over extended ones, but the *ordering* of partitions makes no difference, afaik.

In 1990, the answer to your question might have been different. For instance, imagine a 20M hard disk with four 5M primary DOS partitions. Accessing the filesystem in the fourth partition would probably have been slower, because ...[LIST]
[*]Partition 4 would necessarily have been physically further from the partition table than partition 1.
[*]Seek times would have been far longer than they are today.
[*]Hard disks didn't have on-board buffers.
[*]Operating systems were less intelligently optimised.
[/LIST]

None of these is true today, so I'd be quite surprised to find even a theoretical performance loss ... let alone a practical one. Factors such as the amount of RAM you have, your choice of filesystem type, fragmentation, and so on are far more likely to have significant performance implications than the logical order of partitions.

Anyhow, I hope you find that sensible/helpful.

---

### Post by Kilgore_Trout on 2008-09-05
Absolutely, that was exactly what I was looking for (and what I was hoping to hear).  

Thanks for the info!

---

