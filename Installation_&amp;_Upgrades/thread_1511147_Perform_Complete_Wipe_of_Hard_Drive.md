---
title: "Perform Complete Wipe of Hard Drive"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by Infinitas on 2010-06-16
I've recently  tried to upgrade my server to Ubuntu 10.04 with little success. I was previously using LVM on top of mdadm RAID1. I'm having trouble with some residual data/partitioning on the drives make formatting them fail. Is there a way to completely wipe all formatting, LVM and mdadm information off of a drive? I don't need to zero every bit on the drive or anything like that if I don't have too, I'm just really frustrated right now and am considering buying new drives to fix the issue. How do I make these drives like they were the day I got them?

---

### Post by dino99 on 2010-06-16
[http://linux.die.net/man/8/mdadm](http://linux.die.net/man/8/mdadm)

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by dabl on 2010-06-16
> **Infinitas said:**
> 
 How do I make these drives like they were the day I got them?



One hard drive at a time (so it is "/dev/sda"), from a booted Live CD:

```
dd if=/dev/zero of=/dev/sda bs=512 count=1
```

The next thing you'll have to do is use GParted and make a new partition table.  Choose "MS-DOS" as the partition table type, unless you are sure you need something else.

Once the partition table is created, you are ready to partition and/or format the drive.

---

### Post by Infinitas on 2010-06-16
Thank you for your responses. I guess in my frustration with the problem I've made the age old mistake of not including enough information. I've already tried the following, taken from [http://tldp.org/HOWTO/LVM-HOWTO/initdisks.html]("http://tldp.org/HOWTO/LVM-HOWTO/initdisks.html")

> 
If you get an error that LVM can't initialize a disk with a partition table on it, first make sure that the disk you are operating on is the correct one. If you are very sure that it is, run the following:

DANGEROUS:
The following commands will destroy the partition table on the disk being operated on. Be very sure it is the correct disk.

```

# dd if=/dev/zero of=/dev/diskname bs=1k count=1
# blockdev --rereadpt /dev/diskname

```


I don't remember now if I did that to both drives, or my /dev/md0 that is made up of /dev/sda and /dev/sdb. At any rate, it didn't destroy the RAID1 that I had set up. I've also tried all sorts of ways to repartition the drives, and keep getting errors when I try. It may be that I have one bad drive in the array, but I'm not sure.

At any rate, I'll try the above again on each drive separately and see what happens. While I'm confident that will destroy any partitions created, will it destroy the LVM and mdadm on the drives?

---

### Post by dabl on 2010-06-16
> **Infinitas said:**
> 

 will it destroy the LVM and mdadm on the drives?



Oh yes.  You said "make these drives like they were the day I got them".  You didn't get them with LVM or mdadm.  ;)

---

### Post by jruberto on 2010-06-16
[http://www.dban.org/](http://www.dban.org/)  Grab DBAN, make a boot disc, boot from it, hard drive(s) fully wiped.

---

