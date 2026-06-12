---
title: "Tips and tricks to run ZFS"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by gratou on 2011-03-27
This is not yet another tutorial on how to install ZFS, but rather a list of hard-learnt or long-sought solutions to some problems I had using ZFS (some of them specific to Ubuntu, some not). One will have to learn the basics of ZFS or Ubuntu elsewhere before reading this. There are lots of great tutorials about.
Sorry is the vocab isn't exactly right, I am still climbing the learning curve.


1) Do not use a raw device, format it instead
=============================================
The reason for this is that if you want to replace a 2TB disk with another 2TB disk, and the sizes differ a bit, and the 2nd one is a bit smaller, ZFS will not accept the replacement. So format the disk and leave a bit of unused space so chances are the next disk will be able to be of the same size.

2) Be careful where you start your partition
============================================
I am unsure I fully grasp the 512/4k-byte sector size issue, but be sure your partition is aligned on 4k so your disk works in optimum conditions.

1-2) How to do it?
==================
Here is how I implement the 2 points above:
```
sudo parted 
>select /dev/sdba
>unit s                      
>mkpart primary ext4 2048 3906248704 
quit
```   

 
3) get the latest version of ZFS
================================
The 10.04 package manager points to an obsolete,unstable version.
```
sudo add-apt-repository ppa:bugs-sehe/zfs-fuse  
```


4) add disks to pools by id rather than device name
===================================================
Ubuntu randomly changes /dev/sdX to /dev/sdY upon reboot (which is a pain) and ZFS trips over when that happens and the pool must be recreated (which is incredibly stupid, so maybe I missed something, but I looked long and hard all over the net). To use IDs:
```
sudo blkid #get ids 
sudo zpool create tank /dev/disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2HFJ1AZ806-part1 /dev/disk/by-id/scsi-SATA_SAMSUNG_HD204UIS2HFJ1AZ807-part1 
```


5) Pools aren't usable upon creation
====================================
Take ownership from root
```
sudo chown -R me /tank 
```


6) Verify the data you copy into the pool copied well 
==================================================
cp doesn't do data verification, you must use rsync
```
rsync -rtv "/media/video/"  "/tank/video" # recursive,time stamps kept,verbose. Add c for checksum-based comparison

```


That's all for now. I hope this can help someone, and I am sure what I wrote above can be improved. Please fire away. 


Also if a script guru could tell what to run to delete files in dirA when they don't exist in dirB (even when these dirs are some levels down in a tree: I want to compare trees, not just directories), my replication routine would be complete. :):)

---

