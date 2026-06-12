---
title: "Partition to ensure home isn't deleted by next reinstall"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by kanolsen on 2010-06-09
How do I ensure that my home partition does not get deleted the next time I reinstall Ubuntu, as I can see there is a choice between formatting the whole drive and manually partition it, but if I reinstall won't I delete the home partition as well?

Thanks in advance
Kanolsen

---

### Post by tim48134 on 2010-06-09
Hi,
When reinstalling Ubuntu, the home partition would only be erased if you choose to format the entire drive. The best thing to do would be to select manual partition. Edit the partition you want to have as root  (by clicking on the partition, then "Edit Partition"); have its mount point as / and format the filesystem to ext4 (or ext3). Then edit the home partition, but do NOT click format. Instead, only change it so that its mount point is /home. You should also have a swap partition, which the Ubuntu installer will automatically use if it exists.
Hope this helps!

---

### Post by darkod on 2010-06-09
> **tim48134 said:**
> Hi,
When reinstalling Ubuntu, the home partition would only be erased if you choose to format the entire drive. The best thing to do would be to select manual partition. Edit the partition you want to have as root  (by clicking on the partition, then "Edit Partition"); have its mount point as / and format the filesystem to ext4 (or ext3). Then edit the home partition, but do NOT click format. Instead, only change it so that its mount point is /home. You should also have a swap partition, which the Ubuntu installer will automatically use if it exists.
Hope this helps!

However, this is only possible if you already have separate /home partition.

From your post it's not clear whether you installed using the guided methods, in which case Home is just a folder in /.

There are procedures to move from a Home folder in /, to separate /home partition but I'm not sure I can find a good link right now.

Once you have separate /home partition on every future clean install you simply use manual partitioning option, you specify your /home partition to be used with mount point /home and DO NOT tick the format box. And that's it.

---

### Post by kanolsen on 2010-06-09
thanks a lot.  I now made the right choices when I reinstalled Ubuntu today, and made a /home partition, so the next time I don't have to manually copy everything to an external harddrive (though I know it advisable to do so). 

Kanolsen

---

