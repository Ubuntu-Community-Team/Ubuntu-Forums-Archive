---
title: "Ubuntu Installation cannot detect my partitions but can be mounted"
date: 2012-11-04
forum: Installation &amp; Upgrades
---

### Post by Sreeram Boyapati on 2012-11-04
I attached a screenshot that will explain pretty much my problem..
i have created those partitions using** mini tool partition **software ...
:confused::confused::confused:

Please help me out.. i have important data in my win 8 cant format it. immediately..

---

### Post by Sreeram Boyapati on 2012-11-04
Gparted Is not Working Btw...

---

### Post by darkod on 2012-11-04
Did you notice it says you have 27 bad sectors on the disk? Gparted can sometimes ignore partitions when bad sectors are involved.

Also, an error in the partition table can make Gparted not show them. I don't know how this mini tool partition software makes the partitions, but usually the windows Disk Management or the ubuntu live cd with Gparted is enough for all your partitioning needs. Using third party software might create the partitions in a strange way, especially if they develop it for windows only and ignore how linux would recognize the partitions.

It might be better to post the terminal output of:
sudo parted -l (small L)

---

### Post by Sreeram Boyapati on 2012-11-04
Yeah I noticed it .. but thats not the case...
i had overlapping partitions 
By running Bootinfoscript  i discovered it..
By removing those partitions.. i was able to do it..

sourceforge.net/projects/bootinfoscript/

deleting those overlapping partitions solved my case ....:guitar:
What should i do about those bad sectors ???

---

### Post by darkod on 2012-11-04
Get a new disk. When bad sectors start to appear, usually it only gets worse. It's only a question of time.

In your place I would make frequent backups in case the disk fails.

---

