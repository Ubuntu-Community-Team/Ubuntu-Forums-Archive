---
title: "LiveCD cannot recognize my windows partition"
date: 2012-09-08
forum: Installation &amp; Upgrades
---

### Post by dubcee on 2012-09-08
So I know other threads with this title exist, but they have not helped me so far!

I want to install ubuntu to dual boot with windows7. windows is already installed, and i have 100GB of unallocated space on my hard drive. when booting into the ubuntu livecd, it does not think that any operating systems are currently on my hard drive. 

i ran boot-repair and here is the pastebin: [http://paste.ubuntu.com/1193599/](http://paste.ubuntu.com/1193599/)

i also did the following:
sudo dmraid -rE

Here is my output from fdisk -l
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x93f00317

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   767053823   383423488    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 16.2 GB, 16225665024 bytes
255 heads, 63 sectors/track, 1972 cylinders, total 31690752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    31690751    15844352    c  W95 FAT32 (LBA
```)

and here is my output from os-prober

```
/dev/sda1:Windows 7 (loader):Windows:chain
```

any help would be much appreciated! Thanks!

---

### Post by TheFu on 2012-09-08
And if you create a primary or partition, but do not format it, the Ubuntu installer doesn't see that?

I know that Linux "wants" at least 2 partitions.
* OS/Apps/HOME
* swap partition

Three partitions are more flexible.  Usually the most flexible way to achieve the partition goals is to make as much space as possible contained within an extended partition, inside which all logical partitions fit.

I understand that there is some issue, but you didn't say what that issue was or how you got there.  Or did I miss something?

During the install, there's a "do something else" option for partitioning. Use that.  NTFS or vFAT or exfat partitions are not useful for a normal Linux install.  Ideally, you want three partitions types:
* 82 : Linux swap / Solaris (1G or 2G)
* 83 :  Linux (20G)  for "/"
* 83  : Linux (everything else) for "/home"

---

### Post by dubcee on 2012-09-09
Hey TheFu.

So what's happening is, I have a blank hard drive. I then install windows 7 onto it. From windows, I shrink the partition, splitting into 3 total: System, Windows, and Unallocated (100GB). The first two are of course from the windows installation, and this unallocated section is where I now want to install ubuntu.

[IMG]http://i.imgur.com/ZpTYY.jpg[/IMG]

When i boot into the livecd, it does not detect the OS. From installation, when it asks where I want to install, I am provided with two options: Erase Disk and use it all for Ubuntu, or "Try something else." So I choose "Try something else to choose my specific partition, and it just shows 500GB of unallocated space. This is clearly not true!!

Does this provide you with enough details about my problem? Let me know if there is any more information I can provide.

Thanks!

---

### Post by TheFu on 2012-09-09
Did you use MBR or GPT for the partitioning?  I see from that pastebin that you used GPT.

Which exact version of Ubuntu are you trying to install?  Not all partitioning tools and Linux tools support GPT. This should explain why I'm asking [http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)

---

### Post by dubcee on 2012-09-09
I'm trying to install 12.04, and yes it appears that I used gpt

---

### Post by darkod on 2012-09-09
No, the disk is not gpt. The fdisk results would be different. What happened is that it was gpt and then you changed it to msdos table using windows, and windows doesn't delete the backup gpt table as it should, so linux tools detect it and are confused if the disk is gpt or not.

Use fixparts from live mode and it will sort it out. You only need to open the disk with fixparts, it will offer to remove the backup gpt table. After that you can install uubntu without problems.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by dubcee on 2012-09-09
THANK YOU!

darkod your solutions solved my problem. for anyone else who happens to have this problem, i just did the following:

boot into ubuntu livecd
download fixparts from [http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.4/fixparts-binaries/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.4/fixparts-binaries/)
ran fixparts from terminal
typed in my disk /dev/sda
press Y to delete table
press w to write
and ta da! solved

---

### Post by YannBuntu on 2012-09-11
Good job :)

For information, here was the initial output of "sudo parted -l":

```
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
(snip)
```

(I extract it from the Boot-Info, so that it appears in the forum search results)

---

