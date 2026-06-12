---
title: "partitioning"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by avikguru on 2007-10-25
Hi,
I have downloaded Ubuntu 7.10 and want to dual boot with XP. Xp is preloaded and I dont wanna disturb it. I have assigned 12 GB for total ubuntu installation. But have been stuck at partitioning page.. How to partition my harddrive.. I deleted to my XP F drive to get a 12 GB free space.. But what to do next? Please state clearly as I am completely novice in the issue and need Ubuntu just now.. please give a step by step direction.. Is manual partitioning required? Is disk formatting essential(Google say it is )? Pls Pls help me.. 
Looking forward for a quick reply...Thanx in advance..

---

### Post by anuradha.d on 2007-10-25
Hi,

Boot from your Ubuntu CD. After you see the Desktop, there is an icon "Install".

Double click and run it. Provide all the details in the installation process. In the partitioning stage, select manual disk partition option and you will see the hard disk in a graphical view. 

I think it's better you delete all the other partitions that you don't use, (except that xpee partition). Then you can select the free space and create new partitions. And you can specify the sizes for the partitions. Create recommended partitions.

/ - root partition
/home - home partition
SWAP (double the RAM size)

but depending on your need, you can create /var /boot etc. And partition type also should be selected, Best two options would be EXT3 or RaiserFS. 

Then in the next stage, you select the partitions you've create to be formatted. That's it. 

I don't think you will find it difficult to get the installation done, cos Ubuntu has a very user friendly installer today.!! :-)

cheers!

---

### Post by avikguru on 2007-10-25
Thanx, I will try it TOnight...

---

