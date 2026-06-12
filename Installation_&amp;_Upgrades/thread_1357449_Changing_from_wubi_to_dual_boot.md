---
title: "Changing from wubi to dual boot"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by Bodhibear420 on 2009-12-17
Hey all,
 
I have been running Ubuntu on wubi to get a taste to see if I like it.  Well, the verdict is in and I want to officially set up for a dual boot.  I plan on having a NTFS partition for XP, an Ext3 for Ubuntu, a small swap and a large Ext3 /Home for common/shared files using the FS-Drive program.  Here's my question, when I go to partition all of this, is the partition program from the live disc install "intuitive" enough to set up partitions only where there is free space so it doesn't clip off anything from the already installed XP or should I go through the whole process of moving that to an external disc, setting the partitions and then moving everything back?  Thank you

---

### Post by leprkhn on 2009-12-17
Assuming you already have XP installed, and free space available on the hard drive, the Ubuntu installer will give you the following options:
Install Ubuntu next to XP using the free space available.
Resize the XP partition and install Ubuntu onto the (now larger) free space.
Erase all existing partitions and install Ubuntu only.
Manually partition your drive (ie do it yourself).

If you already have XP installed (if you are going to dual-boot i would recommend installing Windows first), and have free space available, i'd tell the installer to go with the option that just uses already existing free space.

---

### Post by darkod on 2009-12-17
> **Bodhibear420 said:**
> Hey all,
 
I have been running Ubuntu on wubi to get a taste to see if I like it.  Well, the verdict is in and I want to officially set up for a dual boot.  I plan on having a NTFS partition for XP, an Ext3 for Ubuntu, a small swap and a large Ext3 /Home for common/shared files using the FS-Drive program.  Here's my question, when I go to partition all of this, is the partition program from the live disc install "intuitive" enough to set up partitions only where there is free space so it doesn't clip off anything from the already installed XP or should I go through the whole process of moving that to an external disc, setting the partitions and then moving everything back?  Thank you

If you want separate /home partition you will have to use Manual option. The automated process creates just the necessary / and swap.
Remove wubi from add/remove programs like any other windows app.
If you have the rest of the drive as another ntfs partition, delete it from within windows. If it's unallocated space, great.
When you start the install, at step 4 select Manual and create your partitions. I advise you to calculate the size you want in advance for each partition and depending on your unallocated space.
If you need more specific instructions, ask.

---

