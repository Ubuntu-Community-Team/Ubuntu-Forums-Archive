---
title: "Partitioning problems in Preseed"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by nikhilt on 2010-02-16
Hi all,

I am trying to automate Ubuntu v9.04 installs. The method I am using is that I have two Windows partitions on the system initially (sda 1 and 2) and then I copy down the alternate ISO/ preseed.cfg/initrd/grub to sda1 for install onto the other partition sda2. I first delete the sda2 partition to make it free space.

I am not able to get the partitioning scheme in preseed.cfg right. It always gives me a "The installer has detected that the following disks have mounted partitions. Unmount partitions first?" and I always select NO. I cant seem to get this automated? What do I add for this in preseed?

My preseed file is 

```
# Partitioning.........................................................................
#d-i partman-auto/init_automatically_partition select Guided - use entire disk
#Select free spaces as opposed to the entire disk, this will keep the boot partition
d-i partman-auto/init_automatically_partition select biggest_free
#d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string regular
#All files in one partition (recommended for new users)
d-i partman-auto/choose_recipe select atomic 
#partitioning and write changes to disk
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select Finish 
d-i partman/confirm boolean true

```

 Please help!!!

thanks

---

### Post by nikhilt on 2010-02-16
SOLVED:

Use the 
d-i partman/filter_mounted boolean false
d-i partman/unmount_active boolean false

to solve it!

---

