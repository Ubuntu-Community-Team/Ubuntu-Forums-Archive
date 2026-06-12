---
title: "removing ubuntu-cant resize partition !"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by dooper on 2010-02-27
[http://i3.photobucket.com/albums/y82/eranu/misc/diskcapture.jpg](http://i3.photobucket.com/albums/y82/eranu/misc/diskcapture.jpg)

Arghhh... i have a toshiba lappy on which  i had ubuntu 8.04 dual booting via grub with vista. 

I repaired the MBR but now  i find i cant get the ubuntu space on the disk back . From the pic its the section which is 38.62Gb.

When i try to delete the partition it says there isnt enough space on the disk.

The lappy has its recovery partition on the hard disk in some format or other so i presume this is the smaller bits?

I am trying to use dskmgmt.msc to manage the disk at present..

tnx

---

### Post by SecretCode on 2010-02-27
That "EISA Config" partition 1.46GB is something I've not seen before. That and the 1.70GB partition at the end can't both be needed for recovery, so I suspect something more is going on.

I'd remove your Disk 1 which has something odd, possibly a badly formed label. 

If you still can't get it right I'd strongly recommend a windows forum! There may be Vista specifics and you may not get the best advice here.

---

### Post by dooper on 2010-02-27
The two small partitions will be to do with the onboard OS/software recovery as supplied with the lappy from new.

---

### Post by Mark Phelps on 2010-02-28
> **dooper said:**
> [http://i3.photobucket.com/albums/y82/eranu/misc/diskcapture.jpg](http://i3.photobucket.com/albums/y82/eranu/misc/diskcapture.jpg) I repaired the MBR but now  i find i cant get the ubuntu space on the disk back . From the pic its the section which is 38.62Gb.


That's correct.  MS Windows can't read Linux filesystems, so it reports their partitions as free space.

Suggest you go to distrowatch.com, download and burn the GParted LiveCD, boot from that.  It will see ALL the partitions.  Just use that to delete the Ubuntu partition.

Then, use the Vista Disk Management utility to expand the Vista partition to take up the free space.

---

