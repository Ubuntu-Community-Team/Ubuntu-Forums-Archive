---
title: "Manual disk partitioning via preseed"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by boulderguy on 2011-08-05
Esteemed forum members,

I'm trying to setup an unattended installation of Ubuntu 10.04.2 LTS Server x64 using the preseed config file and I've got to the point of partitioning the disks which is where my automatic install stops. My disk partitioning requirements are quite specific and require selecting the manual partitioning method. Here's how I need my boot drive to be partitioned - 

#1 Primary 100GB (Bootable) XFS
#2 Primary 100GB XFS
#3 Primary 100GB XFS

So accordingly, the preseed config I have looks like this for the partitioning section -

```
### Partitioning ###

d-i partman-auto/init_automatically_partition select Manual
d-i partman-auto/disk string /dev/sdb

# Specify the method to use
d-i partman-auto/method string regular

# If one of the disks that are going to be automatically partitioned contains an old LVM 
#configuration, the user will normally receive a warning. 
#This can be preseeded away...
d-i partman-lvm/device_remove_lvm boolean true

d-i partman-auto/expert_recipe string \
 boot-root :: \
 99900 5000 100000 xfs \
 $primary{ } $bootable{ } \
 method{ format } format{ } \
 use_filesystem{ } filesystem{ xfs } \
 mountpoint{ / } \
 . \
 99900 5000 100000 xfs \
 $primary{ } \
 method{ format } format{ } \
 use_filesystem{ } filesystem{ xfs }	\
 . \
 99900 5000 100000 xfs \
 $primary{ } \
 method{ format } format{ } \
 use_filesystem{ } filesystem{ xfs }	\
 .
```

But apparently this isnt working and the installer stops at the partitioning page waiting for user input. What am I missing? Any guidance would be much appreciated.

Thanks!

---

