---
title: "raid 5 setup on 9.10 server"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by froghead on 2010-04-03
I am puzzled as to why the size of te RAID 5 array is showing as 500GB, instead of 750GB, which is what I expected

Using ubuntu server 9.10 and would like to use raid 5.
Four disks of the same size, 300 gb.

I have created two partitions on each disk as follows:
```

sda1 #1 primary 250 GB B raid
     #2 primary  30 GB   raid
     
sda2 #1 primary 250 GB B raid
     #2 primary  30 GB   raid

sda3 #1 primary 250 GB B raid
     #2 primary  30 GB   raid

sda4 #1 primary 250 GB B raid
     #2 primary  30 GB   raid

```The #1 partition on each disk was set to bootable. I then created two raid 
devices. I chose three active #1 partitions from and 1 spare for each raid device. I did the same for the 4 #2 partitions.

The Partition details for the RAID devices now look as follows:
```

RAID5 device #0 - 500 GB Software RAID device
         #1       500 GB ext4
RAID5 device #1 -  60 GB Software RAID device
         #2        60 GB ext4

```
I was expecting the size of each of the two RAID devices to be 750GB and 90GB respectively.

Could anybody explain why the smaller size as I am reluctant to continue with the 
installation until I am sure my RAID devices and partitions are setup correctly.

thanks

---

