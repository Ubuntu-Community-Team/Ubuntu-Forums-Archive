---
title: "hard drive partition problem"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by rj_65535 on 2006-10-21
Hi,

    i have a 80 gb harddisk with 6 fat32 partitions.i have windowsxp and 98 installed in first two partitions.inorder to install ubuntu ,i freed up the last partition and split it into 3 - 4 gb fat32 , 5 gb for root and about 570 for swap .everything works fine now,i can access all the data from xp , 98 and ubuntu,

however strange thing is, i can still see the original last partition in xp as before , in ubuntu (disk manager) i can see each of the split up partitions and some other ones as free spaces,

Parition properties
Free Space,not partitioned
4092.38 GiB (free space not available)

Parition properties
Free Space,not partitioned
3.41 GiB (free space not available)

Parition properties
Free Space,not partitioned
5.36 GiB (free space not available)

Parition properties
Free Space,not partitioned
73.99 GiB (free space not available)

is this a probblem ? .how do i fix this.

thanks.

---

### Post by Sef on 2006-10-21
Get [GParted]("http://gparted.sourceforge.net/livecd.php") delete the partitions and then repartition. (Not Windows.)

---

### Post by rj_65535 on 2006-10-22
ran gparted,turns out fat32 parition was not formated,formated it and
everything looks fine.

thanks. :)

---

