---
title: "after installing ubuntu 7.10 with windows xp sp2 disk geometry proble"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by kai111 on 2008-03-12
hi there,

I have a preconfigured windows xp running on my thinkpad r60 and now I am trying to install Ubuntu 7.10 as a second operating system. It works fine, with one problem: there are disk geometry issues coming up.

There does not seem to be any effect on the operation of the software, but i would like to fix it anyway as I thought that maybe when the partition gets filled up with data there might be problems at the partition boundaries.

When I check the disk with testdisk it says the following:


[COLOR="Sienna"]Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 1 * HPFS - NTFS              0   1  1  2464 239 63   39599217 [Preload]
 2 P Linux                 2464 240  1  3739  74 63   20472480
 3 E extended LBA          3739  75 63  7295 254 63   57138418
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 5 L HPFS - NTFS           3739  76  1  6671  14 63   47098737
   X extended              6671  15  1  7295 254 63   10039680
 6 L Linux Swap            6671  16  1  7295 254 63   10039617

[/COLOR]

i fiddled around with the heads and googled for about a week, but i can;t find anything which solves the problem.

The problem only occurs after I have installed ubuntu.

Could someone help me?

Thank you so much!!


Kai

---

### Post by prshah on 2008-03-12
> **kai111 said:**
> hi there,

[COLOR="Sienna"]Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 1 * HPFS - NTFS              0   1  1  2464 239 63   39599217 [Preload]
 2 P Linux                 2464 240  1  3739  74 63   20472480
 3 E extended LBA          3739  75 63  7295 254 63   57138418
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 5 L HPFS - NTFS           3739  76  1  6671  14 63   47098737
   X extended              6671  15  1  7295 254 63   10039680
 6 L Linux Swap            6671  16  1  7295 254 63   10039617

[/COLOR]

Kai

I havent heard of testdisk, but what I see of your partition strikes me as unusual if not impossible. You seem to have TWO extended partitions.

If you can do ```
sudo fdisk /dev/sda
``` then "p" to print the partition table, copy and paste the output here. Then press "q" to quit: NOTHING ELSE! I can confirm if that is the case.

If you indeed have two extended partitions then you have nothing to worry about, albiet it will be an unusual configuration.

Or you can post a screen shot of "gparted" the Gnome Partition Editor

Cheers,
PRShah

---

### Post by kai111 on 2008-03-12
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2465    19799608+   7  HPFS/NTFS
/dev/sda2            2465        3740    10236240   83  Linux
/dev/sda3            3740        7296    28569209    f  W95 Ext'd (LBA)
/dev/sda5            3740        6672    23549368+   7  HPFS/NTFS
/dev/sda6            6672        7296     5019808+  82  Linux swap / Solaris


here is the screenshot

---

### Post by kai111 on 2008-03-12
i attached the gparted screenshot here

---

### Post by wjlroe on 2008-03-12
Hi,

I'm having probs with disk geometry too. After installing Ubuntu, setting up empty partitions for windows, when ubuntu finished installing it told me windows wouldn't work with those partitions due to cylinder size or something like that. It told me this after letting me create those partitions specifically for Windows. Crazy. 

Anyway, testdisk shows this for me:

```

TestDisk 6.6, Data Recovery Utility, February 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 249 GB / 232 GiB - CHS 30394 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1     4 254 63      80262 [DellUtility]
P FAT32 LBA                5   0  1  4182 254 63   67119570 [NO NAME]
L Linux                11315   1  1 16198 254 63   78461397
L Linux                16199   1  1 16217 254 63     305172
L Linux Swap           16218   1  1 16478 254 63    4192902
L Linux                16479   1  1 30393 254 63  223544412

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT32, 34 GB / 32 GiB

```
And gparted shows what is attached in the screenshot, different strangely...

---

### Post by kai111 on 2008-03-12
yes, this disk geometry problem is really anoying. I am actually not sure if it is caused by linux or if windows just didn't recognize it before. I reinstalled windows about 4 times now, tried to preformat the drive with partition magic to set up the linux primary and swap partitions.

Same result: partition doesn't end on cylinder boundary and partition magic says: chs and lba are different

Kai

Maybe windows and linux just don't like each other

---

### Post by prshah on 2008-03-12
> **kai111 said:**
> Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2465    19799608+   7  HPFS/NTFS
/dev/sda2            2465        3740    10236240   83  Linux
/dev/sda3            3740        7296    28569209    f  W95 Ext'd (LBA)
/dev/sda5            3740        6672    23549368+   7  HPFS/NTFS
/dev/sda6            6672        7296     5019808+  82  Linux swap / Solaris


here is the screenshot

Nope your gparted shot looks OK.. BUT...

> 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc101c101

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551        3645     8795587+  83  Linux
/dev/sda3            3646        4740     8795587+  83  Linux
/dev/sda4            4741        4865     1004062+  82  Linux swap / Solaris



Here's my fdisk and heres what I see, my start and end blocks are off by 1, but yours are the same... eg

yours:> 
/dev/sda1   *           1        [COLOR="Red"]2465[/COLOR]    19799608+   7  HPFS/NTFS
/dev/sda2            [COLOR="Red"]2465[/COLOR]        3740    10236240   83  Linux


mine:> 
/dev/sda1   *           1        [COLOR="Red"]2550[/COLOR]    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            [COLOR="Red"]2551[/COLOR]        3645     8795587+  83  Linux


Do you think this is significant?

Cheers,
PRShah

---

### Post by kai111 on 2008-03-12
right, i am going to try delete every partition apart from the c: windows partition and reinstall ubuntu. Then i'll post the partition table again.

Lets see,

Kai

---

### Post by wjlroe on 2008-03-12
Mmm, my start/end sectors for the NTFS partitions are likewise strange:

```

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        [COLOR="Sienna"]1311[/COLOR]    10485760    7  HPFS/NTFS
/dev/sda3           [COLOR="Sienna"] 1311[/COLOR]       11315    80360448    7  HPFS/NTFS
/dev/sda4           11316       30394   153252067+   5  Extended
/dev/sda5           11316       16199    39230698+  83  Linux
/dev/sda6   *       16200       16218      152586   83  Linux
/dev/sda7           16219       16479     2096451   82  Linux swap / Solaris
/dev/sda8           16480       30394   111772206   83  Linux

```
but the rest are fine. Very strange. Maybe I'll just get rid of them and re-create them...

---

### Post by kai111 on 2008-03-12
hi,

so, i reinstalled ubuntu and deleted every partition apart from the windows partition.

I also checked the windows partition with testdisk before installing ubuntu. It already said that there are 240 heads instead of 255. 

Now the new Ubuntu partition has 255 and the old windows one 240


Kai

---

### Post by kai111 on 2008-03-12
Disk /dev/sda - 60 GB / 55 GiB - CHS 7296 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 1 P HPFS - NTFS              0   1  1  2464 239 63   39599217 [Preload]
 2 * Linux                 2465   0  1  7091 254 63   74332755
 3 E extended              7092   0  1  7295 254 63    3277260
 5 L Linux Swap            7092   1  1  7295 254 63    3277197


new screenshot testdisk

---

### Post by kai111 on 2008-03-12
new development: if I set the head size to 240 in the geometry option of testdisk it displays the following:

[COLOR="Sienna"]Disk /dev/sda - 60 GB / 55 GiB - CHS 7752 240 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P HPFS - NTFS              0   1  1  2618 239 63   39599217 [Preload]

Warning: Bad ending head (CHS and LBA don't match)
 2 * Linux                 2619  15  1  7535  59 63   74332755

Warning: Bad starting head (CHS and LBA don't match)
 3 E extended              7535  60  1  7751 239 63    3277260

Warning: Bad starting head (CHS and LBA don't match)
 5 L Linux Swap            7535  61  1  7751 239 63    3277197

Warning: Bad starting head (CHS and LBA don't match)


*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Proceed ]  [ Backup ]
                            Try to locate partition

[/COLOR]


Now the windows partition is fine but all the linux partitions have a chs lba missmatch

---

