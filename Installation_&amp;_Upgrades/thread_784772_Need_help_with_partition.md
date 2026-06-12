---
title: "Need help with partition"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by SafirXP on 2008-05-06
Okay, I've a 300GB drive where I've installed WinXP on 20GB primary partition. About to install Ubuntu using around 10GB and keep the remaining space as a storage NTFS partition.

I read about having the /home partition separate. So I should make a primary partition for / and put /home & swap in an extended partition along with the storage one?

So help... please...

---

### Post by Pumalite on 2008-05-06
This might help:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by louieb on 2008-05-06
> **SafirXP said:**
> ...So I should make a primary partition for / and put /home & swap in an extended partition along with the storage one? ...
Having /home and your data on separate partitions is a good thing. Do what you want.  Having. I have my /home and my data in separate partitions.  

I boot to Ubuntu a lot more that I boot XP. So my data partition uses the ext3 file system. If I I used XP more I'd have to think about using NTFS. 
Seems like using NTFS from Linux is a little less trouble that using ext3 from XP.

---

### Post by ssican on 2008-05-06
See: Resizing a Windows Partition (XP,/,/home,swap):
[http://www.easy-ubuntu-linux.com/resize-windows-partition.html](http://www.easy-ubuntu-linux.com/resize-windows-partition.html)

EDIT 1: Choice:
- Partition 2 -(/) as Primary
- Partition 3 -(/home) as Logical
- Partition 4 -(Swap) as Swap

EDIT 2: On [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)  there is this information: **This guide is for creating a separate /home partition if you already installed Ubuntu without a /home partition (i.e., /home is just a folder inside your / partition).** **_If you have not yet installed Ubuntu but want to create a /home partition before installing (a very good idea, by the way), use this guide_**:[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

---

### Post by SafirXP on 2008-05-06
Thanks for the help! Yeah I got my basic info from the psychocats website.

Will be installing 8.04 tonight, hopefully tommorow I won't be posting here again about partition problems! :)

---

