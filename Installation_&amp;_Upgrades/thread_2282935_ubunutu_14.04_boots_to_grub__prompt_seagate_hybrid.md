---
title: "ubunutu 14.04 boots to grub  prompt seagate hybrid drive"
date: 2015-06-17
forum: Installation &amp; Upgrades
---

### Post by schnemart on 2015-06-17
Hello
I have a ubuntu 14.04 desktop which was   running for 6 months
with a boot drive being a seagate Hybrid drive .

I have tried using  using boot-repair booted from a USB but when I start the system just reboots

I have plug the drive  into another box and ran the seagate short test and it says all ok

please help

regards
Martin

---

### Post by schnemart on 2015-06-18
Just to clarify the system boots and goes straight to grub prompt

---

### Post by wildmanne39 on 2015-06-18
*Thread moved to **Installation & Upgrades**.* You will be more likely to get the help you need in the section of the forum!

---

### Post by yancek on 2015-06-18
> I have tried using  using boot-repair booted

Boot repiar has an option to Create BootInfo Summary.  Run that and post the output here as it will give a lot of details on your system.

---

### Post by schnemart on 2015-06-19
Hi Yancek
Thanks for your reply 
I got boot repair  report to work and it told me to post this [http://paste2.org/nHv3K0ew](http://paste2.org/nHv3K0ew)

 regards
Martin

---

### Post by oldfred on 2015-06-19
It is very strange that it shows gpt partition and all the partition table errors.
I have seen similar errors with MBR(msdos) where the logical partitions have a invalid link to next logical partition and create a infinite loop. 
I thought gpt was better as it does more internal checking and has a backup.

Post this, you may have to install gdisk.
       sudo apt-get install gdisk
sudo gdisk -l /dev/sda

And if fixable, posts from developer of gdisk:
[http://askubuntu.com/questions/460233/cant-restore-my-gpt-data-with-gdisk](http://askubuntu.com/questions/460233/cant-restore-my-gpt-data-with-gdisk)       
[http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802](http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802)

 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by schnemart on 2015-06-23
Hi Oldfred

I am in the process of backing up the disk with  GNUddrescue and this has taken longer than I liked 
I will get pack with the results of [COLOR=#000000]sudo gdisk -l /dev/sda
thanks for your help
regards
martin[/COLOR]

---

### Post by schnemart on 2015-06-25
Hello Oldfred
 I ran gdisk -l /dev/sdb (   i have pulled out the drive and attached it to my other box)

and this is the result 
GPT fdisk (gdisk) version 0.8.8


Caution: invalid main GPT header, but valid backup; regenerating main header
from backup!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************
Disk /dev/sdb: 7814037168 sectors, 3.6 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 52B26C6A-412A-4DAD-B51E-DC40772A93A7
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 7814037134
Partitions will be aligned on 2048-sector boundaries
Total free space is 3693 sectors (1.8 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1050623   512.0 MiB   EF00  
   2         1050624      7780700159   3.6 TiB     8300  
   3      7780700160      7814035455   15.9 GiB    8200  

your thoughts and thanks
Martin

---

### Post by schnemart on 2015-06-25
Hi  OldFred

Further to the above post

 after reading the posts that was included above above I 
I ran gdisk [COLOR=#000000] /dev/sdb v which was ok
I then ran gdisk /dev/sdb w which must of made the recovery of "[/COLOR][COLOR=#000000]Caution: invalid main GPT header, but valid backup; regenerating main header[/COLOR]
[COLOR=#000000]from backup!"[/COLOR]

[COLOR=#000000]Permanent 

Thus it worked  

Which is good
I wonder if anyone else has had trouble with Hybrid SDD / stand drives ?
any way thanks for your help
I am now making a backup of data and lets see how it goes
again thanks[/COLOR]

---

