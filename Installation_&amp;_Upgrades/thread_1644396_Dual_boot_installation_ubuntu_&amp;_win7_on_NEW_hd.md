---
title: "Dual boot installation ubuntu &amp; win7 on NEW hdd"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by Shishant on 2010-12-13
Hello,

I want to know how should I install for dual boot on new harddisk, [_because in my previous_]("http://ubuntuforums.org/showthread.php?t=1619681") new harddisk win7 formatted it as a dynamic drive (partition) which cant be read by ubuntu.

---

### Post by Quackers on 2010-12-13
What I would do is install Win 7 first. Then boot into Win 7 and check how many PRIMARY partitions it has created. You can do this in the disk management console. If Win 7 has created 3 or less primary partitions you are ok.You can then reduce the size of your C: partition by right-clicking on it and selecting "shrink". This will give you free space for Ubuntu to install into.
If Win 7 has created 4 primary partitions you will need to delete one of them (backup first, if necesary) and if needed then reduce the C: drive size to give free space for Ubuntu.
The new extended partition (and root/swap partitions) can be created in the Ubuntu installation by selecting the manual option in the partitioning stage.
But don't create another primary partition (other than the extended partition).

---

### Post by marin123 on 2010-12-13
or you can select on win 7 installation that it installs on just half (or as much as you want) of the partition and then later on you dont have to shrink win 7 drive space...

---

### Post by Shishant on 2010-12-13
Space is not an issue for me, My new hdd is 2tb. My problem is that last time when I installed win7 first and then was trying to install ubuntu, ubuntu was not detecting partitions correctly and many on forums said its because the disc type is "dynamic" (Img: [http://i52.tinypic.com/v83nyp.png](http://i52.tinypic.com/v83nyp.png)) 

I want to know, in this new hdd how should I install, so that I dont have to convert disc type to basic later.

---

### Post by Quackers on 2010-12-13
With your previous problems it is likely that Win 7 created 4 primary partitions. This is the maximum an any disc using mbr. If you try to create a 5th primary partition Windows will change all of its partitions to "dynamic" which means that Ubuntu won't see the disc.
It is vital to check how many primary partitions Win 7 has created once it is installed.

---

### Post by Shishant on 2010-12-13
> **Quackers said:**
> With your previous problems it is likely that Win 7 created 4 primary partitions. This is the maximum an any disc using mbr. If you try to create a 5th primary partition Windows will change all of its partitions to "dynamic" which means that Ubuntu won't see the disc.
It is vital to check how many primary partitions Win 7 has created once it is installed.
In total I want 6 partitions NTFS and 2 for ubuntu (for / and /swap) so can you please guide how should I install?

---

### Post by Quackers on 2010-12-13
Install Win 7
Boot it and go to disk management console.
See how many primary partitions are there.
If 3 or less create an extended partition and create all other required NTFS partitions as logical partitions within that extended partition, but also leaving space for your Ubuntu partitions.
If Win 7 has created 4 primary partitions you will need to delete one then do as above.

It is possible that Win 7 will use all your disc by default. If it does you will also need to resize a partition before creating new ones.

---

