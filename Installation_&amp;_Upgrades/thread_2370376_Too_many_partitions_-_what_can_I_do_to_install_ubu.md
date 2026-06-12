---
title: "Too many partitions - what can I do to install ubuntu 16.04.03"
date: 2017-09-02
forum: Installation &amp; Upgrades
---

### Post by freubreu on 2017-09-02
Hey guys, I want to install Ubuntu beside my Windows 7 - for that i created an Unallocated partition (15.26GB) on my Computer. If i want to install UBUNTU i cant click the + ( because i have to many primary partitions, I found out searching for the problem).   I made you an attachment (overview) over my HDD.  Looking forward to your help. Best, Fabian

---

### Post by oldfred on 2017-09-02
the 4 partition limit is one of the very old problems of the now 35 year old BIOS/MBR configuration.
You need to delete or convert one primary partition, so you only have 3 primary partitions. then you can create an extended partition as the 4th primary and the extended acts as an container for an unlimited number of logical partitions.

Many backup vendor utilities partition and delete that. Often that data also is available to download, where other info may not be, depending on vendor.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by gordintoronto on 2017-09-02
See Full Circle Magazine, Issue 41, page 36.

---

