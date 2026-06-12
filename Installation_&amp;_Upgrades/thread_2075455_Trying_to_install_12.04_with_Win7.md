---
title: "Trying to install 12.04 with Win7"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by clay7 on 2012-10-23
Hello,

I'm trying to install Ubuntu 12.04 from CD on my Win7 laptop. I tried to use the slider to set the Ubuntu partition but it won't slide far enough. So, I clicked on "advanced partitioning tool" and here is what it shows:



Device     Type   Size       Used
----------------------------------
/dev/sda
  /dev/sda1 ntfs   1572 MB    524 MB
  /dev/sda2 ntfs 734268 MB  62417 MB
  /dev/sda3 ntfs  14313 MB  13556 MB

I just want 25 GB for the ubuntu partition. How can I do this?

---

### Post by clay7 on 2012-10-23
I found a good dual-boot partitioning tutorial:

[http://www.youtube.com/watch?v=3HANcetKsqc](http://www.youtube.com/watch?v=3HANcetKsqc)

---

### Post by Mark Phelps on 2012-10-24
Hope I'm not tool late ... but do NOT, repeat NOT, use the slider to resize your Win7 Partition.  While that might work OK, it's more likely to result in filesystem corruption to your Win7 setup, and when that happens, you won't be able to boot into Win7 anymore!

Much better, and safer, approach is to use the Win7 Disk Management utility to shrink Win7.  If it won't let you shrink it much, that's because forcing it to shrink more than that will damage the filesystem.

Once you have it shrunk, do NOT create another partition with the Disk Management tool; instead, leave it unallocated.  

Then, when you go to install Ubuntu, use the "something else" option to create and format partitions.

---

