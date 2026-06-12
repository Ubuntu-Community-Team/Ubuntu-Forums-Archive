---
title: "Install on whole disk"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by Akina on 2007-05-31
I am about to install Ubuntu I am wondering tho. I want it to use my whole disk but I have a C: and D: Drive.
 I keep all my items I am not willing to lose in my D: Drive for safe keeping ya know.

Heres what I am asking tho. If I was to install Ubuntu to use whole disk will it override my D: Drive as well.

Stupid Partitions :p

---

### Post by jamesjtucker on 2007-05-31
So you are saying that you have one physical drive with two logical partitions (C: and D:)? or two physical drives? Ill assume one drive.
  If you have one physical drive, then you will most likely need to choose the manual partitioning method during the install and delete the C:\ Partition and create a new one for ubuntu there. 
Also, If D: is formatted ntfs, then you will need to install ntfs write support (see: [http://www.linux-ntfs.org/](http://www.linux-ntfs.org/))

---

