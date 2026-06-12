---
title: "Uuid?"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by tropdoug on 2008-08-23
anyone know how to find out the uuid information of my sdb1 disk (which is my /home) so that I can add it into the fstab for autobooting?

---

### Post by Partyboi2 on 2008-08-23
Open a terminal 
```
 ls -l /dev/disk/by-uuid
```

---

### Post by meindian523 on 2008-08-23
or ```
blkid
```

---

### Post by sisco311 on 2008-08-23
or
```
sudo vol_id -u /dev/sdb1
```

---

### Post by meindian523 on 2008-08-23
PartyBoi's command is the only one that doesn't need a sudo privilege.

---

### Post by tropdoug on 2008-08-23
You guys are fantastic, how do you remember all this stuff? 

Okay got that now. Next question is it possible to 'name' the various partitions (and disks) I have so that I can make some sense of this?

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4eab4176

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3888    31230328+   7  HPFS/NTFS
/dev/sda2            3889        6797    23366542+  83  Linux
/dev/sda3            6798        9729    23551290    5  Extended
/dev/sda5            6798        9602    22531131   83  Linux
/dev/sda6            9603        9729     1020096   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3657373

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9352    75119908+  83  Linux
/dev/sdb2            9353        9729     3028252+   5  Extended
/dev/sdb5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x170a8ae2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    c  W95 FAT32 (LBA)
```


sda1 is the soon to be dumped XP but I need to keep it just awhile yet.

sda2 is my / partition

sda 3 I am not sure about??? 

sda 5 is an empty formatted partition ext 3 for data storage

sda 6 is swap space



sdb1 is my /home disk

sdb2 I dont know how that got there, unless it is part of the formatting process

sdb5 is swap place, but again I dont kow how I got that, or why? as I use this didk purely for my data files. because its a physical disk, does it require the swap to work correctly?

sdc1 is my backup external drive - storage only. Not sure why its a fat fs though I thought I had reformatted it too ext3 ... hmmm 

I must appear very un knowledgable, but I am sure you can see why I am confused.

---

### Post by meindian523 on 2008-08-23
Extended partitions are just special cases of primary partitions in that they can "contain" other partitions,which are sda5,sda6,etc.
They help in making the possible number of partitions more than the four primary ones,though they also take up one of the available primary partition slots(that is if there is one primary partition and one extended partition on your hard disk,you have used 2 out of your four possible primary partitions)
Also,you can only create 1 extended partition.

And about putting your /home in the fstab,just follow the format already there.

---

### Post by meindian523 on 2008-08-23
In your case,the entry would be
<The UUID you found from the commands we posted above> /home ext3 relatime 0 2

---

### Post by tropdoug on 2008-08-23
Thanks meindian523 

Thjat makes things a little clearer. I was hoping though that I might be able to sort of rename the partitions without distroying the data so that for instance 

/dev/sda2  could be renamed to /dev/sda2rootpart 
and /dev/sdb2 could become /dev/sdb2homepart 

this way a newbie like myself, would have both the correct identifier as in the sda or sdb etc, and also a word that describes what it is for. Then down the track when learning this new language has sunk in I could drop the words off the end. Does that make sense?

---

### Post by Partyboi2 on 2008-08-23
Maybe [[COLOR=Blue]this[/COLOR]]("https://help.ubuntu.com/community/MoveMountpointHowto") will help

---

### Post by gatenby_jp on 2008-08-23
dont think it is critical to have uuid you should be able to add the following line to your fstab


/dev/sdb1       /home   ext3    defaults                        0       2

however you can only do this if there is nothing inside the existing /home direcory

---

