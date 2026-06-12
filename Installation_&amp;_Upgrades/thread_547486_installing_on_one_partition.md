---
title: "installing on one partition?"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by Bino on 2007-09-10
I have the following partition set-up on my laptop:

• recovery partition pre-installed on my Vaio
• vista partition
• fat32 file partition for music, files,...
• 20gb fat32 partition for running Ubuntu

I thought I should be fine with this set-up however when installing installing Ubuntu I noticed I need to have a partition for /root and /swap aswell. Since I already have 4 primary partitions I´m unable to create these extra requirements. There for I was wondering if I could install everything on the 20gb partition.

Can I just select the created partition and have ubuntu take care of it itself?
Or Should I perhaps set the ubuntu partition to unused and let ubuntu let it sort out itself (if possible)?

---

### Post by logos34 on 2007-09-10
You need a swap.  And linux root shouldn't be on a fat32 partition (ext3, reiserfs, xfs--anything but fat32, it's an inferior filesystem).  

Install.  Choose manual partitioning and delete the 20 gig fat32.  Create an **extended** partition on the remaining disk space.  Make the following **logical** partitions inside: a 1 gb swap, 6-10 gb root (ext3), and rest to separate /home partition (ext3).  

Get ntfs-3g for linux (write support)
Get fs-driver for windows (r+w to ext2/3)

more info here:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by mikewhatever on 2007-09-10
> **Bino said:**
> Can I just select the created partition and have ubuntu take care of it itself?Or Should I perhaps set the ubuntu partition to unused and let ubuntu let it sort out itself (if possible)?

No. The installer would not be able to create more partitions because of the 4 primary ones you already have. You can delete the &#8226; 20gb fat32 partition for running Ubuntu and then create two logical ones, root and swap. I am afraid the only option is to partition manually.

---

