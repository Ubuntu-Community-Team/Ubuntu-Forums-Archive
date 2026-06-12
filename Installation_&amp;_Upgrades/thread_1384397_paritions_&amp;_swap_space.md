---
title: "paritions &amp; swap space"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by Xog on 2010-01-18
So I installed ubuntu on my main PC. I had primary partitions already. So I deleted one that I never used and installed ubuntu. However, I didn't select a swap space. Is it possible for me to do this once I'm inside ubuntu or do I have to reinstall it again? 

I was under the impression you couldn't have any more than three partitions so I didn't want to screw anything up by making a swap space. Please tell me I'm wrong and that I can only have three PRIMARY partitions, and a swap space is perfectly fine with the 3 primaries. thanks :D

---

### Post by kansasnoob on 2010-01-18
If you already had a SWAP for another Linux OS that should be fine. You can share the same SWAP between different Linux OS's:

```
lance@lance-desktop:~$ sudo parted /dev/sda print
[sudo] password for lance: 
Model: ATA WDC WD1600AAJB-0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  22.0GB  22.0GB  primary   ntfs            boot
 3      22.0GB  31.0GB  8933MB  primary   ext3
 2      31.0GB  160GB   129GB   extended
 5      31.0GB  39.5GB  8521MB  logical   ext3
 6      39.5GB  66.8GB  27.3GB  logical   ext3
 7      76.4GB  84.7GB  8365MB  logical   ext3
 8      84.7GB  100GB   15.7GB  logical   ext3
13      100GB   107GB   6835MB  logical   ext3
14      107GB   122GB   15.1GB  logical   ext3
 9      122GB   124GB   1258MB  logical   linux-swap(v1)
10      124GB   141GB   17.0GB  logical   ext3
11      141GB   147GB   6309MB  logical   ext3
12      147GB   160GB   13.1GB  logical   ext3

```

Five Linux OS's on mine with one SWAP :D

Oh, and notice how I used an extended partition to allow many logical partitions.

---

### Post by raymondh on 2010-01-18
> **Xog said:**
> So I installed ubuntu on my main PC. I had primary partitions already. So I deleted one that I never used and installed ubuntu. However, I didn't select a swap space. Is it possible for me to do this once I'm inside ubuntu or do I have to reinstall it again? 

I was under the impression you couldn't have any more than three partitions so I didn't want to screw anything up by making a swap space. Please tell me I'm wrong and that I can only have three PRIMARY partitions, and a swap space is perfectly fine with the 3 primaries. thanks :D

4 primary partitions or .... 3 primary + 1 extended (of which it can house as much 'logical' partitions your system can take).

As for your swap, see the swapFAQ.  You can create a swap FILE or, you can also create a SWAP partition but using the liveCD and then mounting it.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Back-up your files before any partitioning work.

Regards,

Raymond

ADDED : a copy of my parted /dev/sda to show the 3 primary + 1 extended (which houses 3 logicals)

Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  41.1MB  41.1MB  primary   fat16             
 2      41.9MB  10.5GB  10.5GB  primary   ntfs              
 3      10.5GB  135GB   124GB   primary   ntfs         boot 
 4      135GB   160GB   25.3GB  extended               lba  
 6      135GB   156GB   21.6GB  logical   ext3              
 7      156GB   157GB   979MB   logical   linux-swap        
 5      157GB   160GB   2682MB  logical   fat32

---

### Post by Xog on 2010-01-18
Thank you Raymond H. I'll do that when I get home from work today. I hope I don't spend another 16 hours straight trying to fix 1 problem in ubuntu like yesterday.

---

### Post by audiomick on 2010-01-18
As far as I know, if your want hibernate to work, you have to have a swap partition. If won't work with a swap file.
The partition has to be a fraction bigger than your RAM, as hibernate writes the RAM contents to the swap space.

---

### Post by Xog on 2010-01-18
Thanks Mike, I'll keep that in mind.

---

