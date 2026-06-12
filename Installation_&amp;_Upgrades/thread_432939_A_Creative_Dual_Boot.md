---
title: "A Creative Dual Boot"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by tux-curious on 2007-05-04
Ok, so I've been using Ubuntu (no dual-boot) on my home PC for the last year or so, and I'm looking into getting a laptop for University. 

So here's the thing, if I'm buying a laptop, I'm going to have to buy Vista anyways so I'm going to try to dual boot, but I want to minimize the impact of my Vista partition. Here's my plan for partitioning:

[LIST]
[*]5 gig for Vista system files [NTFS)
[*]10 gig for Ubuntu system files and programs [ext3]
[*]
[*]The rest some sort of crazy "home" folder/"My Documents [fat32]
[/LIST]

So basically what I'm asking is, is there anything standing in my way from using the same partition for my Home folder on both OS's so I can keep all my documents, music, and pictures together.

*Note: I realize that I would probably have to manually hide all the hidden linux files on Windows.*

---

### Post by finalzero on 2007-05-04
Nope but you will need to check if Feisty Fawn can read and write to NTFS partitions. 

The way I have got it is as follows:

12GB Windows XP Partition
20GB, 25GB, 20GB partitions in a windows as logical drives (only available to Windows XP)
25GB Ubuntu Partition (1.5GB Swap)

20GB FAT32 Partition - my share point

The 20GB FAT32 partition is used by both Windows XP and Linux, it allows me to share my files with both systems and I have found no issues with reading and writing to the FAT32 partition with Ubuntu 7.04.

Hope that helps,

Fz

---

### Post by confused57 on 2007-05-04
> **tux-curious said:**
> Ok, so I've been using Ubuntu (no dual-boot) on my home PC for the last year or so, and I'm looking into getting a laptop for University. 

So here's the thing, if I'm buying a laptop, I'm going to have to buy Vista anyways so I'm going to try to dual boot, but I want to minimize the impact of my Vista partition. Here's my plan for partitioning:

[LIST]
[*]5 gig for Vista system files [NTFS)
[*]10 gig for Ubuntu system files and programs [ext3]
[*]
[*]The rest some sort of crazy "home" folder/"My Documents [fat32]
[/LIST]

So basically what I'm asking is, is there anything standing in my way from using the same partition for my Home folder on both OS's so I can keep all my documents, music, and pictures together.

*Note: I realize that I would probably have to manually hide all the hidden linux files on Windows.*

Make sure to use the Vista partitioner to resize your Vista partition(don't use gparted to shrink your Vista).
Yes, a separate FAT32 partition would allow you to share data between Linux & Windows.

---

### Post by rillip on 2007-05-04
NTFS can be read by Linux now, and ext3 can be red by Windows, if you do it right.  Don't have any resources lying around on that right off hand, but it is no longer neccessary to use Fat 32.

Having said that, I'm using Fat 32. [:P]  I was lazy and didn't feel like setting it up

---

### Post by JLAudioFan on 2007-05-05
I think you probably need more than 5 gigs for windows vista to install.  My toshiba wouldn't even upgrade to vista unless i had 15 gigs free...

Here's what microsoft says:

[http://www.microsoft.com/windows/products/windowsvista/editions/systemrequirements.mspx?wt_svl=10042VHa1&mg_id=10042VHb1](http://www.microsoft.com/windows/products/windowsvista/editions/systemrequirements.mspx?wt_svl=10042VHa1&mg_id=10042VHb1)

for vista home basic:

# 1 GHz 32-bit (x86) or 64-bit (x64) processor
# 512 MB of system memory
# 20 GB hard drive with at least 15 GB of available space

---

