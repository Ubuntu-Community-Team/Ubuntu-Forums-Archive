---
title: "Disk-Space full-Help"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-09-09
I am using Vista/ubuntu dual booting, but where my ubuntu is installed is full I want to free more disk space from vista.
Help need.
tks

---

### Post by Cmndr Hippofiralkus on 2008-09-09
Thankfully, Or Sadly, depending on your allegiences, Vista itself has a solution to help with this.
If you enter the Disk Management via the Administrative tools (I'm slightly fuzzy on the details), and right click the drive/partition that Vistas is located on, you can select 'Shrink Partition'. Vista will then tell you by how mcuh you can shrink the partition, but be warned, THIS CAN AFFECT DATA ON THE PARTITION YOU ARE SHRINKING!!!. If you don't get nearly enough, defrag the drive and try again.
Once the partition has been shrunk, you can either format it in Windows under an NTFS format (So both Ubuntu and Windows can share nicely), or format it as EXT3 under Ubuntu.

And i suspect someone else may need to expand on this as the keyboard i am using is awful and hurting my fingers.

---

### Post by Partyboi2 on 2008-09-09
Use the partitioning tool in vista to shrink it down, then boot a ubuntu live cd or gparted live cd and open up Partition Editor (System>Admin>Partition Editor) and resize your existing ubuntu partitions to use the newly created space.

---

### Post by blink0 on 2008-09-09
Well, I'm not such a big expert, but I guess all you need to do is resize the partitions, to "steal" some of vista's partition space and give it to the ubuntu partition.
As far as I know, there are several ways of doing this. On Windows, you have several partitioning programs, such as "Partition Magic", that you can use to do this. On Linux, I guess there are several command line utilities for that purpose, or maybe there is even a nice X program on Ubuntu for that.
Hope I was able to help!

---

### Post by Partyboi2 on 2008-09-09
Since you are using wubi I would suggest following [[COLOR=Blue]this[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?") to increase your virtual disk.

---

