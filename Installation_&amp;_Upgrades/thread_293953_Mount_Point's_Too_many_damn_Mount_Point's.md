---
title: "Mount Point's Too many damn Mount Point's"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by mc2k4 on 2006-11-05
My scenario

2 HDD's with 2 partitions on each.

first HDD 40GB has two partitions one with Windows other partition is for file etc..

Second HDD 200GB, two partitions, one is 53 GB and the other is 136GB.

I want to install ubuntu on the 53GB Partition.

Ive partitioned the 53GB HDD further into 510MB for swap. 35GB for ubuntu and another 18GB in FAT32 format for no particular reason.

Now im on the stage where im choosing the mount point.

[SCREENSHOT]("http://img155.imageshack.us/img155/2339/screenshotee9.png")

If you could take a look at the print screen and tell me please if these settings are correct?

22GB partition is 2nd partition on first HDD 
15GB partition is 1st partition on first HDD with Windows
510MB partition is on the second HDD
35GB partition is on second HDD
137GB partition is on second HDD
18GB partition is there in FAT32 format.

Also what is happens if i leave all fields blank except those that need to be used by Ubuntu? I.E Those with /media and /oss?

What does /media/hd.... do? Will this mess up windows and the other partitions?

HELP ME PLEASE IVE BEEN AT THIS FOR A WHOLE 24HOURS!

---

### Post by edwin11 on 2006-11-06
[FONT="Verdana"][SIZE="2"][COLOR="Navy"]Hi mc2k4,

i'm inferring logically here...

HDB is your 40 GB harddisk, therefore you won't want to mess with HDB1 and HDB5.

HDC is your 200 GB harddisk:
HDC5 (137 GB) you do not want to use it for Ubuntu, so you won't want to mess with this as well.
HDC6 (35 GB) This is the partition you want to install Ubuntu on.
HDC7 (510 MB) You want to use this for swap.
HDC8 (18 GB) You want to use this as a FAT32 partition.

/media/hdX is not really a "special" directory (unlike /boot or /home, etc). It's just a mount point. i.e. you will be able to find the files on that partition in that directory when its mounted. However, if you have no need to access your windows files from Ubuntu, then its better to not to have those partitions mounted at all. (Also, even if you want to access your windows files, and hence want those windows partitions mounted, you certainly DO NOT want to re-format them.)

In other words, you should only have

```
[FONT="Courier New"]Mount Point     Size     Partition
/               35 GB    hdc6
swap            510 MB   hdc7
/oss            18 GB    hdc8[/FONT]
```

(i'm assuming that you mean to mount your FAT32 parition on /oss)

The other fields should be left EMPTY (all columns).



HTH,
Edwin
[/COLOR][/SIZE][/FONT]

---

