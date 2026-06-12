---
title: "Unable to see partitions to install Ubuntu 11.10 alongside Windows 7"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by akduncan on 2012-01-04
I recently bought a new hard drive from Amazon. I bought the WD3200BEKT drive. 
It's WD 320 Gb, 7200 RPM, Scorpio Black drive. I bought it in "like new" condition.
I installed WIndows 7 Ultimate on it with no issues.

However, I wanted to install Ubuntu 11.10 on there as well, but when I use the live CD or USB version, the installer does not see the partitions.

From other posts, I wonder if it might have something to do with the installer not reading the MBR correctly. EDIT: after running these commands from another thread, it looks like the partition table may be bad, but I have no idea what to do from here.

Any help would be much appreciated!!

Here is what I have so far.

ubuntu@ubuntu:~$ sudo sfdisk -l

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+     12-     13-    102400    7  HPFS/NTFS/exFAT
/dev/sda2         12+  38913-  38901- 312466432    7  HPFS/NTFS/exFAT
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty

Disk /dev/sdb: 1022 cylinders, 247 heads, 62 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/102/38 (instead of 1022/247/62).
For this listing I'll assume that geometry.
Units = cylinders of 1984512 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+   4041-   4041-   7830456    b  W95 FAT32
        start: (c,h,s) expected (0,57,27) found (0,34,51)
        end: (c,h,s) expected (1023,101,38) found (242,101,38)
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x808cbbe5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   625139711   312466432    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 8019 MB, 8019509248 bytes
102 heads, 38 sectors/track, 4041 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2192    15663103     7830456    b  W95 FAT32


ubuntu@ubuntu:~$ sudo dmraid -r /dev/sda
/dev/sda: ddf1, ".ddf1_disks", GROUP, ok, 623902720 sectors, data@ 0

ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=512 count=1 | hexdump -C
1+0 records in
1+0 records out
512 bytes (512 B) copied00000000  33 c0 8e d0 bc 00 7c 8e  c0 8e d8 be 00 7c bf 00  |3.....|......|..|
00000010  06 b9 00 02 fc f3 a4 50  68 1c 06 cb fb b9 04 00  |.......Ph.......|
, 0.000525012 s, 975 kB/s
00000020  bd be 07 80 7e 00 00 7c  0b 0f 85 0e 01 83 c5 10  |....~..|........|
00000030  e2 f1 cd 18 88 56 00 55  c6 46 11 05 c6 46 10 00  |.....V.U.F...F..|
00000040  b4 41 bb aa 55 cd 13 5d  72 0f 81 fb 55 aa 75 09  |.A..U..]r...U.u.|
00000050  f7 c1 01 00 74 03 fe 46  10 66 60 80 7e 10 00 74  |....t..F.f`.~..t|
00000060  26 66 68 00 00 00 00 66  ff 76 08 68 00 00 68 00  |&fh....f.v.h..h.|
00000070  7c 68 01 00 68 10 00 b4  42 8a 56 00 8b f4 cd 13  ||h..h...B.V.....|
00000080  9f 83 c4 10 9e eb 14 b8  01 02 bb 00 7c 8a 56 00  |............|.V.|
00000090  8a 76 01 8a 4e 02 8a 6e  03 cd 13 66 61 73 1c fe  |.v..N..n...fas..|
000000a0  4e 11 75 0c 80 7e 00 80  0f 84 8a 00 b2 80 eb 84  |N.u..~..........|
000000b0  55 32 e4 8a 56 00 cd 13  5d eb 9e 81 3e fe 7d 55  |U2..V...]...>.}U|
000000c0  aa 75 6e ff 76 00 e8 8d  00 75 17 fa b0 d1 e6 64  |.un.v....u.....d|
000000d0  e8 83 00 b0 df e6 60 e8  7c 00 b0 ff e6 64 e8 75  |......`.|....d.u|
000000e0  00 fb b8 00 bb cd 1a 66  23 c0 75 3b 66 81 fb 54  |.......f#.u;f..T|
000000f0  43 50 41 75 32 81 f9 02  01 72 2c 66 68 07 bb 00  |CPAu2....r,fh...|
00000100  00 66 68 00 02 00 00 66  68 08 00 00 00 66 53 66  |.fh....fh....fSf|
00000110  53 66 55 66 68 00 00 00  00 66 68 00 7c 00 00 66  |SfUfh....fh.|..f|
00000120  61 68 00 00 07 cd 1a 5a  32 f6 ea 00 7c 00 00 cd  |ah.....Z2...|...|
00000130  18 a0 b7 07 eb 08 a0 b6  07 eb 03 a0 b5 07 32 e4  |..............2.|
00000140  05 00 07 8b f0 ac 3c 00  74 09 bb 07 00 b4 0e cd  |......<.t.......|
00000150  10 eb f2 f4 eb fd 2b c9  e4 64 eb 00 24 02 e0 f8  |......+..d..$...|
00000160  24 02 c3 49 6e 76 61 6c  69 64 20 70 61 72 74 69  |$..Invalid parti|
00000170  74 69 6f 6e 20 74 61 62  6c 65 00 45 72 72 6f 72  |tion table.Error|
00000180  20 6c 6f 61 64 69 6e 67  20 6f 70 65 72 61 74 69  | loading operati|
00000190  6e 67 20 73 79 73 74 65  6d 00 4d 69 73 73 69 6e  |ng system.Missin|
000001a0  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
000001b0  65 6d 00 00 00 63 7b 9a  e5 bb 8c 80 29 92 80 20  |em...c{.....).. |
000001c0  21 00 07 df 13 0c 00 08  00 00 00 20 03 00 00 df  |!.......... ....|
000001d0  14 0c 07 fe ff ff 00 28  03 00 00 b8 3f 25 00 00  |.......(....?%..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by carl4926 on 2012-01-04
Who on earth partitioned it like that?

You only need One ntfs partition to install W7

I recommend you start again. Use Parted Magic to delete everything. 
Create a single ntfs partition
swap
ext4 30GB for /
ext4 for /home all the remaining space

Then install windows followed by Ubuntu

---

### Post by akduncan on 2012-01-04
Actually, Windows 7 did the partitioning. I've never had a problem with it before.

---

### Post by darkod on 2012-01-04
If you planned to dual boot, your first mistake was to allow win7 to take the whole disk. Why create one big ntfs partition when you know you want to install a linux OS too? Of course, maybe you made the decision to install ubuntu later.

Tell us exactly what happens when you try to install, it does now see the partitions (shows the disk as unallocated if you select the Something Else option, manual partitioning), or it does not show the disk at all?

If the disk is shown as unallocated, usually it's because of errors in the partition table.

If the disk is not shown at all, usually it was used in RAID and the meta data is still there. To fix that boot ubuntu in Try Ubuntu mode, and in terminal do:
sudo dmraid -E -r /dev/sda

Confirm you want to remove the raid meta data, and that's it.

If that fixes it, you still have to address the fact you have no unpartitioned space for ubuntu. Boot win7 and use Disk Management to shrink the C: partition for as much space as you want to allocate to ubuntu. After that boot the instaler and tell it to use the free space, or partition manually.

EDIT: I didn't notice before that you tried sudo dmraid -r, but still try my command above, sudo dmraid -E -r /dev/sda.

PPS. And make sure any RAID options in bios are disabled.

---

### Post by akduncan on 2012-01-04
> **darkod said:**
> If you planned to dual boot, your first mistake was to allow win7 to take the whole disk. Why create one big ntfs partition when you know you want to install a linux OS too? Of course, maybe you made the decision to install ubuntu later.

Tell us exactly what happens when you try to install, it does now see the partitions (shows the disk as unallocated if you select the Something Else option, manual partitioning), or it does not show the disk at all?

It shows no partition tables and under the drop down list, it only gives the /dev/sda option. 

> If the disk is shown as unallocated, usually it's because of errors in the partition table.

If the disk is not shown at all, usually it was used in RAID and the meta data is still there. To fix that boot ubuntu in Try Ubuntu mode, and in terminal do:
sudo dmraid -E -r /dev/sda

Confirm you want to remove the raid meta data, and that's it.

If that fixes it, you still have to address the fact you have no unpartitioned space for ubuntu. Boot win7 and use Disk Management to shrink the C: partition for as much space as you want to allocate to ubuntu. After that boot the instaler and tell it to use the free space, or partition manually.

EDIT: I didn't notice before that you tried sudo dmraid -r, but still try my command above, sudo dmraid -E -r /dev/sda.

PPS. And make sure any RAID options in bios are disabled.

ubuntu@ubuntu:~$ sudo dmraid -E -r /dev/sda
Do you really want to erase "ddf1" ondisk metadata on /dev/sda ? [y/n] :y
ERROR: ddf1: seeking device "/dev/sda" to 163877341626368
ERROR: writing metadata to /dev/sda, offset 320072932864 sectors, size 0 bytes returned 0
ERROR: erasing ondisk metadata on /dev/sda

---

### Post by akduncan on 2012-01-04
Also, there is no option for RAID as this is a d820 laptop. I checked to make sure. It's on the latest revision of the BIOS as well. A10

---

### Post by darkod on 2012-01-04
But the disk clearly has raid meta data on it:

```
ubuntu@ubuntu:~$ sudo dmraid -E -r /dev/sda
Do you really want to erase "ddf1" ondisk metadata on /dev/sda ? [y/n] :y
ERROR: ddf1: seeking device "/dev/sda" to 163877341626368
ERROR: writing metadata to /dev/sda, offset 320072932864 sectors, size 0 bytes returned 0
ERROR: erasing ondisk metadata on /dev/sda
```

Out of what ever reason it can't be removed. Usually this command removes the meta data without problems.

Try googling the errors it issued if the search finds anything.

---

### Post by akduncan on 2012-01-04
So far, it looks like I'll have to dd at least the first 50Mb of the drive, if not the whole drive.

---

### Post by darkod on 2012-01-04
That's one option, if you don't mind losing the win7 install.

---

### Post by akduncan on 2012-01-04
I'd prefer not to lose the win7 install, as I put quite a bit of effort into making it just the way I like it. 

Isn't there a way to reset the mbr without completely wiping everything on the drive?

---

### Post by darkod on 2012-01-04
Sorry, but so far I haven't been able to find a way to zero out just the raid data without deleting the partition table.

---

### Post by darkod on 2012-01-04
Here seems to be a command to use dd to zero out the last 1MB of the hdd. Other articles also say that dmraid saves information at the end of the disk, not the beginning.

[http://unix.stackexchange.com/questions/13848/wipe-last-1mb-of-a-hard-drive](http://unix.stackexchange.com/questions/13848/wipe-last-1mb-of-a-hard-drive)

Try that command to delete the last 1MB, that should leave your win7 untouched if it's on the beginning of the disk.

---

### Post by akduncan on 2012-01-05
Thanks for the help. I decided to start from scratch and format everything. I'm checking now to make sure I can install everything side by side.

---

### Post by akduncan on 2012-01-05
Alright, Ubuntu still will not see the drive. How would I go about properly formatting the drive?

---

### Post by carl4926 on 2012-01-05
I use Parted Magic
But last time I created a NTFS for win7, the win7 installer spat dummy at it. I had to use a XP disk to format the NTFS partition again, because the win7 installer wouldn't have it.

Let me show you what my little R61 HD is like

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x93900d8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   136327589    68163763+   7  HPFS/NTFS/exFAT
/dev/sda2   *   136327651   312576704    88124527    5  Extended
/dev/sda5       136327653   141259544     2465946   82  Linux swap / Solaris
/dev/sda6       141259608   177582509    18161451   83  Linux
/dev/sda7       177584128   312575999    67495936   83  Linux

```

---

### Post by akduncan on 2012-01-05
I'm taking your suggestion and formatting it with a xp disc.

---

### Post by darkod on 2012-01-05
Since you are starting from scratch you might as well write a new empty partition table on the disk. That will get rid of any errors in the table.

Did you check if the disk has raid meta data left over?

How do you plan to use XP to format a partition since it can't run in live mode like ubuntu?

@carl
That setup you show works like that? The boot flag is on the extended partition and it needs to be on the windows system partition.

---

### Post by akduncan on 2012-01-05
I let the XP disc format the drive during a setup, but killed it after it finished. This is what it looks like now. From the best I can tell, it's ready for me to try it again. yes?

ubuntu@ubuntu:~$ sudo sfdisk -l

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  38912   38913- 312568641    7  HPFS/NTFS/exFAT
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x38938f60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625137344   312568641    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ sudo dmraid -r /dev/sda
/dev/sda: ddf1, ".ddf1_disks", GROUP, ok, 623902720 sectors, data@ 0




EDIT: I loaded the Ubuntu live CD and ran GParted. It now sees the partitions, and gives me a choice of how to install the OS.

---

### Post by darkod on 2012-01-05
> **akduncan said:**
> 
ubuntu@ubuntu:~$ sudo dmraid -r /dev/sda
/dev/sda: ddf1, ".ddf1_disks", GROUP, ok, 623902720 sectors, data@ 0

Doesn't look ready, the raid data is still there. This was some kind of very weird raid setup and probably they just took the disks out instead of first deleting the raid array. So the data remained there and in some cases it seems it refuses to get deleted because it's not in the raid array any more.

Try writing a new partition table, either with Gparted from live mode, or with parted in command line. The command with parted would be:
sudo parted /dev/sda
mklabel msdos
quit

Then check if the raid data is still there with the same dmraid -r command.

---

### Post by akduncan on 2012-01-05
the Gparted is what solved the issue. I'm able to install Ubuntu alongside Windows 7. Thank you for the help!!

---

### Post by carl4926 on 2012-01-05
> @carl
That setup you show works like that? The boot flag is on the extended  partition and it needs to be on the windows system partition.

My setup is quite correct.
And the boot flag is irrelevant if you install grub to the MBR

Just FYI: That partition layout is not my Ubuntu machine, but openSUSE, which still uses legacy grub and the default for the installer is not to write to the MBR, and if root is in the extended space the boot flag goes on the extended.

God to know the OP sorted it though

---

