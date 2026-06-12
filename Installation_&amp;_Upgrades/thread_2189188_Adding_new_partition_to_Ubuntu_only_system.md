---
title: "Adding new partition to Ubuntu only system"
date: 2013-11-21
forum: Installation &amp; Upgrades
---

### Post by douglas.e.ryan on 2013-11-21
I had the same question, but I think it's answered. I let Ubuntu erase the entire disk, but wasn't happy that it only created a root and swap parition. It seems prudent to at least have a data parition and keep the OS seperate.

```
sudo fdisk -l

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009fd2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1947758591   973878272   83  Linux
/dev/sdb2      1947760638  1953523711     2881537    5  Extended
/dev/sdb5      1947760640  1953523711     2881536   82  Linux swap / Solaris
```

and parted output is:

```
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  997GB   997GB   primary   ext4
 2      997GB   1000GB  2951MB  extended
 5      997GB   1000GB  2951MB  logical   linux-swap(v1)
```

Just boot from the DVD, run gparted and shrink sdb1, make and format a new parition?

---

### Post by coffeecat on 2013-11-21
@douglas.e.ryan, I've moved your post into its own thread. Your partition layout is different from the one described in the thread you posted to and giving advice about different layouts will confuse things.

---

### Post by oldfred on 2013-11-21
I prefer separate /home and/or separate data partitions. 
Some advantages to each depending on what you want to do and there is no one right way.

But I believe the advantage of a smaller separate / (root) partition keeps all system files closer together on hard drive and reduces drive from having to read all over the place. The standard of / & swap was started back when driver were a lot smaller and it made sense to keep as one partition as available unused space could be shared and you did not have to allocate in advance.

I prefer separate /mnt/data partition, but that is because I have multiple 25GB / (root) partitions for different installs to test or just try out changes that I may not want in my working system. Then I can mount all data in all installs and still have separate /home with different settings. I usually keep /home inside / since all data is in data partition.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

   Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another thing I often suggest if drive will only be Ubuntu is to use gpt partitioning, not the 30+ year old MBR partitioning with 4 primary partition limit. And if drive may be moved to a newer system with UEFI include an efi partition at beginning of drive. Not much space not used and then easier to convert to UEFI if needed as it may be very difficult to add an efi partition at beginning of drive if drive is full of data.
       GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

