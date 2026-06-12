---
title: "SSD for caching and alignment on 4KB pages per cylinder"
date: 2013-12-04
forum: Installation &amp; Upgrades
---

### Post by dannyboy79 on 2013-12-04
I have an OCZ Synapse 64GB Caching drive and I want to use it to cache my /home/ partition which has my browsing profiles and steam games installed on it. My thought is that it will improve performance of web browsing and or gaming. (i guess the question is should I instead have it be a cache drive for my / partition?) The drive is only going to contain 1 partition formatted as ext4. I still am uncertain whether I am going to go with bcache, dmcache, flashcache or what BUT I do know that in the beginning SSD's needed certain alignments done to them when making partitions so that they were optimized for usage (not putting unneccesarry strain on it when reading and writing due to unaligned partitions). Is this still true? Reading this webpage [http://www.linux-mag.com/id/8397/](http://www.linux-mag.com/id/8397/) it talks about using fdisk to run the following command ```
fdisk -H 224 -S 56 /dev/sdd
``` or ```
fdisk -H 32 -S 32 /dev/sdd
```
Currently my SSD drive is formatted using Gparted standard method and when I issue fdisk -l on it, it shows the following
```
Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```
and according to that webpage I linked to this is not optimized. Should I be running one of those fdisk commands on my disk so it has different head size, sectors/tracks, cylinders, and total sectors? ANy help would be appreciated.

---

### Post by oldfred on 2013-12-04
I use gpt partitioning for all new drives, so fdisk does not work.

 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

### Post by dannyboy79 on 2013-12-05
thanks for replying but I have already read confusing articles about the issue. I am just wondering if my currently partitioned ssd drive is ok the way it is OR if I should change it. Here's the output of the command you listed
```
Model: ATA OCZ-CACHE-SYNAPS (scsi)
Disk /dev/sdb: 62533296s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End        Size       Type     File system  Flags
 1      2048s  62531583s  62529536s  primary  ext4

```

---

### Post by oldfred on 2013-12-05
That is just one large partition on a MBR(msdos) partitioned drive. Starting at sector 2048 provides alignment.

My logic is to have / (root) and /home but not any data on my SSD. That was it is not cached, but actually just using SSD. And data that I link from my /mnt/data partition on my hard drive is not accesses as much. Not sure about your games, I understand they are larger and do not know if caching may then work better for them. Or if you can link them from a data partition.

I created two 28GB / partitions on my SSD, one for current install and one for next or test install. My working install uses 10GB of the 28GB and at least 2GB of the 10 is /home with .wine for the Windows version of Picasa.

---

### Post by dannyboy79 on 2013-12-05
my question is whether or not currently my SSD is partitioned (alignment and sector size) to the optimal settings. The drive is only 32GB and I am going to use it for caching only, not to directly install my home or / on it, only to cache 1 or the other using bcache.

---

### Post by oldfred on 2013-12-05
Starting at sector 2048 provides alignment.

But I do not know how you implement trim with bcache.

---

### Post by dannyboy79 on 2013-12-08
perfect. I got flashcache all setup (abandoned bcache because 3.10 kernel wasn't playing nice in xubuntu 12.04.3, not to mention bcache wasn't available in a precise ppa) and i am loving the speed increase! Used to get roughly 70 MB/s write speed and now I get approx 430 MB/s. thats what dd command returned anyway

---

### Post by sammiev on 2013-12-08
> **dannyboy79 said:**
> perfect. I got flashcache all setup (abandoned bcache because 3.10 kernel wasn't playing nice in xubuntu 12.04.3, not to mention bcache wasn't available in a precise ppa) and i am loving the speed increase! Used to get roughly 70 MB/s write speed and now I get approx 430 MB/s. thats what dd command returned anyway

I need to follow this. Thanks

---

