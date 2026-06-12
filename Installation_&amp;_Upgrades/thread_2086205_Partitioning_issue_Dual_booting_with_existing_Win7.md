---
title: "Partitioning issue: Dual booting with existing Win7 installation"
date: 2012-11-20
forum: Installation &amp; Upgrades
---

### Post by billayk on 2012-11-20
I have been trying to install ubuntu 12.10 on a single HDD with an existing installation of Win7. I'm having trouble getting gpart to use unallocated space that I have created on the HDD specifically for the linux partitions. The following screen shots show the HDD as seen from windows partition manager and gpart during ubuntu installation respectively 

[http://i.imgur.com/4owbP.png](http://i.imgur.com/4owbP.png)

[http://i.imgur.com/WC4Tb.jpg](http://i.imgur.com/WC4Tb.jpg)

I have tried to find information on how to do this and have seen that a HDD can only have 4 primary partitions. I am assuming that the "unallocated space" as seen in the windows partition manager counts as one of these primary partitions and can be used for the linux files, with extra logical partitions within that space for /root etc whatever it needs. So why am I unable to use this space when it comes to the installation?

 It looks as though gpart is showing that there are actually already four primary partitions plus the "unusable" unallocated space even though windows shows only three partitions plus the unallocated space. What's going on here?

I'm really confused now, I usually just use a fresh install of both windows and ubuntu when I'm going to dual boot but I would really rather not do that in this case. 

Can anybody show me the right way to go about this without losing the Windows installation? Any help is greatly appreciated.

---

### Post by darkod on 2012-11-20
If you see in windows Disk Management, below Disk 0 it says it's Dynamic.

Dynamic disks are MS format and ubuntu can't understand them correctly. So, even if it allows you, you shouldn't install.

You need to convert the disk back to Basic. Officially MS says that only Basic to Dynamic can be done without data loss, and not the other way, but people have reported success with some tools. I don't know exactly, I think EaseUS Partition Manager (or similar title) was one of them. I think it's free on EaseUS website but don't hold my word on that.

In any case, make a full backup before trying this.

You are free to google more about converting from dynamic to basic without data loss.

---

### Post by billayk on 2012-11-20
Thanks, I had no idea there was a difference, only a vague inkling. 

This article on the easeus site runs through converting the disk for anyone else that is interested: [http://www.partition-tool.com/easeus-partition-manager/convert-dynamic-disk-to-basic-disk.htm](http://www.partition-tool.com/easeus-partition-manager/convert-dynamic-disk-to-basic-disk.htm)

I'll have a go converting it with their program but will backup first. 

Thanks for pointing me in the right direction.

---

