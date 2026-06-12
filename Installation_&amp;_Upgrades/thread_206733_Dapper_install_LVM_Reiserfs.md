---
title: "Dapper install LVM Reiserfs"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by cotcot on 2006-06-30
I want to reinstall Dapper on my hdb. Therefore i created the logical volumes  /dev/Ubuntu/root,  /dev/Ubuntu/swap_1 and /dev/Ubuntu/home. 

Problem is that during install i do not get the choice to select one of these logical volumes as mount points for /, /swap and /home.  
Checking the logical volumes  with gparted gives an orange triangle for error. I think it is this error : debugreiserfs: can not open reiserfs on "/dev/mapper/Ubuntu-root1": No such file or directory.  
 
Any suggestions ?


this is my fdisl -l on hdb : 

  Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          31      248976   83  Linux
/dev/hdb2              32       14593   116969265    5  Extended
/dev/hdb5              32       14593   116969233+  8e  Linux LVM

this is lvdisplay :

 --- Logical volume ---
  LV Name                /dev/Ubuntu/root
  VG Name                Ubuntu
  LV UUID                CFML7H-8FHG-1sYG-Df3m-3TKT-4Vid-3YkeL1
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                20.45 GB
  Current LE             5234
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:0

  --- Logical volume ---
  LV Name                /dev/Ubuntu/swap_1
  VG Name                Ubuntu
  LV UUID                Vw8g3I-Jsqa-VTnK-6ALI-YWrX-dy9t-7pIr9Y
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                1.10 GB
  Current LE             282
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:1

  --- Logical volume ---
  LV Name                /dev/Ubuntu/home
  VG Name                Ubuntu
  LV UUID                4rGktQ-f1An-Fau0-AdYm-Vl9P-aKxL-hIj6er
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                50.00 GB
  Current LE             12800
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:2

---

### Post by cotcot on 2006-06-30
I found out that i have to use the "alternative CD" . The desktop install CD does not give the option to install on lvm. 
Installation was OK. (I installed dapper 3 times before I figured out the correct choices in the advanced mode : see F6 at boot)

A couple of experiences :

The automatic choice of the disk partitioner with LVM is a small logical partition for boot and the rest for LVM. I had to change the logical boot partition to a primary boot partition to get Grub in the choices for the boot loader. 

The disk partitioner chooses ext3 as file system on the logical volumes. I changed it to reiserfs as recommended in the LVM manual. It allows resize of the filesystem on mounted partitions.

I used "desktop machine" as choice for the partitioner in order to get a separate /home volume.

The installation sequence allows to make an account for root. I made one during the first install. After reboot sudo did not work and graphical login as root neither. I redid the installation without making a root account. Sudo is OK now.

---

