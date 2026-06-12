---
title: "Automatic installation of Ubuntu-12.04.1-server-amd64 OS through Kickstart"
date: 2014-05-28
forum: Installation &amp; Upgrades
---

### Post by sudhir-kumar1 on 2014-05-28
I am trying to perform automatic installation of Ubuntu-12.04.1-server-amd64 OS into supermicro server through kickstart. This server has two physical disk attach. But at this process i am getting "No Root file system is defined" error at Partition Disks screen. Below is the piece of code i added for Partition in Kickstart.cfg file.
 
part /boot --fstype ext4 --size 100 --ondisk sda
 
part / --fstype ext4 --size 10000 --ondisk sda
 
part /var --fstype ext4 --size 10000 --ondisk sda
 
part swap --size 1024 --ondisk sdb

---

