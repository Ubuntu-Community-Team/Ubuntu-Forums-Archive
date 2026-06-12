---
title: "Ubuntu 11.10 installation in only one hard drive"
date: 2012-03-17
forum: Installation &amp; Upgrades
---

### Post by ds95 on 2012-03-17
My laptop contains only one hard drive of about 600GB.I want to install ubuntu on a pre -installed windows 7 drive.The problem is the drive has 3 primary partitions and one extended partition.
C: drive - 522.22GB Windows 7 installed and all my data in it
D: drive - 29 GB drivers and applications preloaded (extended)
200 MB drive (obviously for Windows)
One 14.75 GB rescue partition I think
Now I want to create a separate extended partition for Ubuntu with root , home ,swap partitions.
How will I go from here because my C partition contains all the data and music etc too.

---

### Post by raja.genupula on 2012-03-17
you can use Gparted for editing your partition with out losing the data . for more information read this
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by darkod on 2012-03-17
First of all, you need to open windows Disk Management and take a look at your disk. DO NOT shrink windows system partitions with Gparted. It usually works, but many times windows is complaining if other tools touch its system partition.

Also, you can only have one extended partition. You can't create another one now. What you could do, if your partitions C: and D: are next to each other (and they should be), you can shrink C: for how much space you want to allocate to ubuntu, and the logical ubuntu partitions created into that space should automatically combine with D: into the extended partition.

So, first take a look in Disk Management to make sure C: and D: are next to each other. Then use Disk Management to shrink C:, and make sure to shrink it in a way that the unallocated space created is next to D:.

Then you can install ubuntu. It's bext to do it with the manual method and make your own partitions, but some of the auto methods should work too.

---

