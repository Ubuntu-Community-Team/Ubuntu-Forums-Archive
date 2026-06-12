---
title: "partitioning question"
date: 2005-03-15
forum: Installation &amp; Upgrades
---

### Post by spiderworm on 2005-03-15
Hi,

My friend has a hard drive with a single partition only, FAT or NTFS (cant remember which one) and he wants to resize that partition, create a second partition, and dual boot Windows/Ubuntu.  Is there a free tool that will help him do this?  Thanx in advance for your help.

spiderworm

---

### Post by tmowerman on 2005-03-15
I used a program called qtparted.  You can find it on the knoppix live cd.   I believe it is also available on a standalone system recovery live cd.

---

### Post by Xian on 2005-03-15
[QUOTE=spiderworm]My friend has a hard drive with a single partition only, FAT or NTFS (cant remember which one) and he wants to resize that partition, create a second partition, and dual boot Windows/Ubuntu.  Is there a free tool that will help him do this?[/QUOTE]
Just use the Ubuntu CD. He can do all that during the installation.

---

### Post by spiderworm on 2005-03-15
It will resize the partition without deleting data, like Partition Magic?  The Hoary PR cd will do this for him?

spiderworm

---

### Post by Xian on 2005-03-15
[QUOTE=spiderworm]It will resize the partition without deleting data, like Partition Magic?[/QUOTE]
That's what it is designed to do and it worked fine on my box.
But with partitioning there are no absolute certainties, even with Partition Magic.

Always make back-ups.

---

### Post by Xian on 2005-03-15
[QUOTE=spiderworm]The Hoary PR cd will do this for him?[/QUOTE]
That Hoary CD uses parted for the partitioning tasks, and parted is about as good as Linux has to offer in this category. It is also used by SuSE, Knoppix and many other distros, and there are even GUI's applied to it such as in QTparted. You would either need to go this route or try a Win based tool. I personally prefer the Linux route as I've used both Acronis and PM8 and I've seen them totally wreck my HD geometry. But then again, many people get by just fine with them and use them regularly. 

Like I said...no certainties. :)

---

