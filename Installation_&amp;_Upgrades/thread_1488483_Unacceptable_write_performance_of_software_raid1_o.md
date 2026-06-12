---
title: "Unacceptable write performance of software raid1 on ubuntu lucid server"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by farleylai on 2010-05-20
Compared to my laptop notebook with a HD of 5400rpm, the write performance of raid1 on an ubuntu lucid server is unacceptable.

In the begining, I installed ubuntu 9.04 server(alternate) using raid1 with two WD 1TB HDs of 7200rpm(Green Power) and then performed dist upgrade to 9.10 and then to 10.04.

I guess the write performance initially was reasonable since the installation and data migration(copy from another computer over LAN) didn't take too much time. However, after upgrading the server to 9.10 or so, I found large file upload through samba or ftp tends to block and time out. It is of no use whether to change the daemon or the client program so that I tried to test the read/write performance on the server to figure out the situation.

To my surprise, using strace I found even a simple program like cp would easily get blocked eventually in a write() system call for decades of seconds. Hence, I perform another disk writing test using dd for data size ranging from 50MB to 1GB. Performance test commands are listed as follows:

> dd if=/dev/zero of=test.img count=[5|10|15|20|100] bs=10M

if the data to write is equal or fewer than 150MB, the command returns immediately at very hight speed but the raid disks starts to sync and busy so that the terminal prompt seems to freeze. I think this behavior is normal under the raid1 configuration, isn't it?

But when the data size is equal to 200MB, the test command blocks for seconds and the write speed is measured at about 16.6MB/s. Of course, the raid disk still starts to sync and busy afterwards. Next, I test writing with data of size 1GB. The command blocks so long for about 770 seconds(<2MB/s) while the same test runs for only 17.49 seconds(60MB/s) on my laptop.

I also burn a Lucid LiveCD to boot the server and mount the raid device to run the test again but the results remain similar. Does that means even I re-install the system on the raid, the problem never disappears?

Any ideas or possible solutions? 

PS: the disks run under the mode of UDMA6 without change.

---

### Post by lemming465 on 2010-05-21
If the disks are 1 TB I assume they are still using 512 byte sectors, not the newfangled 4k sectors?  With the big sectors filesystem alignment matters a lot.
What filesystem did you format the devices with?  Are you using LVM?  If so, what's the stripe size?  Are just writes slow, or do reads suffer too?  Does smartctl say anything alarming about the health of the disks?

You are quite right that the performance is much lower than it should be, but we don't have enough information to diagnose it yet.

---

### Post by farleylai on 2010-06-01
After some more experiments, the cause seems more clear.

First, I removed the RAID and cleared the partition table.
Next, I ran Disk Utility to benchmark read/write speed on both drives with ubuntu LiveCD and HD Tune Pro on another Windows XP machine. The results follow:

&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;Ubuntu 10.04&#12288;&#12288;&#12288;Windows XP
min.&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;2.3MB/s&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;40.7MB/s
max.&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;19.0MB/s&#12288;&#12288;&#12288;&#12288;&#12288;88.3MB/s
avg.&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;5.3MB/s&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;70.1MB/s

Reading speed is a little slow for about 40-50MB/s on ubuntu and 75-85MB/s on Windows XP, but still far faster than writing speed.

As a result, it's a no-brainer neither the HD nor the RAID is the problem while the disk sector size matters little. So I started to doubt the SATA cables and the mother board connectors. Then I took the disks out of the case and connected only one disk with the SATA cable at a perfect angle(almost no twisting) to run the benchmark again.

This time, the performance was similar to the results on the Windows XP machine so that I guessed the cables matter a lot. But whenever I connect both disks, the performance always goes down to 30-40MB/s each for writing and 55-75MB/s for reading even after I've replaced the cables with high quality ones made by COMAX and Amphenol.
 
I also ran the benchmarks with ubuntu 9.04 and fedora 13 and the results looked similar. I am at the end of my rope with Intel 865G and ICH5 so that I decide to to detach one of the disk after the RAID is built up to maintain the system performance.:(

---

