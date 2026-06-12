---
title: "The disk drive for X is not ready yet or not present"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by bcollier on 2011-06-10
When I upgraded to Natty I started having the following problem.  When my computer boots up before I get to the login screen I see:

The disk drive for /dev/mapper/isw_jiahgag_BlueGene05 is not ready or is not present. 

Continue to wait;  or press S to skip, or M for manual recovery.

I get the same thing for my Backup driver, a seperate 2GB hard drive.  I have a total of 3 hard drives, two 640's that are at RAID O (BlueGene01 below) which I don't get an error message on.  I get the error message on /dev/mapper/isw_jigahgage_BlueGene05 and /media/Backup.

When I try to put in a USB stick, external drive, or Kindle (or iPod touch storage) I get this message:

Unable to mount Kindle

Error mounting:  mount exited with exit code 1:  helper failed with:  mount:  only root can mount /dev/sdd1 on /media/Backup

I'm not even sure where to start with this whole mess.  Could someone give me some pointers?

A couple more things below:


When I try to do fdisk -l I get:

bcollier@BlueGene:~$ sudo fdisk -l
[sudo] password for bcollier: 

Unable to seek on /dev/sda

My fstab is below.  

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# Commented out by Dropbox
# /dev/mapper/isw_jigahgage_BlueGene01 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_jigahgage_BlueGene05 none            swap    sw              0       0
/dev/mapper/isw_jigahgage_BlueGene01 / ext4 errors=remount-ro,user_xattr 0 1

/dev/sdd1 /media/Backup ext4 rw,nosuid,nodev,uhelper=udisks 0 0

---

### Post by wildmanne39 on 2011-06-10
> **bcollier said:**
> When I upgraded to Natty I started having the following problem.  When my computer boots up before I get to the login screen I see:

The disk drive for /dev/mapper/isw_jiahgag_BlueGene05 is not ready or is not present. 

Continue to wait;  or press S to skip, or M for manual recovery.

I get the same thing for my Backup driver, a seperate 2GB hard drive.  I have a total of 3 hard drives, two 640's that are at RAID O (BlueGene01 below) which I don't get an error message on.  I get the error message on /dev/mapper/isw_jigahgage_BlueGene05 and /media/Backup.

When I try to put in a USB stick, external drive, or Kindle (or iPod touch storage) I get this message:

Unable to mount Kindle

Error mounting:  mount exited with exit code 1:  helper failed with:  mount:  only root can mount /dev/sdd1 on /media/Backup

I'm not even sure where to start with this whole mess.  Could someone give me some pointers?

A couple more things below:


When I try to do fdisk -l I get:

bcollier@BlueGene:~$ sudo fdisk -l
[sudo] password for bcollier: 

Unable to seek on /dev/sda

My fstab is below.  

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# Commented out by Dropbox
# /dev/mapper/isw_jigahgage_BlueGene01 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_jigahgage_BlueGene05 none            swap    sw              0       0
/dev/mapper/isw_jigahgage_BlueGene01 / ext4 errors=remount-ro,user_xattr 0 1

/dev/sdd1 /media/Backup ext4 rw,nosuid,nodev,uhelper=udisks 0 0

Hi, try starting your system with out your usb devices plugged in.

---

