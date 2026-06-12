---
title: "A few partition problems."
date: 2011-12-15
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2011-12-15
Firstly so you know what I'm working with here:

```
dusf@banshee:~$ sudo fdisk -l
[sudo] password for dusf: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1305    10482381    7  HPFS/NTFS
/dev/sda2   *        1306        3263    15727635    7  HPFS/NTFS
/dev/sda3            3590       38913   283739999    f  W95 Ext'd (LBA)
/dev/sda5            3590        4111     4192933+  83  Linux
/dev/sda6            4112        6069    15727603+  83  Linux
/dev/sda7            6070        9985    31455238+  83  Linux
/dev/sda8            9986       38913   232364160    7  HPFS/NTFS
```

Unfortunately at the moment GParted (latest USB live install and here on my Xubuntu 11.04 desktop) is just so 298 of unallocated space with a red exclamation mark 'unable to satisfy all constraints on the partition', and nothing else.

When I test it to see if it would even let me create a new partition the output is:

> 
No partition table found on device /dev/sda

A partition table is required before partitions can be added.
To create a new partition table choose the menu item:
Device --> Create Partition Table.

The thing is I am logged into linux running on one of the partitions as I type this.

Let me explain how I got here. I used to have visible in GParted: a linux / partition, a linux ~ partition, and a 4GB linux-swap, partition for Win XP, another for Win 7, and the largest partition is DUMP where I store media on NTFS.

I wanted to take some space from DUMP and move it over to the Win XP partition but GParted was showing red exclamation marks on DUMP and the 4GB partition which somehow was unformatted. GParted suggested I execute fdisk -f in windows which I did (and checked for bad secotrs etc) for DUMP but since the 4GB partition was not visible in Windows Explorer and EASEUS Partition Master was able to see it I formatted it to FAT32 in the hope it would once more be workable in GParted.

This unfortunately not the case. On reboot the output was:

```
error: file not found
grub rescue > 
```

I definitely only formatted the 4GB partition so I'm not sure why this happened.

GParted was then, as it is now showing just one unallocated 298GB unallocated partition. 

I was able to boot into a Xubuntu Live CD, mount /, and do a grub--install which fortunately has let me log back into linux and restored my old grub menu showing all my operating systems.

I'm just wondering what should be done about the unallocated space? Even if I didn't want to resize my Win XP partition using GParted something must be wrong for this to be showing.

If relevant when I start Xubuntu now I see:

```
Xubuntu 11.04

..[21.180678] device-mapper: table: 252:0: crypt: Device lookup failed

An error occured while mounting /media/DUMP

Press S to skip Mounting and M for manual recovery.
```

I press S and am able to mount DUMP once I have logged in - this never happened before.

---

### Post by darkod on 2011-12-15
OK, let me see if I understand this right:
Your plan was to shrink the last partition on the disk, sda8, and use that space to enlarge one of the ntfs partitions on the front of the disk? In what world can you enlarge a partition if it is not physically next to the unallocated space?

To add to that, you formatted your swap partition just so windows can see it???

Anyway. Try testdisk to get scan and try to get your partitions back (the original structure). See what it comes up with while reading the disk.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Dáire Fagan on 2011-12-15
> **darkod said:**
> OK, let me see if I understand this right:
Your plan was to shrink the last partition on the disk, sda8, and use that space to enlarge one of the ntfs partitions on the front of the disk? In what world can you enlarge a partition if it is not physically next to the unallocated space?

To add to that, you formatted your swap partition just so windows can see it???

Anyway. Try testdisk to get scan and try to get your partitions back (the original structure). See what it comes up with while reading the disk.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)


No the plan was to shrink the partition, then move the space to the front of the disk, then enlarge the NTFS partition.

No I did not just format my swap partition so Windows could see it. Linux and Windows both were not seeing the partition at all in Explorer or Nautilus. GParted was seeing it, advising me to run chkdsk on it which I could not do. EASEUS Partition Master did see it so I formatted an already non-working linux swap partition to something that would allow me work on it elsewhere, like GParted.

---

### Post by darkod on 2011-12-15
> **dusf said:**
> No the plan was to shrink the partition, then move the space to the front of the disk, then enlarge the NTFS partition.

No I did not just format my swap partition so Windows could see it. Linux and Windows both were not seeing the partition at all in Explorer or Nautilus. GParted was seeing it, advising me to run chkdsk on it which I could not do. EASEUS Partition Master did see it so I formatted an already non-working linux swap partition to something that would allow me work on it elsewhere, like GParted.

You can't "move" the space to the front of the disk. Actually, you can but what it does is move all partitions back to make space to the front. So your chances something to go bad during the move are extremely high if all partitions get moved around.

---

### Post by Dáire Fagan on 2011-12-15
Changed fstab from this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=57b7cc02-c00b-49ea-8873-b3918feb9eea /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=47adf8d9-0d98-4d8f-8358-db60391ff3c9 /home           ext4    defaults        0       2
#/dev/sda6       none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/sda5 /media/DUMP ntfs-3g defaults 0 0

```

to this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=57b7cc02-c00b-49ea-8873-b3918feb9eea /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=47adf8d9-0d98-4d8f-8358-db60391ff3c9 /home           ext4    defaults        0       2
#/dev/sda6       none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0
UUID=4442D7A83361F05F    /media/DUMP    ntfs-3g    defaults    0    0
```

and I am now able to log into linux with my /, ~, and DUMP partitions auto mounting without any erros. My Win XP and Win 7 partitions will mount on demand.

I am still unable to configure the swap drive or move space around though because GParted still sees only one chunk of unallocated space reportedly missing a partition table and giving an error 'Unable to satisfy all constraints on the partition'.

---

### Post by Dáire Fagan on 2011-12-15
All drives including swap now active and working.

I used fdisk to delete the 4gb file and recreate a linux-swap partition.

Changed fstab to:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=57b7cc02-c00b-49ea-8873-b3918feb9eea /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=47adf8d9-0d98-4d8f-8358-db60391ff3c9 /home           ext4    defaults        0       2
#/dev/sda5       none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
UUID=4442D7A83361F05F    /media/DUMP    ntfs-3g    defaults    0    0
```

and changed sda6 to sda5 in /etc/crypttab:

```
# <target name>    <source device>        <key file>    <options>
cryptswap1 /dev/sda5 /dev/urandom swap,cipher=aes-cbc-essiv:sha256

```

Still though, GParted sees only one chunk of unallocated space and won't let me work with it.

I have looked at TestDisk, and it does mention partition table recovery but I have not found what I am supposed to do exactly.

---

### Post by Dáire Fagan on 2011-12-15
```
dusf@banshee:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1305    10482381    7  HPFS/NTFS
/dev/sda2   *        1306        3263    15727635    7  HPFS/NTFS
/dev/sda3            3590       38913   283739999    f  W95 Ext'd (LBA)
/dev/sda5            3590        4111     4192902+  82  Linux swap / Solaris
/dev/sda6            4112        6069    15727603+  83  Linux
/dev/sda7            6070        9985    31455238+  83  Linux
/dev/sda8            9986       38913   232364160    7  HPFS/NTFS

Disk /dev/dm-0: 4293 MB, 4293532160 bytes
255 heads, 63 sectors/track, 521 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcbf30dbc

Disk /dev/dm-0 doesn't contain a valid partition table
```

---

### Post by Dáire Fagan on 2011-12-16
Bump.

---

### Post by Quackers on 2011-12-16
It may be that you have a damaged partition table.
Please post the output of ```
sudo fdisk -lu
```

---

### Post by Dáire Fagan on 2011-12-16
> **Quackers said:**
> It may be that you have a damaged partition table.
Please post the output of ```
sudo fdisk -lu
```

Yes, I think I mentioned that in my first post :)
```

dusf@banshee:~$ sudo fdisk -lu
[sudo] password for dusf: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20964824    10482381    7  HPFS/NTFS
/dev/sda2        20964825    52420094    15727635    7  HPFS/NTFS
/dev/sda3        57657285   625137344   283740030    f  W95 Ext'd (LBA)
/dev/sda5        57657348    66043213     4192933   83  Linux
/dev/sda6        66043278    97498477    15727600   83  Linux
/dev/sda7        97498548   160409019    31455236   83  Linux
/dev/sda8       160409025   625137337   232364156+   7  HPFS/NTFS

Disk /dev/dm-0: 4293 MB, 4293532160 bytes
255 heads, 63 sectors/track, 521 cylinders, total 8385805 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x63ab5b60

Disk /dev/dm-0 doesn't contain a valid partition table

```

I have just used TestDisk recommended by another poster to analyse the disk where I found 2 extra swap partitions not showing in fdisk -l which I deleted using the software. After that I wrote the partition table and was advised I need to reboot which I'm doing now.
[URL="http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery"]
http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery[/URL]

Should 'Disk /dev/dm-0 doesn't contain a valid partition table' concern me? In test disk I am given a choice of three disks, my physical one, encrypted swap, or /dev/dm-0. I have only thus far worked on the former.

---

### Post by Quackers on 2011-12-16
I don't see anything wrong with the partition table for /dev/sda. The error shown for /dev/dm-0 I'm afraid I don't know how significant that may be. It seems to be LVM (or RAID) related, possibly due to an encrypted partition. I try to steer clear of anything that will complicate things as a general rule. It makes unravelling problems more difficult.
Has this drive been used in a raid array at any time?

---

### Post by Dáire Fagan on 2011-12-16
> **Quackers said:**
> I don't see anything wrong with the partition table for /dev/sda. The error shown for /dev/dm-0 I'm afraid I don't know how significant that may be. It seems to be LVM (or RAID) related, possibly due to an encrypted partition. I try to steer clear of anything that will complicate things as a general rule. It makes unravelling problems more difficult.
Has this drive been used in a raid array at any time?

Never used in RAID no.

GParted had been mentioning a damaged or missing partition table in one of my first posts.

After creating a new one with TestDisk I can once again see all my partitions in GParted :)

Although, what I have assigned as a linux swap in fstab has a warning on it, please see the screenshot.

Strangely the partition is functioning though evident from:

```
dusf@banshee:~$ sudo free -m
             total       used       free     shared    buffers     cached
Mem:           999        958         40          0          0         51
-/+ buffers/cache:        907         92
Swap:         4094        316       3777

```

I think I am going to try delete and/or format it to linux-swap from GParted USB Live.

Strange how it can function without GParted showing it as linux swap, although that's swap I selected in fdisk despite it not being shown as that in fdisk -l.

---

### Post by Quackers on 2011-12-16
Glad you have found a resolution! :-)
Gparted iirc, only reads the partition table, not the actual partitions, so any problem in that table and Gparted baulks - even though the actual partitions may be fine.
In Gparted right-click on sda5 and select "information". What info is given there?

---

### Post by Dáire Fagan on 2011-12-16
> **Quackers said:**
> Glad you have found a resolution! :-)
Gparted iirc, only reads the partition table, not the actual partitions, so any problem in that table and Gparted baulks - even though the actual partitions may be fine.
In Gparted right-click on sda5 and select "information". What info is given there?

It's on the left hand side of the screenshot! :)

---

### Post by Quackers on 2011-12-16
oops, sorry! :-)
It's strange, but if everything is working it may be an idea to leave it. Alternatively you could delete and re-create, but that would change the UUID.

---

### Post by Dáire Fagan on 2011-12-16
> **Quackers said:**
> oops, sorry! :-)
It's strange, but if everything is working it may be an idea to leave it. Alternatively you could delete and re-create, but that would change the UUID.

I booted up GParted USB Live deleted the swap partition, and re-created it successfully  without errors but when I tried to reboot into Xubuntu I received the same old error

```
error: file not found
grub rescue >
```

From what I've learnt troubleshooting this I knew I had to boot into Xubuntu Live and do a grub--install (and the necessary steps before it) so that's what I did.

I was then able to boot again but the 4GB swap drive was again unrecognised by GParted so I am going in circles!

---

