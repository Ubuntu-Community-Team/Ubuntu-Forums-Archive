---
title: "Impossible to partition hd"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by puntino on 2010-08-12
Hello, 
I'm trying to install Ubuntu 10.04 on Dell inspiron 1370. 
The laptop comes with: 
a partition with Win7 about 60GB
a partition for data about 170GB
a hidden recovery partition for win7. 
More details in the picture "screenshot". 
Before installing Ubuntu, obviously, I have to create a new partition. At this aim, I used the built in disk manager utility of win7.   

1) I shrunk the partition D from which I removed up 30Gb as a new partition on which install Ubuntu
2) I started the Ubuntu installation, but the new partition is unusable 

Then I merged the new partition to the D partition and I tried to re-partition the latter with Gparted. Unfortunately the partition D is "unallocated" and it is not possible to create a new partition because there are already four primary partitions.
Take a look at screenshot-1
If I execute the command dfisk -l from Ubuntu live, I get the following output: 
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x955711c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2               1          13      102400   de  Dell Utility
Partition 2 does not end on cylinder boundary.
/dev/sda3              13        1288    10240000   27  Unknown
/dev/sda4   *        1288        8937    61440000   42  SFS

Disk /dev/sdc: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc

``` 

In order to sort out this problem, without re-installing win7, I've thought to delete the hidden partition, thus the number of primary partitions becomes 3 and I can install ubuntu. 
What do you suggest? 
Thank you in advance for any help.

---

### Post by lechien73 on 2010-08-12
You might want to keep the recovery partitions - particularly if you don't have the Windows 7 media. I would suggest:

1. Back up the data partition
2. Delete the data partition
3. Create an extended partition the full size of the unallocated space
4. Create a logical partition for the data
5. Restore the data partition
6. Install Ubuntu to the extended partition

---

### Post by puntino on 2010-08-12
I attach the disk manager screen-shot, also. (and the other that I mentioned in the previous post, but I missed)

---

### Post by puntino on 2010-08-12
How can I create an extended partition?

---

### Post by lechien73 on 2010-08-12
You can have a maximum of 4 x primary partitions using the msdos partition table. One of these partitions can be an extended partition, which contains more logical partitions.

To create an extended partition in GParted, highlight the unallocated space, Go to Partition > New. Follow the prompts and, when you can, click the **Create as** arrow button, and select **Extended** from the list.

You can then create a replacement data partition as a logical partition. Leave the rest of the space unallocated, and the Ubuntu installer will sort it out.

---

### Post by puntino on 2010-08-13
First of all, thank you lechien for your interest. 
You said that I can create an extended partition and suggested to > 
GParted, highlight the unallocated space, Go to Partition > New
 
Unfortunately, I cannot do that. (I have a grey menu, no choice is available). I think it is normal because the "unallocated space" is not a partition and there are already 4 primary partitions, we should chose one among them. Before doing any disaster I'm trying to figure out what each partition mean. 
Let's tack together the pieces. Ubuntu automatically mounted the partition sda1 and sda2 as depicted in "screenshot2".
I also mounted the partition sda3, but I failed to mount the partition sda4. For the latter I tried the command 
```

mount -t ntfs /dev/sda4 /media/sda4

```
that prompts the error message "Failed to access volume /dev/sda4: No such file or directory". Indeed /dev/sda4 is not listed in /dev (I checked it out with the ls command). 

Looking in each single partition successfully mounted with the command ls: 

```

sda1 ->/media/OS

Boot
bootmgr
BOOTSECT.BAK
Dell
dell.sdr
Documents and Settings
hiberfil.sys
inetpub
MSOCache
pagefile.sys
ProgramData
Program Files
Program Files (x86)
Programmi
Recovery
$Recycle.Bin
System Volume Information
texlive
Users
Windows
WinPEpge.sys


```


```

sda2-> media/3AD0....

Music
My Documents
Pictures
$RECYCLE.BIN
System Volume Information

```

```

sda3->/media/sda3

Boot
bootmgr
dell
Recovery
$RECYCLE.BIN
ResSys.ini
System Volume Information

```

Taking account what you said previously, we can say only that: 
sda3 is the Dell "hidden" partition for system recovery.

sda1 seems Win7 root directory, it should be sda4 (that I didn't manage to mount). 

sda2 is my "data" partition what I expected to be on the "unallocated space" (see screenshot2).

It seems something went wrong. Have you any idea?
I'll carry on searching other info on the net, hopefully to get rid of this problem :(
Thank you

---

### Post by lechien73 on 2010-08-13
Sorry - I didn't make myself clear.

I meant that you would only be able to highlight the unallocated space and create an extended partition *after* backing up and deleting your data primary partition.

---

### Post by puntino on 2010-08-13
Don't worry lechien :)

So you suggest to delete partition sda2 (media/3....) and add it to the unallocated space that will become a new primary partition.

---

### Post by puntino on 2010-08-13
Dear Lechien,
I investigated on my problem and my final conclusion is: 
Win7 does need an its own partition for recovery (it is sized 100MB). I do not know what the partition dev/sda1 is for, loader? 
The other two partitions are quite self explicative. 
In the end, if i want to have win7 and Ubuntu, I have to format the hd, create three primary partitions: 
1 for win 
1 for Ubuntu 
1 for dell recovery 

and one extended partition for data.

---

### Post by wilee-nilee on 2010-08-13
sda1 is dell firmware. I don't think you can create a recovery partition so you just want to keep the sda1 dell and the main W7 partition with everything from the data moved to it and the recovery, then let Ubuntu build in the unallocated space.

Here is a picture of my install with gparted, mine was a fresh install from XP so the 100mb boot is inside of sda1. I also have Lucid and maverick in the extended.
[ATTACH]166355[/ATTACH]

To be honest I would contact dell and see what the cost is for a full install recovery disc with the key or a OEM set. You may be able to reinstall without the Dell firmware or recovery and have more space on the HD.

With your computer setup the way it is you can't really do much with adding Ubuntu in a extended, if you want to keep the recovery. The recovery would be pretty much unusable after installing Ubuntu. Although on my acer netbook the recovery was in my Ubuntu grub boot and was usable originally but this is unusual.

---

