---
title: "Need Help With installation and partition"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by Blue-Fox on 2010-10-13
Need some help. I have a dual boot laptop with xp and ubuntu 10.04.
Had a system crash on ubuntu 10.04 and reinstalled the os now I have two versions of 10.04

How can I  safely  repartition

see  screen shot

---

### Post by kansasnoob on 2010-10-13
Please post the output of:

```
sudo parted /dev/sda print
```

---

### Post by dhysk on 2010-10-13
If you're not trying to keep data looks like you can repartition everything under the extended section and reinstall.  Other wise you have to figure out witch partition has the working Ubuntu probably the second one...

---

### Post by ender4 on 2010-10-13
I don't know if there is such a thing as a safe repartition.  If there is anything you don't want to lose, I suggest you back it up.

That said, there are some GUI's that allow you to  repartion your hard drive, the most popular being GParted which is available in the Software Center.  

The following has some instructions on how to partition using GParted: [https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by Blue-Fox on 2010-10-13
I got the drive partitioned however now my windows xp hangs when trying to boot. 

Get a blue screen that says something about need to check disk for consistency.

 It runs a series of three test then  hangs and just sits there on the blue screen.

It must have something to do with the boot loader but I don't know what. 

Any help is greatly appreciated.

---

### Post by oldfred on 2010-10-13
Its nothing to do with boot loader, but with inconsistencies in the partition.

Part of testdisk which is in the repositories or most recovery CDs. 

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Run chkdsk several times, until no more errors are detected.
Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by Blue-Fox on 2010-10-13
Here is the first analysis of TestDisk

Doing the second analysis now

If you see anything wrong please let me know


TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1 10777 174 13  173143417 [Local Disk]
P Linux                19461  41 37 38548 172 24  306640896
P Linux Swap           38548 172 25 38913  69 52    5857264


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 88 GB / 82 GiB

---

### Post by Blue-Fox on 2010-10-13
Here is the complete information
I am not sure how to read the results
I did try to install ubuntu several times, however there are only four primary partitions and one of them is unallocated space



TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1 10777 174 13  173143417 [Local Disk]
P Linux                19461  41 37 38548 172 24  306640896
P Linux Swap           38548 172 25 38913  69 52    5857264


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 88 GB / 82 GiB




@@@@@@@@@@@@@@@@@@@@@@@@@@


TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63

The harddisk (320 GB / 298 GiB) seems too small! (< 396 GB / 369 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                33476  41 38 42673 156 43  147757056
  Linux                33477  79 11 42674 194 16  147757056
  Linux                33477 209 13 42675  69 18  147757056
  Linux                33478 246 49 42676 106 54  147757056
  Linux                33479 219 21 42677  79 26  147757056
  Linux                33480  94 23 42677 209 28  147757056
  Linux                33482   6 61 42679 122  3  147757056
  Linux                33482  39 30 42679 154 35  147757056
  Linux                33482 104 31 42679 219 36  147757056
  Linux                33482 136 63 42679 252  5  147757056

[ Continue ]
EXT4 Large file Sparse superblock Recover, 75 GB / 70 GiB


@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1 10777 174 13  173143417 [Local Disk]
D HPFS - NTFS              0   1  1 19121 254 63  307194867 [Local Disk]
D Linux                19461  41 37 38548 172 24  306640896
D Linux                19473  69 53 38560 200 40  306640896
D Linux                29015 111 25 38212 226 30  147757056
D Linux Swap           38213   3 63 38562 243  1    5621744
D Linux Swap           38548 172 25 38913  69 52    5857264
D Linux Swap           38560 200 41 38913  69 52    5662704
D Linux Swap           38563  85 51 38913  69 52    5621744



Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 88 GB / 82 GiB

---

### Post by oldfred on 2010-10-13
That is listing the partitions. Since your issue is more with the NTFS partition, not recovering deleted partitions what does further checks of the MFT of the NTFS show.

Did you ever get chkdsk to complete without error?

---

### Post by Blue-Fox on 2010-10-13
Thanks Oldfred helping me

I never did get xp to boot so i could not run chkdsk other than when it first tries to boot. 

The only way that I can get out of the chkdsk  blue screen is to shut the power off manually. 

This morning I had everything working both xp and ubuntu were doing just fine. I was surfing the web   and  my computer locked up. I had to turn off the power. Things have never been the same since then.

Not sure how to do further checks of the MFT of the NTFS but will try and figure it out.

---

### Post by oldfred on 2010-10-14
chkdsk can take a long time, like hours if the drive is large or has many errors. I might just leave it over night.

---

### Post by Blue-Fox on 2010-10-14
here are some more reports 
scroll down to see the newer ones



TestDisk

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1 10777 174 13  173143417 [Local Disk]
P Linux                19461  41 37 38548 172 24  306640896
P Linux Swap           38548 172 25 38913  69 52    5857264


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 88 GB / 82 GiB




@@@@@@@@@@@@@@@@@@@@@@@@@@


TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63

The harddisk (320 GB / 298 GiB) seems too small! (< 396 GB / 369 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                33476  41 38 42673 156 43  147757056
  Linux                33477  79 11 42674 194 16  147757056
  Linux                33477 209 13 42675  69 18  147757056
  Linux                33478 246 49 42676 106 54  147757056
  Linux                33479 219 21 42677  79 26  147757056
  Linux                33480  94 23 42677 209 28  147757056
  Linux                33482   6 61 42679 122  3  147757056
  Linux                33482  39 30 42679 154 35  147757056
  Linux                33482 104 31 42679 219 36  147757056
  Linux                33482 136 63 42679 252  5  147757056

[ Continue ]
EXT4 Large file Sparse superblock Recover, 75 GB / 70 GiB


@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1 10777 174 13  173143417 [Local Disk]
D HPFS - NTFS              0   1  1 19121 254 63  307194867 [Local Disk]
D Linux                19461  41 37 38548 172 24  306640896
D Linux                19473  69 53 38560 200 40  306640896
D Linux                29015 111 25 38212 226 30  147757056
D Linux Swap           38213   3 63 38562 243  1    5621744
D Linux Swap           38548 172 25 38913  69 52    5857264
D Linux Swap           38560 200 41 38913  69 52    5662704
D Linux Swap           38563  85 51 38913  69 52    5621744



Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 88 GB / 82 GiB


@@@@@@@@@@@@@@@@@@@@@@@@@

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 10777 174 25  173143429 [Local Disk]

Boot sector
Status: OK

Backup boot sector
Status: Bad

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

@@@@@@@@@@@@@@@@@@@@@@@@@@@@

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 10777 174 25  173143429 [Local Disk]

filesystem size           173143429 173143417
sectors_per_cluster       8 8
mft_lcn                   786432 786432
mftmirr_lcn               19199679 19199679
clusters_per_mft_record   -10 -10
clusters_per_index_record 1 1
Extrapolated boot sector and current boot sector are different.







[  Dump  ]  [  List  ]  [ Write  ]  [  Quit  ]
                               Quit this section

@@@@@@@@@@@@@@@@@@@@@@@@@@

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
 1 * HPFS - NTFS              0   1  1 10777 174 25  173143429 [Local Disk]
     Rebuild Boot sector           Boot sector
0000 eb52904e 54465320   .R.NTFS   eb52904e 54465320   .R.NTFS
0008 20202000 02080000      .....  20202000 02080000      .....
0010 00000000 00f80000   ........  00000000 00f80000   ........
0018 3f00ff00 3f000000   ?...?...  3f00ff00 3f000000   ?...?...
0020 00000000 80008000   ........  00000000 80008000   ........
0028 84f5510a 00000000   ..Q.....  78f5510a 00000000   x.Q.....
0030 00000c00 00000000   ........  00000c00 00000000   ........
0038 bff62401 00000000   ..$.....  bff62401 00000000   ..$.....
0040 f6000000 01000000   ........  f6000000 01000000   ........
0048 8d0abf10 20bf10d2   .... ...  8d0abf10 20bf10d2   .... ...
0050 00000000 fa33c08e   .....3..  00000000 fa33c08e   .....3..
0058 d0bc007c fbb8c007   ...|....  d0bc007c fbb8c007   ...|....
0060 8ed8e816 00b8000d   ........  8ed8e816 00b8000d   ........
0068 8ec033db c6060e00   ..3.....  8ec033db c6060e00   ..3.....
[Previous]  [  Next  ]  [  Quit  ]
                               Quit dump section





[  Quit  ]  [  List  ]  [Org. BS ]  [Rebuild BS]  [  Dump  ]
                      Copy boot sector over backup sector


@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
 1 * HPFS - NTFS              0   1  1 10777 174 25  173143429 [Local Disk]
     Rebuild Boot sector           Boot sector
0188 69736b20 72656164   isk read  69736b20 72656164   isk read
0190 20657272 6f72206f    error o  20657272 6f72206f    error o
0198 63637572 72656400   ccurred.  63637572 72656400   ccurred.
01A0 0d0a4e54 4c445220   ..NTLDR   0d0a4e54 4c445220   ..NTLDR
01A8 6973206d 69737369   is missi  6973206d 69737369   is missi
01B0 6e67000d 0a4e544c   ng...NTL  6e67000d 0a4e544c   ng...NTL
01B8 44522069 7320636f   DR is co  44522069 7320636f   DR is co
01C0 6d707265 73736564   mpressed  6d707265 73736564   mpressed
01C8 000d0a50 72657373   ...Press  000d0a50 72657373   ...Press
01D0 20437472 6c2b416c    Ctrl+Al  20437472 6c2b416c    Ctrl+Al
01D8 742b4465 6c20746f   t+Del to  742b4465 6c20746f   t+Del to
01E0 20726573 74617274    restart  20726573 74617274    restart
01E8 0d0a0000 00000000   ........  0d0a0000 00000000   ........
0068 8ec033db c6060e00   ..3.....  8ec033db c6060e00   ..3.....
[Previous]  [  Next  ]  [  Quit  ]

---

### Post by Blue-Fox on 2010-10-14
The text below  is exactly the error message i get with the blue screen.
It only takes a few minutes to complete these test.
Then it just sits there frozen.

 
[B][COLOR=Blue]Checking file system on C:
 
The type of file system is NTFS.
 
volume label is Local Disk.
 
 
One of your disk needs to be checked for consistency.
 
You may cancel the disk check, but it is strongly recommended that you 
continue.
 
Windows will now check the disk.
 
 
CHKDSK is verifying files (stage 1 of 3)
 
File verification completed.
 
CHKDSK is verifying indexes (stage 2 of 3)
 
Index verification completed.
 
CHKDSK is verifying security descriptors (stage 3 of 3)
 
100 percent completed.
 [/COLOR][/B]

---

### Post by dino99 on 2010-10-14
how to make installation:

[http://ubuntuforums.org/showpost.php?p=9971263&postcount=4](http://ubuntuforums.org/showpost.php?p=9971263&postcount=4)

---

### Post by Blue-Fox on 2010-10-19
I am not sure what to do to resolve the problem :confused:

---

### Post by Blue-Fox on 2010-10-19
I was able to fix the problem using testdisk and navigated to fixboot and that fixed the  problem 


Thank you all for your help!

---

