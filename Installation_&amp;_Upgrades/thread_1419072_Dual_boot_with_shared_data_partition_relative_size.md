---
title: "Dual boot with shared data partition: relative sizes?"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by emagar on 2010-03-01
Hi, I've been trying to fully abandon Windows. But there are a few apps that have either imperfect or no substitutes in Karmic. I therefore plan to keep a dual boot in my new machine (64-bit Ubuntu 9.10 + Win7), with a shared partition for data, files, pics, etc. 

I've so far learned from this forum that NFTS is preferable to FAT32 for the shared partition. But I still wonder what sizes to allocate to each partition. I have a pretty large drive, and planned something along the following lines:

1 Swap: 8GB (double the RAM)
2 Linux: ext3 with 100GB (more stable than ext4)
3 SharedData: NFTS with ~440GB
4 Windows: NFTS with 100GB.
TOTAL: 640GB

Am I allocating too much to the Linux and Windows partitions? Any advice?
Thanks in advance. ;)

Edit 1: See summary of responses below.

---

### Post by manoriax on 2010-03-01
Well, there are some points that could be optimised here. E.g. your SWAP-partition. If you have 4GB of RAM installed, I really doubt that the Ubuntu system will ever use so much memory. I for example have 4GB of RAM, too, but I don't use a SWAP partition. This, however, depends on the applications you wish to run.

Furthermore you have to create more than just one Ubuntu partition (at least my advise would be to create more than one). One partition (mountpoint: /) for the operating system itself and a partition (mountpoint: /home) for all the application settings and so on. I think both can have about 50GB or something. And, personally, I prefer EXT4, but this is a most subjective choice.

---

### Post by darkod on 2010-03-01
If you plan to keep most of the large files on the shared partition, which would be logical because it would allow you to access them from both OSs, then yes, the partitions for windows and ubuntu are quite large.

If it helps, on a 250GB disk, I have win7 ultimate on 65GB partition and it's half used. But I don't play games and their install files can take significant space.

Also I have 15GB ubuntu root partition and separate 10GB /home partition.

Because my disk is smaller, all I could spare for the shared partition was 141GB.

For my needs, it works out fine.

---

### Post by emagar on 2010-03-01
> **manoriax said:**
> Furthermore you have to create more than just one Ubuntu partition (at least my advise would be to create more than one). One partition (mountpoint: /) for the operating system itself and a partition (mountpoint: /home) for all the application settings and so on. I think both can have about 50GB or something. And, personally, I prefer EXT4, but this is a most subjective choice.

Sounds like a good idea. If they take 50GB together, how much is advisable for / and how much for /home?

---

### Post by manoriax on 2010-03-01
> **emagar said:**
> Sounds like a good idea. If they take 50GB together, how much is advisable for / and how much for /home?
Since you want to store all the important data on the shared partition (music, videos, ...), I think 25-30GB are enough for the operating system. The remaining space can be used for the home partition.

---

### Post by emagar on 2010-03-01
Thanks for the info, this was useful!

---

### Post by emagar on 2010-03-01
Thanks for the useful replies. 

The allocation should therefore end up being as follows:

1 Swap: 2GB (since I have 4GB RAM)
2 Win7: NFTS with 65GB.
 3 SharedData: NFTS with ~520GB
4 Linux: ext3 or ext4 with 30GB to mount /
5 (logical) Linux: ext3 or ext4 with 20GB to mount /home
 TOTAL: 640GB

Hope this is useful to others. Cheers!

---

### Post by oldfred on 2010-03-01
I had root and swap with a small partition for sharing with windows for 3 years. With a new clean install of Karmic and a new 640GB drive I total reorganized. I moved /home to a 50GB partition and it uses 1GB since I also moved all Ubuntu data to a /data partition and link all the folders in. I directly mount my shared partition into home. I created 3 20GB (about 5GB used in each) partitions for root - current, previous and beta and mount data into each.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
oldfred's versions
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by emagar on 2012-08-05
Sorry to resuscitate an old thread, but technology has moved on, and some comparability should be useful. 

How have these issues evolved with new distributions of Ubuntu and larger disks? Do relative partition sizes remain the same for Precise? Do SSDs change anything?

---

### Post by oldfred on 2012-08-05
Better to start your own thread, with info on what you have or may think you want in the way of drives. Mix of SSD & hard drives make a lot of difference.

Oldfred is still posting his suggestions, almost daily. Many others have different or somewhat similar suggestions. 

I now use 25GB for / on my newer 60GB  SSD which has two / partitions. I still keep /home in / and have almost all data on my rotating drives. I now use gpt not MBR(msdos) for partitioning.

---

