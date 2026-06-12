---
title: "Ubuntu Install - Mount Points???"
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by aSystemOverload on 2011-08-03
Hi guys

Just installed Ubuntu and got a little confused about 'mounts or mount points'


I've got 1 * 250 and 2 * 500GB HDDs.  I mounted the 250 as '/' and 1 * 500GB as '/home'.

What should I mount the final 500GB as (and how do I mount it after I've now installed it).  I only want the 500GB as general storage.

Also is it worth repartitioning the 250 with a dedicated section for 'swap' etc???

Any advice welcomed. :)

---

### Post by ajgreeny on 2011-08-03
If you have a separate /home partition setup at install time your / partition only needs to be 10-20GB, not 250GB, but to be sure what's going on can you boot to ubuntu and show the output of the command ```
sudo fdisk -l
```in terminal.

Are these disks real separate disks or just partitions on one large disk?  Windows calls everything a drive which is confusing, but could be either.  The answer will affect the way that I recommend you deal with the current disk or partition setup.

However, to answer one part of your post, if you don't already have a swap partition make one using gparted on a live ubuntu CD, which I suggest you do it by shrinking your huge / partition to the 10-20GB, then if that really is on a separate disk, make a new extended partition of all the unallocated space, and then in that extended partition make a swap partition of about 2-4GB and another new logical partition you can use for data.  If this machine is ubuntu only and not dual booting windows make this data partition ext4 and mount it a boot time by making the mountoint folder with ```
sudo mkdir /media/data
```and added  lines in /etc/fstab
```
# data partition on sdx#
UUID=e2554df2-7e16-4864-97c9-834d8bebecda /media/data ext4 defaults,relatime 0 2
```You can find the UUID with ```
sudo blkid
```and change the sdx# to your own partition device name.  Note lines starting with # are comments and not read as part of the configuration.

if it is to be shared with windows, format to ntfs and use ntfs-config, which you will need to install, to enable mounting the partition.

---

### Post by aSystemOverload on 2011-08-04
I took the easy way out and reinstalled as I'd only just installed the system last week and hadn't made any changes since.  Went with 

250GB
 - '/' 50GB
 - '/home' 50GB
 - swap 5GB
 - unused for now...

I did want to try and get the two 500GBs under raid1, but not a clue how to do that. :-s

and yes three phsyical HDDs 250, 500, 500.

---

### Post by psusi on 2011-08-04
I'd suggest that you put the two 500gb drives in a raid-0 and install the system there, then use the 250 for backups or something.  For that you will need to use the alternate installer.  There's also no need to have a separate /home partition, and if you have plenty of ram ( 2gb+? ) then you don't really need a swap partition either, unless you want to use hibernation.

---

### Post by aSystemOverload on 2011-08-04
Nahhhh, I need the 500GB for media files and I want some redundancy. :)   I can't even get the raid to work, so thats a bust :(

I'll look into that another time, will stick with JBOD.  My issue is now, that root owns the drives and I can't seem to get read-write access :-s

---

### Post by psusi on 2011-08-06
Use sudo chown to change the ownership of the folder to yourself.

---

