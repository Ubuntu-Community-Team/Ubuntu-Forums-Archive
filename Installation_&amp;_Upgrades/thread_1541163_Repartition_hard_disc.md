---
title: "Repartition hard disc"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by soasertsus on 2010-07-28
[ATTACH]164851[/ATTACH]

See attached screenshot:

I would like to combine my Linux partition (/sda3) and /sad1 to give me more disc space. I would also like to combine the two unallocated partitions to install a Windows 7 dual-boot with Ubuntu. How would I do that without totally raping my current Ubuntu install?

---

### Post by oldfred on 2010-07-29
You only show a couple of gigs of data in sda1, what is in it (is it /home?) and can you move it to your install? I do not like moving installs left as then the partitioner has to totally move all data. Slightly more risk of data loss.

Of course you should back up everything. I would move your data from sda1 and delete sda1. Then make a new sda1 as your windows, a new sda2 for shared NTFS and possibly a new ext3 partition. You can enlarge the extended partition right and move swap right. If you change too much you have to reinstall grub which you will have to do after installing windows anyway. You may have to edit fstab if any partitions are referred to in it and you delete & recreate with new UUIDs.

After all that it may just be easier to backup and start all over?? You then can set partitions up they way you currently want.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Partitioning basics with some info on /data older but still valid by bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

