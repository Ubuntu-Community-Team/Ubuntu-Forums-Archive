---
title: "My /home is unlocated after Boot repair"
date: 2012-08-06
forum: Installation &amp; Upgrades
---

### Post by dennym on 2012-08-06
Ok here the thing...

I wanted a Windows7 install beside my existing Ubuntu 12.04LTS.
So i googled some and used many wikis to figure it out.

I made some free space for my windows installation on my hdd. After this was done i installed Windows on this freespace. 
After the installation was done I booted my Boot repair USB live dongle to fix the grub.
Everything runs fine. 
Both systems are in grub, windows runs and ubuntu starts... till it cant find my /home partition.

I rebooted and started repair boot usb dongle to check the partitions with gparted... The /home is unlocated.

Dont know what to do next, dont want to lose this /home content.

Guess its iust something with the partitiontable, I hope it is. Seems that sda3 moved to a new partition. sdb is the usb dongle.
Any ideas or suggestions for me?

[IMG]http://i.stack.imgur.com/Gy8WQ.png[/IMG]

Edit: My fdisk -lu

    ```
user@debian:~$ sudo fdisk -lu
    
    Disk /dev/sda: 250.1 GB, 250059350016 bytes
    255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x1ebcccc9
    
       Device Boot      Start         End      Blocks   Id  System
    /dev/sda1            2048    39063551    19530752   83  Linux
    /dev/sda2        39065598   437198847   199066625    5  Extended
    /dev/sda3   *   437198848   437403647      102400    7  HPFS/NTFS
    /dev/sda4       437403648   488394751    25495552    7  HPFS/NTFS
    /dev/sda5       425340928   437196799     5927936   82  Linux swap / Solaris
    
    Disk /dev/sdb: 2021 MB, 2021654528 bytes
    63 heads, 62 sectors/track, 1010 cylinders, total 3948544 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x00000000
    
       Device Boot      Start         End      Blocks   Id  System
    /dev/sdb1   *          62     3945059     1972499    c  W95 FAT32 (LBA)
```

---

### Post by darkod on 2012-08-07
How exactly did you make the free space?

---

### Post by dennym on 2012-08-07
> **darkod said:**
> How exactly did you make the free space?

I made the /home partition smaller. Moved my swap partition to the end of the smaller /home then I shortend the extended partition to the minimum which were possible. So i got free space which is now known as sda3 and sda4

Everything was fine with my ubuntu after  this.

---

### Post by Cheesemill on 2012-08-07
How *exactly* did you resize and move your partitions?
 
Which software did you use, what steps did you take etc.

---

### Post by oldfred on 2012-08-07
I would be more suspicious of Windows as it writes partition table info. Boot Repair does not write info into partition table, just read it.

What does test disk show? It may find your old partition. You can install from repository.

repairs including testdisk info & links
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by dennym on 2012-08-07
> **oldfred said:**
> I would be more suspicious of Windows as it writes partition table info. Boot Repair does not write info into partition table, just read it.

What does test disk show? It may find your old partition. You can install from repository.

repairs including testdisk info & links
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)


All of the testdisk guides are windows partition related -.-
Ok according to test disk every partition is deleted oO There have to be something wrong with testdisk. Any idea?

```
Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
D Linux                    0  32 33  2431 118 55   39059456
D Linux                 2431 183 57 26476  30 50  386273280
D Linux Swap           26476  63 20 27214  61 31   11855856
D HPFS - NTFS          27214  94 17 27227  30  3     204800 [System-reservier
D HPFS - NTFS          27227  30  4 30401  42 41   50991104
```


So i checked this partition ```
D Linux 2431 183 57 26476  30 50  386273280
``` because this should be my home. And tada, there are my files still inside it.

Thinking about to get a 12.04 ubuntu install disk and reinstall it, there is a possibilty at the install where u can add the mount point, filesystem without formating it. What u think about this?

---

### Post by Kalanac on 2012-08-07
My guess is the partition has changed designation or maybe the UUID changed.  Check your /etc/fstab.

Try mounting the partition manually.  If that works, just update your fstab accordingly and things should return to normal.

---

### Post by dennym on 2012-08-07
> **Kalanac said:**
> My guess is the partition has changed designation or maybe the UUID changed.  Check your /etc/fstab.

Try mounting the partition manually.  If that works, just update your fstab accordingly and things should return to normal.


this is the /etc/fstab from my ubuntu installation

> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ee0eb828-edd1-4a0c-a988-7c5c6b81241f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=23ede6fe-1246-4d45-8d49-584b525077c0 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=38888049-6cc3-43fd-aa14-909244e922cd none            swap    sw              0       0
 I cant mount the /home partition manually, as u can see its unallocated.

And here is the testdisk log [pastin]("http://pastebin.com/yG90wJU3").com

also I have the fsck here
> 
user@debian:~$ sudo fsck /dev/sda2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?


Edit: for the completion

> **Cheesemill said:**
> How *exactly* did you resize and move your partitions?
 
Which software did you use, what steps did you take etc.

I uses the Boot repair live version on my usb dingle. I installed gparted. I did make the /home partition (is now the unallocated part) smaller. After this i moved the swap partition right at the end of the /home partition. Then i make the extended partition (sda2 in the pic) smaller, that it fits right to the /home and swap. So i got free space behind all my ubuntu partitions. The free space is now the NTFS partitions.

---

### Post by dennym on 2012-08-07
Sorry for the new reply, dont wanne mess up the last one.

There are 3 possibiltys i guess.

**First**

Did this:

```
user@debian:~$ sudo fsck.ext4 -v /dev/sda
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

So i could try the e2fsck, but Im not sure, because he recognize a ext2 fs. But there is no ext2.


**Second**

I could try to get my partition recovered by testdisk. But i dont know how secure this is or stable. There are no hints about that.


**Third**

Could use an ubuntu install disc to reinstall ubuntu, where I can add a partition with ext4 without formating it and set the mount point to /home. But I dont know how secure this is.



Any ideas or suggestion to that?

---

### Post by oldfred on 2012-08-07
The only easy way to recover partition is to use testdisk and change the d to undelete the partition. Testdisk normally finds all your old partitions, so the more you have changed them the more that it finds.

If testdisk shows files I would definitely back those up before they are totally gone.

The only other way is if you know the start & size of the partition sda6, you can write that into the partition table with some of the Linux tools.

First backup partition table
sudo sfdisk -d /dev/sda > parts_sda.txt


I think the parted commands to find a partition is using the same type of logic as testdisk. If you know start and size:

 GParted's partition-recovery tool.
Device -> Attempt Data Rescue in GParted
Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)

---

### Post by dennym on 2012-08-07
> **oldfred said:**
> The only easy way to recover partition is to use testdisk and change the d to undelete the partition. Testdisk normally finds all your old partitions, so the more you have changed them the more that it finds.

If testdisk shows files I would definitely back those up before they are totally gone.

The only other way is if you know the start & size of the partition sda6, you can write that into the partition table with some of the Linux tools.

First backup partition table
sudo sfdisk -d /dev/sda > parts_sda.txt


I think the parted commands to find a partition is using the same type of logic as testdisk. If you know start and size:

 GParted's partition-recovery tool.
Device -> Attempt Data Rescue in GParted
Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)


As you can see here every partition seems deleted oO. But they are there and usable and mountable.

> Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63      Partition               Start        End    Size in sectors 
D Linux                    0  32 33  2431 118 55   39059456 
D Linux                 2431 183 57 26476  30 50  386273280 
D Linux Swap           26476  63 20 27214  61 31   11855856 
D HPFS - NTFS          27214  94 17 27227  30  3     204800 [System-reservier 
D HPFS - NTFS          27227  30  4 30401  42 41   50991104

Sure to simly do the undelete on this partition?

best regards



So i did some more research on the ...
On the official site there was a wiki entry which said, that when the superblock is damaged some filesystems cant be mounted.
My testdisk is saying > EXT4 Large file Sparse superblock,. 
Maybe i should try to recover this superblock first from its backups? If its boot everything should be fine. If not i can still try testdisk?
I really dont know what to do first :/ Im kinda inexpierienced in this filesystem error thingy.

---

### Post by oldfred on 2012-08-07
Testdisk does not usually show them all deleted, so that worries me.

Post the backup of the partition table from sfdisk. Please use code tags to make it legible.

---

### Post by dennym on 2012-08-07
> **oldfred said:**
> Testdisk does not usually show them all deleted, so that worries me.

Post the backup of the partition table from sfdisk. Please use code tags to make it legible.


```
user@debian:~$ sudo sfdisk /dev/sda
Checking that no-one is using this disk right now ...
OK

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+   2431-   2432-  19530752   83  Linux
/dev/sda2       2431+  27214-  24783- 199066625    5  Extended
/dev/sda3   *  27214+  27227-     13-    102400    7  HPFS/NTFS
/dev/sda4      27227+  30401-   3175-  25495552    7  HPFS/NTFS
/dev/sda5      26476+  27214-    738-   5927936   82  Linux swap / Solaris
Input in the following format; absent fields get a default value.
<start> <size> <type [E,S,L,X,hex]> <bootable [-,*]> <c,h,s> <c,h,s>
Usually you only need to specify <start> and <size> (and perhaps <type>).

```

The partition should be apear from start 2431 to 26475 I guess.

---

### Post by oldfred on 2012-08-07
Did you run the command to backup the current table. The backup is slightly different format than the one you posted.

---

### Post by dennym on 2012-08-08
> **oldfred said:**
> Did you run the command to backup the current table. The backup is slightly different format than the one you posted.

Sorry i forgot the ```
-d
``` on ```
sfdisk
```.

this is my partition table backup, did it 5 minutes ago:

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 39061504, Id=83
/dev/sda2 : start= 39065598, size=398133250, Id= 5
/dev/sda3 : start=437198848, size=   204800, Id= 7, bootable
/dev/sda4 : start=437403648, size= 50991104, Id= 7
/dev/sda5 : start=425340928, size= 11855872, Id=82
```regards



Regarding to the testdisk usage. If i do the quicksearch he finds the 5 deleted partition, maybe some of them are from older partitioning. What to do next?

Do i have to change with the arrow keys the partition to logical or extended and then advance?

---

### Post by oldfred on 2012-08-08
I have not used testdisk to recover partition. Have you used the deeper search?

---

### Post by darkod on 2012-08-08
If testdisk can list the files correctly, most probably it can recover the partition. I guess it got messed up when you moved swap. That's why you need good planning of your hdd. Besides, you could have shrinked /home and the extended partition from the other end if swap was in the way. I always try to avoid moving a partition, I consider it dangerous.

Also, probably it would have been better to delete the swap partition instead of moving it, and create it later where ever you need it.

Anyway...
Try the testdisk recovery but be careful what you do. From what you posted so far, the recovery with testdisk (changing the D type of each partition) should go something like:
For the first Linux partition (smaller one) into P (primary partition)
For the second Linux partition into L (logical)
For the Linux swap partition into L (logical)
For the small NTFS System Reserved into * (primary bootable)
For the large NTFS into P (primary)

That should be it.

---

### Post by dennym on 2012-08-08
> **oldfred said:**
> I have not used testdisk to recover partition. Have you used the deeper search?


I found my partition with quick search, but i dont know how to advance next.
I can change the partition type with left and right arrow key, but what do i have to choose? logical, extended, primary?

already backuped some stuff, iust in case.

---

### Post by dennym on 2012-08-08
> **darkod said:**
> If testdisk can list the files correctly, most probably it can recover the partition. I guess it got messed up when you moved swap. That's why you need good planning of your hdd. Besides, you could have shrinked /home and the extended partition from the other end if swap was in the way. I always try to avoid moving a partition, I consider it dangerous.

Also, probably it would have been better to delete the swap partition instead of moving it, and create it later where ever you need it.

Anyway...
Try the testdisk recovery but be careful what you do. From what you posted so far, the recovery with testdisk (changing the D type of each partition) should go something like:
For the first Linux partition (smaller one) into P (primary partition)
For the second Linux partition into L (logical)
For the Linux swap partition into L (logical)
For the small NTFS System Reserved into * (primary bootable)
For the large NTFS into P (primary)

That should be it.


Hey darkod, did this and got my guts and everything works FINE...grub is still there with the right entrys... my ubuntu runs like before and windows also runs fine.


Thanks to oldfred and darkod for the help.

have a nice day :D


best regards
dennym

---

