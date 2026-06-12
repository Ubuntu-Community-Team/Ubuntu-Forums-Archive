---
title: "Create LVM through Kickstart using percentage of disk"
date: 2013-04-17
forum: Installation &amp; Upgrades
---

### Post by rix08 on 2013-04-17
Hi I am new here.  trying to create the following LVM with a kickstart .  I will post the details below but I am getting the following error related to the 60% of disk capacity for /  
error is getopt: unrecognized option `percent=60` wondering if someone can help me correct the syntax

         . A ext2 partition for /boot
         . LVM for the whole disk, with the following repartition :     
                 - One LV called "swap" of 3 gb as swap
                 - One LV called "root" as ext4, mounted on / and up to 60% of the disk capacity
                 - One LV called "home" as xfs mounted on / home that fills up the rest

Here is my KS.CFG disk configuration

#Partition clearing information
clearpart --all --initlabel
# Disk partitioning information
part /boot --fstype=ext2 --size=150
part pv.01 --size=1 --grow
volgroup vg00 pv.01
logvol / --vgname=vg00 --size=1 --name=lv_root --fstype=ext4 --percent=60
logvol swap --name=swapvol --vgname=vg00 --size=3072
logvol /home --name=lv_home --vgname=vg00 --size=1 --grow --fstype=xfs

---

