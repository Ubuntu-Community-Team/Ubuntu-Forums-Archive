---
title: "Partitioning: Can't allocate freespace before Linux Partition"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by Justin312 on 2008-08-24
So I've been trying out linux, and I think I've decided I like it more, and want to allocate more space to it. 

I thought this would be fairly simple. I popped in the live CD, opened-up GParted, shrank my NTFS partition, and then.... tried in vain for what now seems an eternity (also with QTparted and Knoppix) to make my extended linux partition which contains my root and swap partitions use the free space which is graphically right there!

I give-up and am very frustrated with this. Can anyone tell me why I can't use this freespace or more importantly how I can extend this partition? I don't have a large drive and don't really want to create a separate partition for use - I want to keep my drive partitioned cleanly in two - one NTFS - one Extended with my root/swap. 

I've included a screenshot with GParted open (not from LiveCD). 

Would really appreciate understanding how I can add more space to my linux partition. I've installed enough programs that I really don't want to install from scratch. 

This was the closest I found on the forums to my question ([http://ubuntuforums.org/showthread.php?t=850741&highlight=partition](http://ubuntuforums.org/showthread.php?t=850741&highlight=partition)) but it doesn't quite answer my question nor does it seem like that is the process I should have to undertake.

Thanks for any help:




         Justin

---

### Post by Pumalite on 2008-08-24
You are behind an extended partition. You have to delete sda2 and then extend. Backup everything first.

---

### Post by cmat on 2008-08-24
You would move the partition into the free space and then expand the trailing end of it.

---

### Post by Justin312 on 2008-08-24
Thanks for the help.

If I make the freespace available large enough to copy my current extended partition to, can I use GParted to copy my extended partition to this freespace, then delete that extended partition, then rename to the same thing, then expand to the freespace and life will be peachy? 

Or else, should I be using a utility like what is mentioned in that other forum post? 

Thanks -

---

### Post by SkonesMickLoud on 2008-08-24
In order to do what I think you want to do, you'll have to shrink your NTFS partition so that your unallocated space between the NTFS and the extended partition is **exactly** the same size as the logical partition that houses Ubuntu.  Then follow the instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=599599](http://ubuntuforums.org/showthread.php?t=599599)

Pay close attention to that thread as "dd" can easily delete your data.  If you have any questions about it, **ask**, either here or in the thread I linked.

After that, boot into your copied installation to make sure it works (edit grub accordingly).  If it all works, you can delete /dev/sda5 and grow your new partition with GParted, which will also take a while.

---

### Post by Justin312 on 2008-08-26
Thanks to everyone who helped me out. Used Partimage to do this. Succeeded - mostly - I put up a new post with the issue I'm having now but overall the technique should work.

---

