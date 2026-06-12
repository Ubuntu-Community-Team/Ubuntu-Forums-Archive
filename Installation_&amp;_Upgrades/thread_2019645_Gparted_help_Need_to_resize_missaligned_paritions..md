---
title: "Gparted help? Need to resize missaligned paritions."
date: 2012-07-07
forum: Installation &amp; Upgrades
---

### Post by javajames79 on 2012-07-07
Basically when i enter disk utility it shows that the partition is missaligned (there are three partitions all missaligned by different amounts), from what i've read the partitions can be realigned using Gparted tool or fdisk from a live CD, and that this can be done without destroying anything (with the minor inconvienience of having to reinstall grub).

Basically i need someone to help talk me through doing this? I will login from the live CD to give details from FDISK.

If you know anything about resizing partitions it would be appreciated!

Thanks in advanced.

---

### Post by javajames79 on 2012-07-07
```
Command (m for help): p

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Command (m for help): 

```

This is the partition table for the HDD i have ubuntu on.

---

### Post by darkod on 2012-07-07
You have a GPT partition table on that disk. Don't use fdisk to manipulate partitions, it doesn't work with gpt.

To get a better idea of your partitions, you can print the list with parted, and use MiB as unit (real MegaByte).

```
sudo parted /dev/sdb unit MiB print
```

Do you need to align them for something, or only because you saw the message saying they are not aligned?

I am asking this because any moving of partition does carry risk for the data. In theory, Gparted should be able to move the partition (in other words align it to the closest 1MiB), but if thing go wrong that can also destroy the data on that partition.

If this is not urgent, I would leave it as it is. Then, in some future reinstall, you can delete all partitions and create them this time aligned. parted is a very good tool for that since you can create partitions by specifying the start/end values.

If there is no OS on this disk, you can also consider moving the data temporarily, deleting the partitions and recreating them, then putting the data back. If you think it's worth it.

---

### Post by irv on 2012-07-07
I found this on askubuntu.com. I have never had to re-align partitions before so I hope this will help. It looks like there were some links in the help portion of the answer post.
[http://askubuntu.com/questions/73438/how-to-partition-a-advanced-disk-hdd-properly-using-gparted-or-similar]("http://askubuntu.com/questions/73438/how-to-partition-a-advanced-disk-hdd-properly-using-gparted-or-similar")

---

### Post by javajames79 on 2012-07-07
[http://askubuntu.com/questions/103855/partition-is-misaligned-by-3072-bytes-pavilion-dv7-6199us](http://askubuntu.com/questions/103855/partition-is-misaligned-by-3072-bytes-pavilion-dv7-6199us)

I would quite like to have it alligned because speed is very important too me and i have noticed how much slower my PC boots up since last time i used ubuntu.

You were right that fdisk didn't work, i tried moving it to the nearest sector at 4096, but then disk util didn't work, thankfully moving it back undid that.

---

### Post by javajames79 on 2012-07-07
Well the confusing thing is all the partitions on that drive have the same issue, but with different values of missalignment

Even swap. And the partition before it is called EFI system partition.

Not sure if that means if i touch that im screwed? (im a noob with partitioning)

---

### Post by oldfred on 2012-07-07
If you use a newer version of gparted to partition it should automatically be correct. The real issues is 8 sectors.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

### Post by javajames79 on 2012-07-07
The exact info (from diskutil):

100MB FAT - EFI System partition - missaligned 3072 bytes
983gb ext4 - linux basic data partion - misaligned 2560 bytes
17gb swap - swap space - missaligned 1536 bytes

---

### Post by javajames79 on 2012-07-07
More data:

```
ubuntu@ubuntu:~$ sudo parted /dev/sdb unit s print
Model: ATA ST1000DM003-9YN1 (scsi)
Disk /dev/sdb: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start        End          Size         File system     Name  Flags
 1      34s          195346s      195313s      fat32                 boot
 2      195347s      1920017612s  1919822266s  ext4
 3      1920017613s  1953525118s  33507506s    linux-swap(v1)

ubuntu@ubuntu:~$ sudo parted /dev/sdb unit MiB print
Model: ATA ST1000DM003-9YN1 (scsi)
Disk /dev/sdb: 953870MiB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start      End        Size       File system     Name  Flags
 1      0.02MiB    95.4MiB    95.4MiB    fat32                 boot
 2      95.4MiB    937509MiB  937413MiB  ext4
 3      937509MiB  953870MiB  16361MiB   linux-swap(v1)

ubuntu@ubuntu:~$ 
```Ah i see, 95.4 mib, thats the missalignment?

Oh i see, so the first partition is the boot partition, with grub, so i can reinstall that later, how do i change the start and end of each partition to get a fixed table?

---

### Post by javajames79 on 2012-07-07
Can i just resize it with the resize tool in gparted

Will parted write the changes before i exit? Can i change the table and check the alignment?

---

### Post by irv on 2012-07-07
> **javajames79 said:**
> Can i just resize it with the resize tool in gparted

Will parted write the changes before i exit? Can i change the table and check the alignment?

I have deleted partitions, re-sized others with gparted, and it is a slow go. It needs to move data around and it takes a long time. I just set it in motion and let it go. After awhile I thought it would have been easier to just format and reload everything. And by the way, I had 4 OS's on the drive.

---

### Post by javajames79 on 2012-07-07
Hmm 1TB hdd, with 30gb used, just ubuntu on there. 

Well however long it takes, i can leave it running overnight. Can i please have some information on HOW to move these partitions?

---

### Post by javajames79 on 2012-07-07
Ok i'm thoroughly confused:

I have two drives of the exact same make, one is a slightly modern version, which is the one i'm running linux on. Can anyone tell me if i should basically not care at all about the misalignment?

sda is my old mac HDD
sdb is my new linux HDD

```
james@hyperarray:~$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   32076 MB in  2.00 seconds = 16056.86 MB/sec
 Timing buffered disk reads: 450 MB in  3.00 seconds = 149.85 MB/sec
james@hyperarray:~$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   30460 MB in  2.00 seconds = 15246.93 MB/sec
 Timing buffered disk reads: 524 MB in  3.00 seconds = 174.55 MB/sec
james@hyperarray:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   32178 MB in  2.00 seconds = 16108.08 MB/sec
 Timing buffered disk reads: 348 MB in  3.01 seconds = 115.68 MB/sec
james@hyperarray:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   32196 MB in  2.00 seconds = 16117.38 MB/sec
 Timing buffered disk reads: 348 MB in  3.02 seconds = 115.39 MB/sec
james@hyperarray:~$ 

```

---

### Post by oldfred on 2012-07-07
If it is not a new 4k drive nor an SSD, I do not think it makes much difference.

You must have used an older gparted as first partition starts at 34. I had that also with the old versions of gparted, but all the new ones start at 2048. 

I am not sure you can adjust with gparted by a few sectors? You want either first sector to be 40 so it can be divided by 8 or 2048 which seems to be the new default.  Have not tried using gparted to move just a few sectors. If you have a new install or just a little data, it just may be easier to start over.

---

### Post by javajames79 on 2012-07-08
I'm not quite following how i could've used an older version of gparted to install it. I stil have the pendrive from the install and when i try sudo apt-get install gparted, it doesn't come up with any updates. In other words im running gparted 0.11.0. I installed it a week ago (though i have done a LOT of work since then.) I installed with the erase driver completely option from the automatic installer. 

Starting again is NOT an option. I have spent too long working on this too long.

I'm still very confused by this all; using what exactly do i move what? Could i see any example commands?

---

### Post by javajames79 on 2012-07-08
Ok so heres my partition table

```
james@hyperarray:~$ sudo parted /dev/sdb unit MiB print
Model: ATA ST1000DM003-9YN1 (scsi)
Disk /dev/sdb: 953870MiB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start      End        Size       File system     Name  Flags
 1      0.02MiB    95.4MiB    95.4MiB    fat32                 boot
 2      95.4MiB    937509MiB  937413MiB  ext4
 3      937509MiB  953870MiB  16361MiB   linux-swap(v1)
```

Now i want to resize it so that (don't mind reinstalling grub) the linux partition remains intact and i have got rid of this error.

Put quite simply im very confused because: MiB = 1000bytes doesn't it? Because in which case how am i supposed  to allign my drive O.o.

Can someone please explain this to me? If anyone knows exactly what sizes i want that'd be great!

---

### Post by darkod on 2012-07-08
No, 1MiB is the correct in computer binary terminology. In other words:
1 MiB = 1024 x 1024 bytes
1 MB = 1000 x 1000 bytes

Since computers work in binary, you need to align in MiB, the binary. I believe it considers them aligned when every partition begins and ends on a value divisible with 1 MiB. Or just that the first partition starts on 1 MiB, not sure about that.

Also, I am not sure Gparted is the best tool for this, since Gparted works in MB so it might not align properly because of the MB / MiB difference.

Parted can work with all of these units (as you noticed in the example) but I have never tried moving / resizing partitions with it. Also, when resizing with some tools you need to make sure you resize the filesystem first if the tool doesn't do that automatically, since if the partition size is made smaller than the filesystem size, it can affect the data.

As for the starting over again, it doesn't need to be from scratch. There is the option to copy all files from all partitions (less swap of course, no need to copy anything from swap), delete partitions, create them with parted where you can control exactly the start/end in MiB, and put the data back.

You would only need to replace the UUID of the partitions in /etc/fstab with the new ones, and reinstall grub2 so that it connects to the new root partition. As far as I am aware, that's all.

Trying to move the partitions might be a lot riskier process. I personally have never tried it, and can't advise you on the exact commands. Anyone else is free to jump in if they have more experience with that.

---

### Post by oldfred on 2012-07-08
I have not done it either.

In gparted and you click on a partition, it has resize/move. One of the options is align to MiB which is the default and what you want. If you just do that will it resize by a small amount to align or will have actually have to move it to get it to then round to aligned sectors?

---

### Post by javajames79 on 2012-07-08
But the thing which is causing my brain to segfault is that it gives values of whole numbers of MiB, suggesting it can't really tell at all and making me wonder whether thats why i got this in the first place.

---

### Post by goltoof on 2012-07-12
Can someone just provide the simple command i need to put into parted to make the alignment happen?

I simply need to turn logical/physical from 512/4096 to 4096/4096.

2 pages into google now.... Nada.

---

### Post by oldfred on 2012-07-12
I think the links in post #7 cover it. I do not think you want it to be 4096/4096, but just on a 8 sector boundry. Most common is first at 2048, but 40 also works.

---

