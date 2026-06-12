---
title: "Restart error possibly due to generic upgrade"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by ayberkoktay on 2010-01-10
Hi everybody;

I firstly wanted to say thank you because allthought yhis is my first time writing in the forum. I had read alot befor. Thanks for the share of knowledge.

I have been using ubuntu for nearly a year. I have been using the 9.10 release untill this morning. Yesturday there was a update ( &#305; think generic ... .17) and &#305; donwloaded it. After a hour I went to bed without a restart.
This morning I tried to open my pc and there was no responce. I saw the ubuntu sign and after that total darkness for minutes.

I tried every thig I could ( which is not much because I am a newbee ) I tried reaching my files( some very important files) by live cd( ubuntu) &#305; couldnt. I could see my windows partition but not ubuntu. I tried slax live cd. I got an error like this
------------------------------------------------------------------------

Type. Unmounted hard Disk Volume

Location: unmounted hard disk volume

    /media (system)

    mount: wrong fs type, bad option, bad superblock on /dev/sda5,
    missing codepage or helper program, or other error
Size:     In some cases useful info is found in syslog - try
     dmesg | tail or so 

-------------------------------------------------------------------------

I dont know what to do
I really want reach those files


I should remind you that I am not a gen&#305;ous on linux and even the simple stuff on terminal am not very good.

I would apprec&#305;ate &#305;f you g&#305;ve me some help:(

---

### Post by tachuela on 2010-01-10
Boot your Live CD; go to the Terminal and post:
```
sudo fdisk -lu
```

---

### Post by ayberkoktay on 2010-01-14
[COLOR=Green]thanks for your reply &#305; d&#305;d 

fdisk -lu

This  &#305;s the result[/COLOR]
-----------------------------
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9474ad7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    52789589    26394763+   7  HPFS/NTFS

Disk /dev/sdb: 2034 MB, 2034237440 bytes
63 heads, 62 sectors/track, 1017 cylinders, total 3973120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005de30

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     3972401     1986170    c  W95 FAT32 (LBA)
[COLOR=Green]
----------------------------

&#305; also tr&#305;ed test d&#305;sk &#305;t found the dr&#305;ve but &#305; th&#305;nk

&#305; got th&#305;s
-----------------------------[/COLOR]
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  3285 254 63   52789527
 2 E extended LBA          3286   0  1 19456 254 63  259787115
 5 L Linux                 3286   1  1 18794 254 63  249152022
 6 L Linux Swap           18795   1  1 19456 254 63   10634967
---------------------
[COLOR=Green]&#305; d&#305;d deeper search on test d&#305;sk &#305; got th&#305;s[/COLOR]
--------------------
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63

The harddisk (160 GB / 149 GiB) seems too small! (< 3902167 TB / 3549000 TiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
  HFS                   7400   0  1 1965064465  54 39  632127066

------------------------------
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  3285 254 49   52789513
D HPFS - NTFS              0   1  1 19455 254 63  312560577
D HPFS - NTFS              0   1 15  3285 254 63   52789513
D HPFS - NTFS             12 223 20 19457  21 20  312371200
D Linux                 3286   1  1 18794 254 57  249152016
D Linux Swap           18795   1  1 19456 254 40   10634944


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT3 Large file Sparse [COLOR=Red]_superblock, 127 GB / 118 GiB_[/COLOR]

[COLOR=Green]what should &#305; do now??[/COLOR]

---

