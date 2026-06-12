---
title: "partition table has errors - how do I fix it?"
date: 2006-03-09
forum: Installation &amp; Upgrades
---

### Post by mogliii on 2006-03-09
Hi,

I have (K)ubuntu 5.10 installed. 30 GB harddrive and I am also using WinXP.

my partition table before all this looked maybe something like this: (except hda1 everything was set by the partitioning program when installing Kubuntu 5.10)

```
/dev/hda1 8,5 GB prim ntfs WinXP
/dev/hda2 5 GB prim ext3 /

/dev/hda4 15 GB extended
/dev/hda5 1 GB logical vfat (fat32)
/dev/hda6 0,5 GB logical swap
/dev/hda7 13,5 GB logical ext3 /home 
```
I wanted to use hda5 to transfer data safely and convenient from win to linux and vice versa. But it didnt work as intended:

Data written in Windows could be read in Linux
Data written in Linux did not exist under Win. But, when going back to linux, data existed.

I tried a lot with mounting and stuff, but the problem remained. 

So I decided to delete the partition and create it new. So I used the WinXP Disk Management to delete the partition. But after that, it looked like this in the extended partition (hda4)

[I]600mb Free space
13,5 Gb /home
240GB Free space
605GB Healthy (Active) but no drive letter or properties available[/I]
(it is really GB. This is not a typing fault) 

So as a next step I bootet Linux to see what it says. And while startup, a error message appeared:
```
fsck.ext3: No such file or directory while trying to open /dev/hda7
/dev/hda7:
The superblock could not be read or does not describe a correct ext2
 filesystem. If the device is valid and it really contains an ext2 filesystem 
(and not swap or ufs or something else), then the superblock is corrupted 
and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>
```
I executed this command but got this error message:
```
e2fsck: Bad magic number in super block while trying to open /dev/hda
```
I continued booting, and except that X fails with an error message and /home is empty, everything is working (internet connection, etc)

Then I tried different partitioning tools to show me the list/resolve the error.

fdisk - shows error or nothing
cfdisk - shows Fatal Error
parted - could give me a list of partitions, but I had to press (I)gnore several times. Output follows further down
sfdisk - I could convince it to give me a table with special options. the list is given below
```
parted output:
Minor              Start         End           Type         Filesystem    Flags
1       0.031                 8578.828            prim           ntfs      boot
2       8581.597           13750.949          prim           ext3
3       13750.950        28615.781          extend       
5       13750.980        14378.488          log             fat32
6       14378.520        27627.407          log             ext3

sfdisk output:

Disk /dev/hda: 62016 cylinders, 15 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/hda1   *        63  17569439   17569377   7  HPFS/NTFS
/dev/hda2      17575110  28161944   10586835  83  Linux
/dev/hda3      28161945  58605119   30443175   5  Extended
/dev/hda4             0         -          0   0  Empty
/dev/hda5      28162008  29447144    1285137   b  W95 FAT32
/dev/hda6      29447208  56580929   27133722  83  Linux

```

Further Information: I have IFS Drives installed in WinXP. Its an opensource Win ext2/3 driver. With it, I can access the /home partition without errors and read data.
========

So my question is now, how to get the partition table running again? 

Is it a good idea to "remember" the entries in parted, completely erase the partition table and rebuild the needed partitions?

Every help apreciated... already missing my friendly Linux Desktop!

---

