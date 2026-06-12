---
title: "ubuntu partition resizing/moving help"
date: 2013-06-29
forum: Installation &amp; Upgrades
---

### Post by ltkenbo on 2013-06-29
So when I installed ubuntu on my windows machine I shrunk the windows space, then partitioned 3 partitions, / (root), /home and swap. I am migrating from windows 7 so my plan was to move chunks of files over to my /home partition until it was full then shrink the windows volume and continue. I shrunk my windows volume the other day by 200 gb and was planning to add this space on to my /home partition, however because of the partition order, my root partition is sitting in between the unallocated space and the /home partition. 

In the attached picture sda2 is windows partition, grey obviously the unallocated space, my root partition for ubuntu is the tiny blue one, sda6 is the /home partition and red the swap. I would like to add the unallocated space to sda6. What would be the easiest way to fix this, especially considering I am planning on shrinking more and adding more to home in the future.

---

### Post by fantab on 2013-06-29
It may be possible to add 'unallocated space' to '/' partition then move it to /home. However it is not safe for your Data, plus it may be time consuming. Moreover it is not Recommended to add/remove space from the left of partition, ie the beginning of the partition.

What you can do safely is redo your partitions. Back up all your DATA, preferably externally, delete all partition including those of Ubuntu, shrink your Windows partition to as much as you want. Then create new partitions and reinstall Ubuntu.

Or 

For now create a new partition from the 'unallocated space' and format it as ext4. It will be simple linux partition without any mountpoint set. You can use this partition to store your data. You can manually mount it from 'file browser'... or use fstab to mount it at system startup.

Partitioning is not something we do all the time so if you plan your partitions well and re-install Ubuntu it will be worth the effort and far more cleaner than moving space around.

My two cents...

---

### Post by p-dh on 2013-06-30
Hmmm... It doesn't look like your picture from gparted gives all the info needed. Either you are using gpt for your partitions (which is what it looks like) or you have mbr partitions with your linux partitions in an extended partition. If it is the first, you could boot up with a LiveCD and use gparted to move the root partion over and then resize the home partition to take up the unallocated space. I've done that a lot without losing data, but, as fantab noted, backing up is always a good thing to do. 
If gparted is showing an mbr partition, you will want to follow fantab's advice - backup your Ubuntu data and reinstall.

Peace,
Paul :cool:

---

### Post by Bucky Ball on 2013-06-30
Use Win software for manipulating Win partitions, Linux for Linux.

---

### Post by oldfred on 2013-06-30
You can just leave it as a partition and mount it as a data partition. If you want to make it more like it is part of /home you can link folders into /home.

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

