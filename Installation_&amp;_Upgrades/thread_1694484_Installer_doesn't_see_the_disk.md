---
title: "Installer doesn't see the disk"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by lkuczera on 2011-02-24
Hi All. 
I have trouble installing ubuntu on my desktop machine. I had Mint before, reinstalled Win7 and wanted to upgrade to newest release as I didn't use Linux for some time. Basically fdisk can see the disk but installer don't :(

                         cfdisk (util-linux-ng 2.17.2)

                              Disk Drive: /dev/sda
                      Size: 1000204886016 bytes, 1000.2 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 121601

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sda1     Boot    Primary FAT16                          222.09
                            Pri/Log   Free Space                  27645.17
    sda5                Logical   NTFS             []            53242.24
    sda6        NC   Logical   NTFS             []            118943.09*
                            Logical   Free Space                  2.69*
    sda7                Logical   NTFS             []]           800145.02*
                            Logical   Free Space                  2.00*


[IMG]https://lh4.googleusercontent.com/_eEvLBBNfRZ8/TWaVInYDMPI/AAAAAAAAEQU/1UNd9nPw4Lg/s288/Screenshot-Install.png[/IMG]

---

### Post by dino99 on 2011-02-24
follow this little help to prepare your installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by lkuczera on 2011-02-24
I can't create three partitions. I have already extended partition created that I don't want to resize. I have created one primary ext4 partition and swap. Still the same.

---

### Post by srs5694 on 2011-02-24
The link dino99 provided is likely to be useless. There are several problems that can produce the symptoms you report, the three most common being a corrupt partition table, leftover GPT data on an MBR disk, and leftover RAID data on a disk that's no longer part of a RAID array. I've got a [Web page on the first possible cause,](http://www.rodsbooks.com/missing-parts/index.html) although it focuses on one specific sub-cause. Perhaps it will help. If not, or if you need more advice, boot the installer into the "try before installing" mode, open a Terminal window, and type the following command:

```

sudo fdisk -lu

```

Post the results here, being sure to precede the output by a [noparse]```
[/noparse] tag and follow it by a [noparse]
```[/noparse] tag. This command will provide details on the partition table, enabling us to see what's wrong, and offer specific recovery suggestions, if it's either of the first two causes.

---

### Post by lkuczera on 2011-02-24
Maybe thats because extended partition is /dev/sda2 ?
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf91c1807

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      433754      216846    6  FAT16
/dev/sda2        54428220  1953520064   949545922+   f  W95 Ext'd (LBA)
/dev/sda3          434176    50329599    24947712   83  Linux
/dev/sda4        50329600    54427647     2049024   82  Linux swap / Solaris
/dev/sda5        54428283   158416964    51994341    7  HPFS/NTFS
/dev/sda6       158418944   390727679   116154368    7  HPFS/NTFS
/dev/sda7       390732993  1953516161   781391584+   7  HPFS/NTFS

Partition table entries are not in disk order

```

---

### Post by lkuczera on 2011-02-24
I have created extended partition as well but didn't help neither.

---

