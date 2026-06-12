---
title: "Can't Install"
date: 2005-11-14
forum: Installation &amp; Upgrades
---

### Post by newuser111 on 2005-11-14
I set up a primary ext3 partition on my harddrive (20gb) but when running the ubuntu installer it will not let me chose any option beyond the partitioning screen, but I dont need to use partitioning, any other option past it just shows the partitioning screen

is there a problem?  cant ubuntu install to ext3 partitions like other linux distros?  I dont really want to use the ubuntu partitioning tools, partition magic is much more safer

---

### Post by yesplease on 2005-11-14
You have to mount your partition in the install procedure. You do this by selecting the right partition and answer some questions. There are some instructions on mounting in the last 2 posts in this thread: [http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652) 

I doubt that Partition Magic is safer than the Ubuntu tools, but since you have made a partition with it you might as well use it.

---

### Post by linbetwin on 2005-11-14
Why don't you delete your 20GB partition and let Ubuntu repartition it automatically? It will also create a swap partition and it is completely safe. ext3 is the default fs in Ubuntu.

---

### Post by yesplease on 2005-11-14
@ linbetwin: Partition Magic may get confused when you delete partitions it made. I am not sure about this, perhaps Partition Magic is improved on that issue in the last years.

---

### Post by linbetwin on 2005-11-14
[quote=yesplease]@ linbetwin: Partition Magic may get confused when you delete partitions it made. I am not sure about this, perhaps Partition Magic is improved on that issue in the last years.[/quote]
 
My suggestion was to let the Ubuntu partitioner delete the partition and create / and swap.

---

