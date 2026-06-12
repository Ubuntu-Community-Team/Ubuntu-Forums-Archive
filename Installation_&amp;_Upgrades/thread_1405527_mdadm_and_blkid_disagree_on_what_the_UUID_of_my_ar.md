---
title: "mdadm and blkid disagree on what the UUID of my array is..."
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by ljwobker on 2010-02-12
I have a 3-component raid5 array, composed of: /dev/sd[abc]1.  mdadm tells me that the UUID for this array is something *different* than what blkid says it is.

```
root@lwobker-fs:~# mdadm --examine /dev/sd[abc]1 | egrep 'UUID|dev'
/dev/sda1:
     Array UUID : f82a311d:93d4f3a1:cd359611:8b50ce19
    Device UUID : e0b77465:531d19cd:e5609b47:326babe8
   Device Role : Active device 0
/dev/sdb1:
     Array UUID : f82a311d:93d4f3a1:cd359611:8b50ce19
    Device UUID : 2c1050e8:eb321107:f37b8b8a:b9fc56d2
   Device Role : Active device 1
/dev/sdc1:
     Array UUID : f82a311d:93d4f3a1:cd359611:8b50ce19
    Device UUID : f4035780:5bd340e6:21d9468d:f944050b
   Device Role : Active device 2
```but blkid thinks that it's something different:
```

/dev/sda1: UUID="f82a311d-93d4-f3a1-cd35-96118b50ce19" LABEL="lwobker-fs:0" TYPE="linux_raid_member"
/dev/sdb1: UUID="f82a311d-93d4-f3a1-cd35-96118b50ce19" LABEL="lwobker-fs:0" TYPE="linux_raid_member"
/dev/sdc1: UUID="f82a311d-93d4-f3a1-cd35-96118b50ce19" LABEL="lwobker-fs:0" TYPE="linux_raid_member"
/dev/sdd1: UUID="cdf5d475-37c7-48d9-b6a1-5564702e3ccf" TYPE="ext4"
/dev/sdd5: UUID="9a5ba558-3a80-4248-9a08-3178d42b50dc" TYPE="swap"
/dev/md0: UUID="ceeef66c-0caa-4127-a1a2-01de1738da1b" TYPE="ext4"
```

my understanding is that within the md superblock the "array uuid" would be the same as what blkid reports... any ideas here on what I might be missing?  I would have expected to see unique ID's for each device (which I do) and a common ID for the array (which I do) -- but where is the difference between the array UUID and what blkid sees coming from?

---

### Post by jcalcote on 2011-11-08
kinda old, but I'll contribute anyway: The raid array uuid is the one copied around to all devices from which the raid is composed. You'll notice that blkid shows the uuid of sda1,2,3 as all being the same - that's the raid array uuid.

The uuid you're actually seeing on /dev/md0 is the ext4 file system uuid installed on top of the array. This would be much more clearly shown if you had fdisk'd your array and partitioned it into md0p1 and md0p2, and then put file systems on top of both partitions. You'd have unique uuid's for both partitions - but these UUID's would belong to the filesystem, not the array.

---

