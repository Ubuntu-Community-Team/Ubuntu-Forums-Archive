---
title: "Please help my harddisk is 96% full"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-06-04
Hello gurus please help me, my harddisk is 96% full,I have vista installed , I am using dual booting, the harddisk part where vista is installed has big free place, how can I extended the part of Ubuntu part of the harddisk.
move some free places from vista harddisk to ubuntu ?
Thanks

---

### Post by chriskin on 2008-06-04
i might be too naive, but i do not think you can do something like that without formating

i don't know, let those with more experience answer for sure

---

### Post by jonom on 2008-06-04
You can use a partition editor to resize your partitions. 

Gparted is pretty good. There is a LiveCD available for download: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) 

Don't forget to backup anything important!

---

### Post by wolfen69 on 2008-06-04
[PartedMagic]("http://partedmagic.com/wiki/PartedMagic.php") is also very good.

---

### Post by avtolle on 2008-06-04
Be aware that one adds additional "room" on a linux partition at the end, not the beginning; thus, merely creating a smaller Vista partition will not necessarily give more room to expand the Ubuntu partition. If this is the case, as I fear it may well be, once the Vista partition is resized, to enlarge the Ubuntu partition may well require backing up externally your /home folder and other files, reformatting the empty space plus the existing Ubuntu space, reinstalling Ubuntu into the enlarged partition, and restoring the /home folder. Just be aware this is a real possibility.
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning) for some general information on partitioning, etc.

---

### Post by CameO73 on 2008-06-04
Just a reminder: **backup any data** on your Vista/Ubuntu partitions **before resizing** them! I've seen resizing gone bad enough times to know this is important advice!

---

### Post by avtolle on 2008-06-04
> **CameO73 said:**
> Just a reminder: **backup any data** on your Vista/Ubuntu partitions **before resizing** them! I've seen resizing gone bad enough times to know this is important advice!
+1 on this; also, defrag the heck out of your Vista partition before resizing it.

---

