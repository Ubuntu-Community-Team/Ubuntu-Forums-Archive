---
title: "no root partition"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by bbjimmy on 2006-12-01
](*,)  I messed up my installation big-time and am attempting to re-install Ubuntu edgy ... When I select the partitions ... one for "/" and one for swap, the installed errors stating that there is no root partition. ](*,)  This wall is getting painful ... H E L P

---

### Post by tommcd on 2006-12-01
Make sure you select ext3 as file system for root. Also, if ubuntu is the only OS on the machine, set the boot flag to on. Can't remember off hand what other options there are for the partitions. If you will not be setting up a seperate /home, you can just select the option to automatically create the partitions instead of manually editing the partition table. This will automatically create /root.

---

### Post by bbjimmy on 2006-12-01
*Make sure you select ext3 as file system for root*

I did that ... I am going to try removing the exst3 partition and creating a blank one and see if this works.


](*,)

---

### Post by bbjimmy on 2006-12-01
That did it! I had to blow away the old partition and create a new ext3 partition for root ... it is now installing ... this is great, I am posting from the computer while it is installing the OS! 


:)

---

### Post by sudden8 on 2006-12-02
I had the same problem here - while attempting to partition and specify root partition, I would receive the error message stating no root partition.  The original partition was formatted ext2.  I circumvented the problem by using other software to format the partition in format ext3 BEFORE I attempted to run the Ubuntu installation procedure to install Ubuntu on that partition.

---

