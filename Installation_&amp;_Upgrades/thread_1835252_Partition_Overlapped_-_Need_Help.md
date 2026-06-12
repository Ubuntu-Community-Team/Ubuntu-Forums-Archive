---
title: "Partition Overlapped - Need Help"
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by mastergaurav on 2011-08-29
Hi,

My Dell N4010 has, somehow, got overlapped paritions.

testdisk ("Deeper Search") gives me the following:

```

Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1    10 254 63     176652 [DellUtility]
P FAT32 LBA               11   0  1  4188 254 63   67119570 [ Unlabeled]
D HPFS - NTFS             11  23 13  1300 243 31   20721664 [RECOVERY]
D HPFS - NTFS           1300 243 31  2590 208 49   20721664
D HPFS - NTFS           1300 243 32  7782 254 57  104134049 [C DRIVE]
D HPFS - NTFS           1300 243 32 58190  90 12  913928192
D HPFS - NTFS           1300 243 32 60801  47 46  955871232
D HPFS - NTFS           7784   0  1 13004 254 51   83875353 [D DRIVE]
D HPFS - NTFS           7784   0 13 13004 254 63   83875353
D HPFS - NTFS          13005   1  1 24796 254 63  189438417 [PERSONAL]
D HPFS - NTFS          24797   1  1 37850 254 57  209712441 [OFFICIAL]
D HPFS - NTFS          37851   1  1 50904 254 57  209712441 [G DRIVE]
D Linux                50905   1 41 52149 254  9   20000768
D Linux                51448 117 62 52693 115 30   20000768
D Linux                51449  25 33 52694  23  1   20000768
D Linux                51449 155 35 52694 153  3   20000768
D Linux                51509   4 16 52754   1 47   20000768
D Linux                51512  51 60 52757  49 28   20000768
D Linux                51512 116 61 52757 114 29   20000768
D Linux                51512 214 31 52757 211 62   20000768
D Linux                51513   1  1 52757 253 32   20000768
D Linux                51516  39 44 52761  37 12   20000768
D Linux                52150  31 42 53394 251 41   19998720
D Linux Swap           53395  29 11 53457  50 17     997360

```

Result of ```
fdisk -ul
```

```

Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0xe804 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x28000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      176714       88326   de  Dell Utility
/dev/sda2   *      178176    20899839    10360832    7  HPFS/NTFS
/dev/sda3        20899840   125033894    52067027+   7  HPFS/NTFS
/dev/sda4       104775991   976773119   435998564+   f  W95 Ext'd (LBA)
/dev/sda5   ?  1271515563  4832842606  1780663522   50  OnTrack DM

```

Similarly, output of ```
sfdisk -l
```

```

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

sfdisk: ERROR: sector 104775991 does not have an msdos signature
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+     10      11-     88326   de  Dell Utility
/dev/sda2   *     11+   1300-   1290-  10360832    7  HPFS/NTFS
/dev/sda3       1300+   7782    6483-  52067027+   7  HPFS/NTFS
/dev/sda4       6522+  60801-  54280- 435998564+   f  W95 Ext'd (LBA)

```

And the output of ```
sfdisk -d
```

```

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

sfdisk: ERROR: sector 104775991 does not have an msdos signature
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=   176652, Id=de
/dev/sda2 : start=   178176, size= 20721664, Id= 7, bootable
/dev/sda3 : start= 20899840, size=104134055, Id= 7
/dev/sda4 : start=104775991, size=871997129, Id= f

```


Any help will be appreciated. I have over 400GB of partition space not visible, with over 300GB of data.

The good part is that testdisk can list all the files, which I should be able to recover (take backup on external drive)... but my Ubuntu OS partition is not visible and so are a bunch of my Windows partitions. Any direct recovery will be of great help!


-Gaurav
[www.mastergaurav.com](www.mastergaurav.com)

---

### Post by fdrake on 2011-08-29
boot from a live cd or from your ubuntu partition:
```

sudo apt-get install ntfs-3g
sudo umount /dev/sda3
sudo umount /dev/sda4
sudo ntfsfix /dev/sda3

```

installation of ntfs-3g (in case you dont have it installed) may require a reboot so the live cd option may not be appropriate in this case.

---

### Post by YesWeCan on 2011-08-29
It looks like your EBR has been corrupted.
Could you post the output of
sudo dd if=/dev/sda bs=512 count=1 skip=104775991 | hexdump -C

---

### Post by mastergaurav on 2011-08-29
> **YesWeCan said:**
> It looks like your EBR has been corrupted.
Could you post the output of
sudo dd if=/dev/sda bs=512 count=1 skip=104775991 | hexdump -C

Here you go:

```

00000000  d8 8b d9 8b 4d d8 33 d2  e8 53 d9 ff ff 85 c0 74  |....M.3..S.....t|
00000010  0a 33 c0 8d 65 f4 5b 5e  5f 5d c3 33 d2 89 55 d4  |.3..e.[^_].3..U.|
00000020  83 bb ec 00 00 00 00 74  3d 8b b3 ec 00 00 00 8b  |.......t=.......|
00000030  4d d8 8b 01 8b 40 28 ff  50 10 8b d0 8b ce 39 09  |M....@(.P.....9.|
00000040  e8 3b 95 00 00 8b f0 85  f6 74 18 81 3e 2c 78 20  |.;.......t..>,x |
00000050  30 75 02 eb 0e 8b d6 b9  2c 78 20 30 e8 47 97 f0  |0u......,x 0.G..|
00000060  ff 8b f0 89 75 d4 8b 0d  f8 13 00 30 ba 16 01 00  |....u......0....|
00000070  00 e8 fa 96 f0 ff 89 45  c0 8b 80 54 01 00 00 3b  |.......E...T...;|
00000080  45 d4 75 0a 33 c0 8d 65  f4 5b 5e 5f 5d c3 83 7d  |E.u.3..e.[^_]..}|
00000090  d4 00 74 0b 8b 45 d4 8d  65 f4 5b 5e 5f 5d c3 89  |..t..E..e.[^_]..|
000000a0  5d d0 8b cb e8 37 89 f0  ff 83 bb ec 00 00 00 00  |]....7..........|
000000b0  74 3d 8b b3 ec 00 00 00  8b 4d d8 8b 01 8b 40 28  |t=.......M....@(|
000000c0  ff 50 10 8b d0 8b ce 39  09 e8 b2 94 00 00 8b f0  |.P.....9........|
000000d0  85 f6 74 18 81 3e 2c 78  20 30 75 02 eb 0e 8b d6  |..t..>,x 0u.....|
000000e0  b9 2c 78 20 30 e8 be 96  f0 ff 8b f0 89 75 d4 8b  |.,x 0........u..|
000000f0  45 c0 8b 80 54 01 00 00  3b 45 d4 75 1d 33 d2 89  |E...T...;E.u.3..|
00000100  55 cc c7 45 e4 00 00 00  00 c7 45 e8 fc 00 00 00  |U..E......E.....|
00000110  68 91 ec 12 30 e9 61 01  00 00 83 7d d4 00 74 1e  |h...0.a....}..t.|
00000120  8b 45 d4 89 45 cc c7 45  e4 00 00 00 00 c7 45 e8  |.E..E..E......E.|
00000130  fc 00 00 00 68 9a ec 12  30 e9 3d 01 00 00 8b cb  |....h...0.=.....|
00000140  8b 01 8b 40 64 ff 50 04  89 45 c8 33 ff 8b 40 08  |...@d.P..E.3..@.|
00000150  89 45 dc 85 c0 0f 8e 7d  00 00 00 8b 45 c8 8b 50  |.E.....}....E..P|
00000160  04 8b 45 c8 8b 40 04 3b  78 04 0f 83 06 01 00 00  |..E..@.;x.......|
00000170  8b 74 b8 0c 85 f6 74 18  81 3e 2c 78 20 30 75 02  |.t....t..>,x 0u.|
00000180  eb 0e 8b d6 b9 2c 78 20  30 e8 1a 96 f0 ff 8b f0  |.....,x 0.......|
00000190  89 75 c4 8b b6 84 00 00  00 8b 46 04 83 78 04 00  |.u........F..x..|
000001a0  0f 86 d0 00 00 00 8b 48  0c 8b 01 8b 40 2c ff 10  |.......H....@,..|
000001b0  8b c8 e8 79 1f 00 00 8b  d0 8b 4d d8 8b 01 8b 40  |...y......M....@|
000001c0  68 ff 50 18 85 c0 74 08  8b 45 c4 89 45 d4 eb 08  |h.P...t..E..E...|
000001d0  83 c7 01 3b 7d dc 7c 89  83 bb ec 00 00 00 00 75  |...;}.|........u|
000001e0  2e b9 34 68 20 30 e8 a5  95 f0 ff 8b f0 ba 10 00  |..4h 0..........|
000001f0  00 00 b9 e2 38 00 30 e8  3c 96 f0 ff 8d 56 04 e8  |....8.0.<....V..|
00000200

```

---

### Post by mastergaurav on 2011-08-29
> **fdrake said:**
> boot from a live cd or from your ubuntu partition:


Thankfully, ntfsfix is already installed with Live CD.

Will try it after I've copied all the content to my external drive (using testdisk).

I don't want to take any chances with the data right now.



Thanks!

---

### Post by YesWeCan on 2011-08-29
It is garbage.
The extended partition entry in the MBR needs reconstructing, and the first EBR needs locating (see [http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)).

This may or may not be feasible to do by hand. Let's see if the EBR is somewhere obvious and is intact. The partition labelled "PERSONAL" is the first logical and it should be preceded by an EBR with at least a 2 sector gap. I just need to figure out the sector of this partition from the testdisk CHS address.

---

### Post by YesWeCan on 2011-08-29
I make the start sector 208925388
= C x 16065 + H x 63 + S - 1

So have a look at a few sectors before this one, say the preceding 10:
sudo dd if=/dev/sda bs=512 count=10 skip=208925378 | hexdump - C | more
A good EBR sector should end with 55AA.

If you find it please post it.

---

### Post by YesWeCan on 2011-08-29
Actually, I now think the D: drive must be the first logical because there are three before it:
Dell utility
recovery
C:

The fourth is extended
So the first logical must be D: at sector 125049960
Have a look at the 10 sectors preceding D: 

The EBR has to be in the range 125033895 to 125049959, which is a lot of sectors! You can dump the dd/hexdump output to a file and then search it for instances of the 55 AA magic number, hopefully there will only be one sector ending with this.


If a valid EBR is found then you just need to fix the MBR partition table to point to it. Then, hopefully, the whole thing will spring back to life.

---

### Post by mastergaurav on 2011-08-29
> **YesWeCan said:**
> If you find it please post it.

Yikes! That's gonna be a huge task...
Wondering if there's an easy alternate to manual scanning :)

---

### Post by YesWeCan on 2011-08-29
I think your disk layout is something like this:
```
**record   label           start        end       size**
MBR                          0          0          1
sda1     Dell Utility       63     176714     176652
sda2     Recovery       178176   20899839   20721664
sda3     C:           20899840  125033894  104134055
sda4     ext'd               ?  976773167          ?
EBR-1                        ?          ?          1
sda5     D:          125049960  208925312   83875353
EBR-2    
sda6     PERSONAL   
EBR-3    
sda7     OFFICIAL   
etc...    

```The trouble seems to be that the entry in the MBR partition table for sda4 (extended) is not pointing to the EBR-1. The sda4 entry needs the sector address of EBR-1 as its start and the end of the disk as its end (to be safe).

---

### Post by YesWeCan on 2011-08-29
> **mastergaurav said:**
> Yikes! That's gonna be a huge task...
Wondering if there's an easy alternate to manual scanning :)
No one said it would be easy. ;)
There probably is an automated tool for this somewhere.
But it may not be too onerous to dd into a file and open with gedit and search for the magic number. There may be a lot of false positives.
sudo dd if=/dev/sda bs=512 count=16066 skip=125033895 | hexdump -C > temp

---

### Post by mastergaurav on 2011-08-29
> **YesWeCan said:**
> false positives.

Scares me. :D

The "safest" solution that I'm trying out (since EBR is all gone) is:

[LIST=1]
[*]Backup all data: using testdata
[*]Try ntfsfix. If it works - awesome!
[*]If (2) fails, reinstall Ubuntu. Since Windows partitions are intact, I hope to recover Windows directly and restore the data.
[/LIST]

3(a). If Windows recovery fails, I hope to recover using Dell recovery DVDs and then reinstall everything.
    Good part: File system will be cleaner and Windows faster ;)
3(b). If Dell Recovery fails... dump the machine. :P


-Gaurav

---

### Post by Quackers on 2011-08-29
I'm not sure what caused this, or even whether Fixparts can fix it, but it may be worth looking at.
If you try it, make sure you download Fixparts and not gdisk or sgdisk, or anything else :-)

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by srs5694 on 2011-08-29
> **Quackers said:**
> I'm not sure what caused this, or even whether Fixparts can fix it, but it may be worth looking at.
If you try it, make sure you download Fixparts and not gdisk or sgdisk, or anything else :-)

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

I doubt if FixParts would do anything very useful in this situation, although trying it and aborting if it doesn't find anything won't hurt. Chances are it will throw away /dev/sda5, since its size as reported by fdisk is much bigger than the disk itself. (FixParts and fdisk read the same disk data to determine partition sizes, so FixParts will probably see the partition as the same size reported by fdisk.)

Chances are TestDisk can recover the damaged partition(s); however, the output posted in post #1 shows several options, and I can't say which one is correct. You could try each one in turn and see if it works. This poses a risk, though: If a partition is created as a logical partition, it will have an associated EBR, which could end up overwriting critical data if the initial guess is wrong. Thus, I'd only recommend trying this by creating the test partitions as primary partitions rather than as logical partitions. I'm not sure if TestDisk enables you to specify whether the partitions it recovers are created as primaries or as logicals. If you get something that works and then want to make it a logical partition, you should be able to convert it using FixParts (or with sfdisk or fdisk, with some extra work).

IIRC GParted has a partition recovery option. It might work better, but you'll probably have to delete the current bogus /dev/sda5 using fdisk, sfdisk, FixParts, or some other utility before GParted will be usable. (GParted generally shows a disk as being completely empty if it's got any partition table irregularities, so you need to use something else to overcome this initial problem.)

There may be some other automated or semi-automated utility that will do the job, but if so I don't know what it is. The only other way forward is to do the sort of low-level editing that YesWeCan is suggesting. This can be effective if you know what you're doing or have sufficient help from somebody who does, but if you do it wrong you can end up causing more problems.

Before doing anything else, save a copy of the "sfdisk -d" output you posted earlier on a USB flash drive, optical disc, or whatever. That will enable you to recover your current partitions (minus /dev/sda5, which is bogus) should your recovery attempts make things worse.

---

### Post by mastergaurav on 2011-08-30
The good news is that ntfsfix did great job in restoring the partitions!

But for me, I did something crazy post ntfsfix causing the OS partition (Windows) reset its signature and initial sectors... the result being that the OS partition shows no files - even by testdisk.

So, now I am a happy man.

1. Got all my data backup done
2. Tried "Dell Recovery" but it always got stuck at 43% while "formatting" - at least thrice. So, not too keen on using it now.
3. Will now have only and only Ubuntu on my machine ;)



Happy Hacking,
Gaurav
[www.mastergaurav.com](www.mastergaurav.com)

---

