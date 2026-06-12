---
title: "Windows Logical Partition Accidentally Deleted"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by BLaZuRE on 2011-03-21
While this is not fully linux-related, I am looking into recovering my files using Ubuntu.

**The short story:**

A partition containing files has been formatted/deallocated and now appears as 'free space' inside Windows.  These files would like to be recovered since my last backup is weeks old.

**Long story:**

I was trying to allocate a separate partition by shrinking the logical partition, then formatting the freed space as a result of the 'shrinkage' into a new logical partition.  While it was formatting, I realized I was going to have a grub problem on boot (now resolved).  With that in the back of my mind, Windows errored for some reason and said it couldn't format the partition and to Refresh.  I did, my files partition disappeared and so did the separate shrunk space that was supposed to be formatted.  All that space is now FREE SPACE according to windows.  I know my files are still there since I can't imagine anything would write on "Free Space" and some address table was just deleted.

**Question:**

Is it possible to rewrite the table, wrap the partition in NTFS somehow, or somehow mount 'FREE SPACE' inside linux to gain access to the files?  If no other alternative is possible, how can I find a reputable/free recovery tool/program and how can I tell it is safe and will not harm/snoop my system?

---

### Post by Mark Phelps on 2011-03-21
As to free tools, folks around here will recommend testdisk -- but I've not personally had much success using that to recovery Windows files and partitions.

Don't know of any free MS Windows file recovery utilities -- and to use them, you need to connect your drive to a Windows PC.  But if you can do that, you can download trial versions of data recovery utilities from Runtime Software.  You can at least then install and try them to see how well they find your files.

---

### Post by BLaZuRE on 2011-03-21
Thanks, I'll be trying that.

---

