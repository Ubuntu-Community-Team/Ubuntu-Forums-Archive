---
title: "Partition disappeard"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by escgoat on 2012-11-27
Hi guys, about 3 years ago i installed Ubuntu alongside XP SP2. When i logged into Windows i noticed that one of my partitions were missing. I was frustrated and ended up formatting the entire drive. Now after 3 years, i want to try Ubuntu again(12.04). And my worry is that i will end up with another missing partition.   Is this avoidable? If it is, what can i do to make sure it doesnt happen? What precautions should i take when installing Ubuntu alongside XP SP2? Even if i followed the instructions, is there still a chance of messing up my Windows due to a bug any other technical issue?

---

### Post by darkod on 2012-11-27
Nothing is missing, windows can't recognize linux partitions. So, you will not see them in My Computer, and you don't need to see them there.

Is it a problem for you if the partitions don't show in windows? It's not a good idea to let windows write on your linux system partition anyway, it can mess it up.

---

### Post by escgoat on 2012-11-27
> **darkod said:**
> Nothing is missing, windows can't recognize linux partitions. So, you will not see them in My Computer, and you don't need to see them there.

Is it a problem for you if the partitions don't show in windows? It's not a good idea to let windows write on your linux system partition anyway, it can mess it up.

 It was a windows partition that was missing. I had three partitions in windows, only two were there in windows after i installed Ubuntu. Is this supposed to happen?

---

### Post by darkod on 2012-11-27
Unless you deleted it so you can install ubuntu in its place, no. All ntfs partitions should show up correctly in windows. And they will show in ubuntu too because it can read ntfs partitions.

Of course, if you delete one partition to make space on the disk and install ubuntu, that ntfs partition doesn't exist any more and will not show in windows or in ubuntu.

Also, some partition in windows are hidden, so they might exist but not show in My Computer.

---

### Post by escgoat on 2012-11-27
Ok thanks. Im trying to install Ubuntu alongside xp now. If i choose the &quot; Install Ubuntu alongside windows&quot; option, how will this affect my windows partitions? I have four partitions in windows, three of them have data that i need. The other is empty. I dont want anything to happen to those three partitions and the data on them. What should i do? If i choose "install Ubuntu along side windows" does it use free space of my hard drive?

---

### Post by darkod on 2012-11-27
If it's a partition, no, it doesn't use it. Even if it's totally empty.

In order to be used, you need to delete the partition, so that in Disk Management it shows as Unallocated (or Unpartitioned) space.

After that, when you use the Install Along Windows it will use this space automatically creating the / (root) and swap partitions into it as logical partitions (it does that automatically).

---

### Post by escgoat on 2012-11-27
> **darkod said:**
>  
In order to be used, you need to delete the partition, so that in Disk Management it shows as Unallocated (or Unpartitioned) space.


 If i use this method, should i select install ubuntu alongside option or "something else" option and select that partition?

---

### Post by darkod on 2012-11-27
The Install Alongside uses the largest unallocated space it can find and installs ubuntu on it.

The Something Else is for manually creating the partitions yourself. It allows better control and more flexibility (like installing with separate /home partition etc). I always recommend the manual method but the decision is up to you. But with this method you will have to create all the partitions you want to use, from that unallocated space.

---

### Post by escgoat on 2012-11-27
Deleted partition in windows and now its free space, not unallocated. Is this fine?

---

### Post by darkod on 2012-11-27
Different OSs call that space differently, free space, unallocated, etc. The main point is that it does not belong to any partition. If you deleted the partition, it should be fine.

If you don't have unallocated space the ubuntu installer will not even offer Install Alongside option since it has no space to create the partitions. Like that you can know if something is wrong.

---

### Post by escgoat on 2012-11-27
I installed Ubuntu. Everything went well. Surprisingly i can access my windows partitions and files within Ubuntu.Except for the partition i dedicated for Ubuntu. And i didnt import anything either. Did i do anything wrong?

---

### Post by darkod on 2012-11-28
Anything you want to access on the ubuntu partition is under Filesystem. You will not see it listed together with the other partitions in the Devices section. Only partitions not belonging to ubuntu are listed there.

---

