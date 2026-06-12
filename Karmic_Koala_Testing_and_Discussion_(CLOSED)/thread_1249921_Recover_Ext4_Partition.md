---
title: "Recover Ext4 Partition"
date: 2009-08-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Bill_ on 2009-08-25
Hi Guys,

Sorry if this is in the wrong part of the forum - please move it if it is.

Basically, I'm running karmic with the latest updates, and I have an ext4 partition that I can see, but I can't access, and I'm wondering if anyone has any suggestions.

It first happened when I was running jaunty - I had just created an ext4 partition on a new drive, and I started copying some stuff to it. Some of the stuff came from an ntfs drive, which I think had some corrupt files on it that I tried to copy over.

I could access the drive fine, but after I reset the computer, the whole ext4 partition appeared to be corrupt - gparted just saw it as an unknown filesystem type.

It was a little while ago now, but I think I could still see the partition with testdisk at this stage, but I couldn't recover anything from it using testdisk.

I think I ran fsck.ext4 -y /dev/sdc1 (that's where it's located) a few times, but it didn't seem to get anywhere.

I then decided to upgrade to karmic to see if that helped at all - surprisingly enough, gparted could see it perfectly, including things like the type of the partition, and how much of it was used.

I ran fsck.ext4 -y /dev/sdc1 a few more times, but after a while I realised that after a little while it was just restarting so I stopped doing that.

I've also tried running it with most of the alternative superblocks for the partition, but I haven't had any luck yet.

Here's the start of when I run fsck.ext4 ->

```
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext4: Group descriptors look bad... trying backup blocks...
One or more block group descriptor checksums are invalid.  Fix<y>?
```

then if I answer yes to them all (or use the -y flag), it goes down to this ->

```
Group descriptor 7452 checksum is invalid.  FIXED.
media contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Root inode is not a directory.  Clear<y>? yes
```

Then after a while it just restarts.

I don't know if it helps at all, but when I cancel the check, it says this:

```
media: ***** FILE SYSTEM WAS MODIFIED *****

media: ********** WARNING: Filesystem still has errors **********

fsck.ext4: Inode bitmap not loaded while setting block group checksum info
```

Also, when I try to mount the drive, I get this error:

```
mount: Stale NFS file handle
```

If I then run dmesg | tail, I get this:

```
[ 5511.973511] EXT4-fs (sdc1): get root inode failed
[ 5511.973523] EXT4-fs (sdc1): mount failed
```

I would love to be able to recover the actual partition and it's structure if that is still possible, but I'm open to any suggestions.

Thanks.

---

### Post by pulpo69 on 2009-08-26
i have a similar or the same problem here with my /home partition.
i don't know how to recover it.

---

### Post by danf_1979 on 2009-08-26
what does SMART say about the disks?

---

### Post by Bill_ on 2009-08-26
> **danf_1979 said:**
> what does SMART say about the disks?

I'm not entirely sure how to get a terminal output so I can paste it in here (smartctl just seems to list the actual specs of the particular disk), but using the Palimpsest Disk Utility in Applications -> System Tools, I ran a smart selftest and it said it passed.

---

### Post by dinxter on 2009-08-26
i would recommend letting fsck run through, it can restart at the beginning any number of times on particularly boggled filesystems. i'm afraid sometimes you just need to let the hooks do their work :*)

---

### Post by dabl on 2009-08-26
> **Bill_ said:**
> 

It first happened when I was running jaunty - I had just created an ext4 partition on a new drive, and I started copying some stuff to it. Some of the stuff came from an ntfs drive, which I think had some corrupt files on it that I tried to copy over.

...

I ran fsck.ext4 -y /dev/sdc1 a few more times, but after a while I realised that after a little while it was just restarting so I stopped doing that.


```
Group descriptor 7452 checksum is invalid.  FIXED.
media contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Root inode is not a directory.  Clear<y>? yes
```

Then after a while it just restarts.



The problems with this filesystem go way back, and involve "mystery files that might be corrupt" -- not a situation that is going to be tweaked to solve.

Why don't you boot a Live CD, mount the partition, and copy the KNOWN GOOD files and directories onto known good media, then use GParted, delete the bad boy partition, and make it new again, and reformat it?  Then you can copy the known good data onto it and probably everything will work fine.

---

### Post by Bill_ on 2009-08-26
> **dinxter said:**
> i would recommend letting fsck run through, it can restart at the beginning any number of times on particularly boggled filesystems. i'm afraid sometimes you just need to let the hooks do their work :*)

hmm sorry yeah I should've gone into more detail - when I said I ran fsck  and it eventually restarted, at one stage I left it running overnight and it still seemed to be back in the same spot (in all it would've been running for about 10 hours - I just assumed it would never finish)

---

### Post by Bill_ on 2009-08-26
> **dabl said:**
> The problems with this filesystem go way back, and involve "mystery files that might be corrupt" -- not a situation that is going to be tweaked to solve.

Why don't you boot a Live CD, mount the partition, and copy the KNOWN GOOD files and directories onto known good media, then use GParted, delete the bad boy partition, and make it new again, and reformat it?  Then you can copy the known good data onto it and probably everything will work fine.

I never thought about doing that - would that work though? wouldn't I just still be able to see the partition from the livecd in gparted, but still get the same errors when I tried to mount it?

---

### Post by Bill_ on 2009-08-26
I'll download a current .iso of karmic and try it anyway - thanks for the idea

---

### Post by dinxter on 2009-08-26
> **Bill_ said:**
> hmm sorry yeah I should've gone into more detail - when I said I ran fsck  and it eventually restarted, at one stage I left it running overnight and it still seemed to be back in the same spot (in all it would've been running for about 10 hours - I just assumed it would never finish)
yep, seems longer than i would have given it, it must be in  a very poor state

---

### Post by bacardiandwatermelon on 2009-08-26
I had the same sorta issue, Karmic fresh build on ext4 + restricted extras plus updates, gave me all sorts of permissions errors when starting to boot after a restart, I replicated it like 4 times, I got pissed off, formatted my drive as jfs and didn't have an issue since.

---

### Post by hansab on 2009-08-29
Hello!
Me lost my / partion ext4, its listed by fdisk but gparted say it is unknown filesystem. I hocked disk to other box, and now running testdisk but I think I could just tell its ext4 somehow.

```
sudo fdisk -l

Disk /dev/sda: 300,0 GB, 300090728448 byte
255 huvuden, 63 sektorer/spår, 36483 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x9e183fa8

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2           35876       36483     4883760   82  Linux växling / Solaris
/dev/sda3            6375       12453    48829567+   5  Utökad
/dev/sda4           12454       35875   188137215   83  Linux
/dev/sda5            6375       12453    48829536   83  Linux

Posterna i partitionstabellen är inte i diskordning

Disk /dev/sdb: 400,0 GB, 400088457216 byte
255 huvuden, 63 sektorer/spår, 48641 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x01d501d5

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1               2        6527    52420095    f  W95 Utökad (LBA)
/dev/sdb2   *        6528       23603   137161728    7  HPFS/NTFS
/dev/sdb3           23604       43974   163630057+  83  Linux
/dev/sdb4           43975       48641    37487677+  83  Linux
/dev/sdb5               2        5696    45745056   83  Linux
/dev/sdb6            5697        6387     5550426   83  Linux
/dev/sdb7            6388        6527     1124518+  82  Linux växling / Solaris

```sofar i got this from deep scan on testdisk

```


Sun Aug 30 01:26:46 2009
Command line: TestDisk

TestDisk 6.11.3, Data Recovery Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 2.6.28-15-generic (#49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009)
Compiler: GCC 4.3 - May  6 2009 14:40:08
ext2fs lib: 1.41.4, ntfs lib: 10:0:0, reiserfs lib: 0.3.1-rc8, ewf lib: 20080501
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       586114704 sectors
/dev/sda: user_max   586114704 sectors
/dev/sda: native_max 586114704 sectors
/dev/sdb: LBA, HPA, LBA48, DCO support
/dev/sdb: size       781422768 sectors
/dev/sdb: user_max   781422768 sectors
/dev/sdb: native_max 781422768 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 300 GB / 279 GiB - CHS 36483 255 63, sector size=512 - ATA Maxtor 6L300S0
Disk /dev/sdb - 400 GB / 372 GiB - CHS 48641 255 63, sector size=512 - ATA SAMSUNG HD401LJ

Partition table type (auto): Intel
Disk /dev/sdb - 400 GB / 372 GiB - ATA SAMSUNG HD401LJ
Partition table type: Intel

Analyse Disk /dev/sdb - 400 GB / 372 GiB - CHS 48641 255 63
Geometry from i386 MBR: head=255 sector=63
NTFS at 6527/21/23
check_part_i386 failed for partition type 83

ReiserFS Marker at 1/1/1
get_geometry_from_list_part_aux head=255 nbr=16
get_geometry_from_list_part_aux head=8 nbr=4
get_geometry_from_list_part_aux head=16 nbr=4
get_geometry_from_list_part_aux head=32 nbr=4
get_geometry_from_list_part_aux head=64 nbr=4
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=2
get_geometry_from_list_part_aux head=255 nbr=16
Current partition structure:
 1 E extended LBA             1   0  1  6526 254 63  104840190
 2 * HPFS - NTFS           6527  21 23 23602 236 58  274323456
No EXT2, JFS, Reiser, cramfs or XFS marker
 3 P Linux                23603   0  1 43973 254 63  327260115
 3 P Linux                23603   0  1 43973 254 63  327260115
 4 P Linux                43974   0  1 48640 254 63   74975355
 5 L Linux                    1   1  1  5695 254 63   91490112
   X extended              5696   0  1  6386 254 63   11100915
 6 L Linux                 5696   1  1  6386 254 63   11100852
   X extended              6387   0  1  6526 254 63    2249100
 7 L Linux Swap            6387   1  1  6526 254 63    2249037
Computes LBA from CHS for Disk /dev/sdb - 400 GB / 372 GiB - CHS 48642 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sdb - 400 GB / 372 GiB - CHS 48642 255 63
NTFS at 0/1/1
filesystem size           104856192
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               6553511
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  1  6526 254 63  104856192
     NTFS, 53 GB / 49 GiB

XFS Marker at 6527/0/1

recover_xfs
     Linux                 6527   0  1 23602 254 11  274325888 [lager]
     XFS 6.2+ - bitmap version, 140 GB / 130 GiB

recover_EXT2: s_block_group_nr=0/1248, s_mnt_count=13/39, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 40907514
recover_EXT2: part_size 327260112
     Linux                33803   0  1 54173 254 60  327260112
     EXT4 Large file Sparse superblock Recover, 167 GB / 156 GiB
This partition ends after the disk limits. (start=543045195, size=327260112, end=870305306, disk end=781433730)

recover_EXT2: s_block_group_nr=0/286, s_mnt_count=5/23, s_blocks_per_group=32768, s_inodes_per_group=8208
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 9371648
recover_EXT2: part_size 74973184
     Linux                43974   0  1 48640 220 34   74973184
     EXT3 Large file Sparse superblock Recover, 38 GB / 35 GiB
Disk /dev/sdb - 400 GB / 372 GiB - CHS 48642 255 63
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (400 GB / 372 GiB) seems too small! (< 445 GB / 414 GiB)
The following partition can't be recovered:
     Linux                33803   0  1 54173 254 60  327260112
     EXT4 Large file Sparse superblock Recover, 167 GB / 156 GiB
get_geometry_from_list_part_aux head=255 nbr=5
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=2
get_geometry_from_list_part_aux head=32 nbr=2
get_geometry_from_list_part_aux head=64 nbr=2
get_geometry_from_list_part_aux head=128 nbr=2
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=5

Results
   * HPFS - NTFS              0   1  1  6526 254 63  104856192
     NTFS, 53 GB / 49 GiB
   P Linux                 6527   0  1 23602 254 63  274325940 [lager]
     XFS 6.2+ - bitmap version, 140 GB / 130 GiB
   P Linux                43974   0  1 48640 254 63   74975355
     EXT3 Large file Sparse superblock Recover, 38 GB / 35 GiB


dir_partition inode=2
   P Linux                43974   0  1 48640 254 63   74975355
     EXT3 Large file Sparse superblock Recover, 38 GB / 35 GiB
Directory /
       2 drwxr-xr-x     0      0      4096 22-Jan-2009 04:31 .
       2 drwxr-xr-x     0      0      4096 22-Jan-2009 04:31 ..
      11 drwx------     0      0     16384 22-Jan-2009 03:03 lost+found
  467857 drwxr-xr-x     0      0      4096 29-Oct-2008 22:28 var
  870049 drwxr-xr-x     0      0     12288 15-May-2009 00:49 etc
 1731889 drwxr-xr-x     0      0      4096 15-May-2009 00:35 media
      12 lrwxrwxrwx     0      0        11 22-Jan-2009 03:04 cdrom
  517105 drwxr-xr-x     0      0      4096 22-Jan-2009 04:27 bin
  328321 drwxr-xr-x     0      0      4096 22-Jan-2009 04:32 boot
 1567729 drwxr-xr-x     0      0      4096 29-Oct-2008 22:18 dev
 1337905 drwxr-xr-x     0      0      4096 22-Jan-2009 03:09 home
 1723681 drwxr-xr-x     0      0      4096 22-Jan-2009 04:26 lib
      13 lrwxrwxrwx     0      0         4 22-Jan-2009 03:04 lib64
 1937089 drwxr-xr-x     0      0      4096 20-Oct-2008 14:27 mnt
 2027377 drwxr-xr-x     0      0      4096 29-Oct-2008 22:04 opt
  894673 drwxr-xr-x     0      0      4096 20-Oct-2008 14:27 proc
  993169 drwxr-xr-x     0      0      4096 22-Jan-2009 04:25 root
  270865 drwxr-xr-x     0      0      4096 22-Jan-2009 04:27 sbin
  648433 drwxr-xr-x     0      0      4096 29-Oct-2008 22:04 srv
 1477441 drwxr-xr-x     0      0      4096 14-Oct-2008 15:02 sys
  960337 drwxrwxrwt     0      0      4096 15-May-2009 00:49 tmp
  558145 drwxr-xr-x     0      0      4096 22-Jan-2009 04:45 usr
      17 lrwxrwxrwx     0      0        29 22-Jan-2009 04:31 vmlinuz
      16 lrwxrwxrwx     0      0        32 22-Jan-2009 04:31 initrd.img
X     14 lrwxrwxrwx     0      0        29 22-Jan-2009 03:10 vmlinuz.23080
      15 lrwxrwxrwx     0      0        32 22-Jan-2009 03:10 initrd.img.old
      14 lrwxrwxrwx     0      0        29 22-Jan-2009 03:10 vmlinuz.old

dir_partition inode=1337905
   P Linux                43974   0  1 48640 254 63   74975355
     EXT3 Large file Sparse superblock Recover, 38 GB / 35 GiB
Directory /home
 1337905 drwxr-xr-x     0      0      4096 22-Jan-2009 03:09 .
       2 drwxr-xr-x     0      0      4096 22-Jan-2009 04:31 ..
 1337907 drwxr-xr-x  1000   1000      4096 15-May-2009 00:49 xerox

dir_partition inode=1337907
   P Linux                43974   0  1 48640 254 63   74975355
     EXT3 Large file Sparse superblock Recover, 38 GB / 35 GiB
Directory /home/xerox
 1337907 drwxr-xr-x  1000   1000      4096 15-May-2009 00:49 .
 1337905 drwxr-xr-x     0      0      4096 22-Jan-2009 03:09 ..
 1337908 -rw-r--r--  1000   1000       220 22-Jan-2009 03:09 .bash_logout
 1337909 -rw-r--r--  1000   1000      3115 22-Jan-2009 03:09 .bashrc
 1337910 lrwxrwxrwx  1000   1000        26 22-Jan-2009 03:09 Examples
 1337911 -rw-r--r--  1000   1000       675 22-Jan-2009 03:09 .profile
X1338336 -rw-------  1000   1000         0 15-May-2009 00:49 .Xauthority
 1337913 -rw-r--r--  1000   1000      3056 15-May-2009 00:49 .xsession-errors
 1338341 -rw-------  1000   1000         2 15-May-2009 00:16 .dmrc
 1337914 drwxr-xr-x  1000   1000      4096 15-May-2009 00:34 Skrivbord
 1337916 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:23 Mallar
 1337917 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:23 Publikt
 1337918 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:23 Dokument
 1337919 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:23 Musik
 1337920 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:23 Bilder
 1337921 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:23 Video
 1337922 drwxr-xr-x  1000   1000      4096 15-May-2009 00:33 .config
 1337925 drwx------  1000   1000      4096 22-Jan-2009 04:23 .dbus
 1337928 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:24 .pulse
 1337929 -rw-------  1000   1000        16 22-Jan-2009 04:23 .esd_auth
 1337930 -rw-------  1000   1000       256 22-Jan-2009 04:23 .pulse-cookie
 1337931 drwx------  1000   1000      4096 15-May-2009 00:30 .gconf
 1337932 drwx------  1000   1000      4096 15-May-2009 00:49 .gconfd
 1337934 drwx------  1000   1000      4096 22-Jan-2009 04:23 .gnupg
 1337936 drwx------  1000   1000      4096 15-May-2009 00:49 .gnome2
 1337939 drwx------  1000   1000      4096 22-Jan-2009 04:23 .gnome2_private
 1337937 -rw-------  1000   1000       612 15-May-2009 00:16 .ICEauthority
 1337948 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:27 .fontconfig
 1337950 drwxr-xr-x  1000   1000      4096 15-May-2009 00:49 .nautilus
 1337952 drwx------  1000   1000      4096 22-Jan-2009 04:23 .gvfs
 1337960 drwx------  1000   1000      4096 22-Jan-2009 04:24 .local
 1337969 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:24 .gstreamer-0.10
 1338031 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:24 .cache
 1338038 drwx------  1000   1000      4096 22-Jan-2009 04:24 .update-notifier
 1337949 -rw-r--r--  1000   1000       104 15-May-2009 00:17 .gtk-bookmarks
 1338044 -rw-r-----  1000   1000         0 15-May-2009 00:42 .gksu.lock
 1338051 -rw-r--r--  1000   1000         0 22-Jan-2009 04:24 .sudo_as_admin_successful
 1338058 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:25 .update-manager-core
 1338067 drwx------  1000   1000      4096 22-Jan-2009 04:32 .thumbnails
 1338134 drwx------  1000   1000      4096 22-Jan-2009 04:33 .mozilla
 1337990 -rw-------  1000   1000        26 22-Jan-2009 04:50 .bash_history
 1338143 -rw-------  1000   1000       751 22-Jan-2009 04:35 .recently-used.xbel
 1346415 drwx------  1000   1000      4096  8-Feb-2009 11:57 .compiz
X1338066 -rw-------  1000   1000        86 15-May-2009 00:49 .Xauthority-c
X1338066 -rw-------  1000   1000        86 15-May-2009 00:49 .Xauthority-l

dir_partition inode=1337918
   P Linux                43974   0  1 48640 254 63   74975355
     EXT3 Large file Sparse superblock Recover, 38 GB / 35 GiB
Directory /home/xerox/Dokument
 1337918 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:23 .
 1337907 drwxr-xr-x  1000   1000      4096 15-May-2009 00:49 ..
Directory /home/xerox
 1337907 drwxr-xr-x  1000   1000      4096 15-May-2009 00:49 .
 1337905 drwxr-xr-x     0      0      4096 22-Jan-2009 03:09 ..
 1337908 -rw-r--r--  1000   1000       220 22-Jan-2009 03:09 .bash_logout
 1337909 -rw-r--r--  1000   1000      3115 22-Jan-2009 03:09 .bashrc
 1337910 lrwxrwxrwx  1000   1000        26 22-Jan-2009 03:09 Examples
 1337911 -rw-r--r--  1000   1000       675 22-Jan-2009 03:09 .profile
X1338336 -rw-------  1000   1000         0 15-May-2009 00:49 .Xauthority
 1337913 -rw-r--r--  1000   1000      3056 15-May-2009 00:49 .xsession-errors
 1338341 -rw-------  1000   1000         2 15-May-2009 00:16 .dmrc
 1337914 drwxr-xr-x  1000   1000      4096 15-May-2009 00:34 Skrivbord
 1337916 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:23 Mallar
 1337917 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:23 Publikt
 1337918 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:23 Dokument
 1337919 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:23 Musik
 1337920 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:23 Bilder
 1337921 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:23 Video
 1337922 drwxr-xr-x  1000   1000      4096 15-May-2009 00:33 .config
 1337925 drwx------  1000   1000      4096 22-Jan-2009 04:23 .dbus
 1337928 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:24 .pulse
 1337929 -rw-------  1000   1000        16 22-Jan-2009 04:23 .esd_auth
 1337930 -rw-------  1000   1000       256 22-Jan-2009 04:23 .pulse-cookie
 1337931 drwx------  1000   1000      4096 15-May-2009 00:30 .gconf
 1337932 drwx------  1000   1000      4096 15-May-2009 00:49 .gconfd
 1337934 drwx------  1000   1000      4096 22-Jan-2009 04:23 .gnupg
 1337936 drwx------  1000   1000      4096 15-May-2009 00:49 .gnome2
 1337939 drwx------  1000   1000      4096 22-Jan-2009 04:23 .gnome2_private
 1337937 -rw-------  1000   1000       612 15-May-2009 00:16 .ICEauthority
 1337948 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:27 .fontconfig
 1337950 drwxr-xr-x  1000   1000      4096 15-May-2009 00:49 .nautilus
 1337952 drwx------  1000   1000      4096 22-Jan-2009 04:23 .gvfs
 1337960 drwx------  1000   1000      4096 22-Jan-2009 04:24 .local
 1337969 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:24 .gstreamer-0.10
 1338031 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:24 .cache
 1338038 drwx------  1000   1000      4096 22-Jan-2009 04:24 .update-notifier
 1337949 -rw-r--r--  1000   1000       104 15-May-2009 00:17 .gtk-bookmarks
 1338044 -rw-r-----  1000   1000         0 15-May-2009 00:42 .gksu.lock
 1338051 -rw-r--r--  1000   1000         0 22-Jan-2009 04:24 .sudo_as_admin_successful
 1338058 drwxr-xr-x  1000   1000      4096 22-Jan-2009 04:25 .update-manager-core
 1338067 drwx------  1000   1000      4096 22-Jan-2009 04:32 .thumbnails
 1338134 drwx------  1000   1000      4096 22-Jan-2009 04:33 .mozilla
 1337990 -rw-------  1000   1000        26 22-Jan-2009 04:50 .bash_history
 1338143 -rw-------  1000   1000       751 22-Jan-2009 04:35 .recently-used.xbel
 1346415 drwx------  1000   1000      4096  8-Feb-2009 11:57 .compiz
X1338066 -rw-------  1000   1000        86 15-May-2009 00:49 .Xauthority-c
X1338066 -rw-------  1000   1000        86 15-May-2009 00:49 .Xauthority-l
Directory /home
 1337905 drwxr-xr-x     0      0      4096 22-Jan-2009 03:09 .
       2 drwxr-xr-x     0      0      4096 22-Jan-2009 04:31 ..
 1337907 drwxr-xr-x  1000   1000      4096 15-May-2009 00:49 xerox
Directory /
       2 drwxr-xr-x     0      0      4096 22-Jan-2009 04:31 .
       2 drwxr-xr-x     0      0      4096 22-Jan-2009 04:31 ..
      11 drwx------     0      0     16384 22-Jan-2009 03:03 lost+found
  467857 drwxr-xr-x     0      0      4096 29-Oct-2008 22:28 var
  870049 drwxr-xr-x     0      0     12288 15-May-2009 00:49 etc
 1731889 drwxr-xr-x     0      0      4096 15-May-2009 00:35 media
      12 lrwxrwxrwx     0      0        11 22-Jan-2009 03:04 cdrom
  517105 drwxr-xr-x     0      0      4096 22-Jan-2009 04:27 bin
  328321 drwxr-xr-x     0      0      4096 22-Jan-2009 04:32 boot
 1567729 drwxr-xr-x     0      0      4096 29-Oct-2008 22:18 dev
 1337905 drwxr-xr-x     0      0      4096 22-Jan-2009 03:09 home
 1723681 drwxr-xr-x     0      0      4096 22-Jan-2009 04:26 lib
      13 lrwxrwxrwx     0      0         4 22-Jan-2009 03:04 lib64
 1937089 drwxr-xr-x     0      0      4096 20-Oct-2008 14:27 mnt
 2027377 drwxr-xr-x     0      0      4096 29-Oct-2008 22:04 opt
  894673 drwxr-xr-x     0      0      4096 20-Oct-2008 14:27 proc
  993169 drwxr-xr-x     0      0      4096 22-Jan-2009 04:25 root
  270865 drwxr-xr-x     0      0      4096 22-Jan-2009 04:27 sbin
  648433 drwxr-xr-x     0      0      4096 29-Oct-2008 22:04 srv
 1477441 drwxr-xr-x     0      0      4096 14-Oct-2008 15:02 sys
  960337 drwxrwxrwt     0      0      4096 15-May-2009 00:49 tmp
  558145 drwxr-xr-x     0      0      4096 22-Jan-2009 04:45 usr
      17 lrwxrwxrwx     0      0        29 22-Jan-2009 04:31 vmlinuz
      16 lrwxrwxrwx     0      0        32 22-Jan-2009 04:31 initrd.img
X     14 lrwxrwxrwx     0      0        29 22-Jan-2009 03:10 vmlinuz.23080
      15 lrwxrwxrwx     0      0        32 22-Jan-2009 03:10 initrd.img.old
      14 lrwxrwxrwx     0      0        29 22-Jan-2009 03:10 vmlinuz.old

interface_write()
 1 * HPFS - NTFS              0   1  1  6526 254 63  104856192
 2 P Linux                 6527   0  1 23602 254 63  274325940 [lager]
 3 P Linux                43974   0  1 48640 254 63   74975355

search_part()
Disk /dev/sdb - 400 GB / 372 GiB - CHS 48642 255 63
NTFS at 0/1/1
filesystem size           104856192
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               6553511
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  1  6526 254 63  104856192
     NTFS, 53 GB / 49 GiB

ReiserFS Marker at 1/1/1

recover_rfs
block_count=11436256
block_size=4096
     Linux                    1   1  1  5695 253 62   91490048
     ReiserFS 3.6 with standard journal, need recovery, 46 GB / 43 GiB

ReiserFS Marker at 2/2/1

recover_rfs
block_count=11436256
block_size=4096
     Linux                    2   2  1  5696 254 62   91490048
     ReiserFS 3.6 with standard journal, need recovery, 46 GB / 43 GiB

ReiserFS Marker at 2/140/11

recover_rfs
block_count=11436256
block_size=4096
     Linux                    2 140 11  5697 138  9   91490048
     ReiserFS 3.6 with standard journal, need recovery, 46 GB / 43 GiB

recover_EXT2: s_block_group_nr=0/42, s_mnt_count=28/30, s_blocks_per_group=32768, s_inodes_per_group=16160
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1387606
recover_EXT2: part_size 11100848
     Linux                 5696   1  1  6386 254 59   11100848
     EXT2 Sparse superblock, 5683 MB / 5420 MiB

block_group_nr 3

recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/42, s_mnt_count=12/30, s_blocks_per_group=32768, s_inodes_per_group=16160
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 1387606
recover_EXT2: part_size 11100848
     Linux                 5696   1  1  6386 254 59   11100848
     EXT2 Sparse superblock Backup superblock, 5683 MB / 5420 MiB
     Linux Swap            6387   1  1  6526 254 42    2249016
     SWAP2 version 1, 1151 MB / 1098 MiB
NTFS at 6526/254/63
filesystem size           104856192
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               6553511
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  1  6526 254 63  104856192
     NTFS found using backup sector!, 53 GB / 49 GiB

XFS Marker at 6527/0/1

recover_xfs
     Linux                 6527   0  1 23602 254 11  274325888 [lager]
     XFS 6.2+ - bitmap version, 140 GB / 130 GiB
NTFS at 6527/21/23
filesystem size           274323456
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               17145215
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS           6527  21 23 23602 236 58  274323456
     NTFS, 140 GB / 130 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=14/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                 6672 235 28  9168 234 26   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=14/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                 9281  20 20 11777  19 18   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB
NTFS at 11107/33/63
filesystem size           586067202
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               36629200
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          11107  33 63 47588  32 62  586067202
     NTFS, 300 GB / 279 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=14/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                15349  58  6 17845  57  4   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=14/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                15375  92 14 17871  91 12   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=2/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                16028 180 25 18524 179 23   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=2/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                16037 193 29 18533 192 27   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=2/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                16047 244  6 18543 243  4   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=2/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                16050 161 48 18546 160 46   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=2/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                17196  80 37 19692  79 35   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=14/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                17245 101  9 19741 100  7   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=2/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                17317 205 41 19813 204 39   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=14/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                17499 249 31 19995 248 29   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=14/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                17500  26 63 19996  25 61   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=22/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                17772 201 30 20268 200 28   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=21/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                17816   0  1 20311 253 62   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=20/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                18020 156 57 20516 155 55   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=14/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                18038  52 63 20534  51 61   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=21/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                18092   1 22 20588   0 20   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=14/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                18092  66 23 20588  65 21   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=14/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                18499 111 45 20995 110 43   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=2/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                18511 107 29 21007 106 27   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=2/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                18513 117 37 21009 116 35   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=2/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                18514 220 11 21010 219  9   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=19/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                18604 220 49 21100 219 47   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=14/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                18609  51  3 21105  50  1   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=22/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                18661 184 20 21157 183 18   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=22/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                18687 218 28 21183 217 26   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/152, s_mnt_count=22/23, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 5012272
recover_EXT2: part_size 40098176
     Linux                18692  16 13 21188  15 11   40098176
     EXT3 Large file Sparse superblock Recover, 20 GB / 19 GiB

recov 
```any help?

---

### Post by Bill_ on 2009-08-30
It turns out I actually got somewhere with my original problem.

I tried using the 'check' command in gparted for the filesystem, and I left that going for an hour or two, not really expecting anything to happen.

But, it actually completed the check, and to my surprise, I was actually able to mount the partition and browse it.

Unfortunately though, all the data that was on it, just appears as lots of numbered files in the lost+found folder - I'm guessing it's not possible, but does anyone know if there's any chance of recovering those files?

For anyone interested, using the terminal to browse to the lost+found folder, then running ls, gives me a list of all the files, with them all listed like this small selection from the end of the list:

#18320491  #30308600  #38415270  #45272672  #51530321  #57449083
#18320494  #30308601  #38415276  #45272680  #51530344  #57449085

I think the reason this sort of worked (in the sense that I've got a useable filesystem again, but lost all my data), is that gparted seemed to run the command e2fsck instead of fsck.ext4 which I was running from the command line.

---

### Post by Herman on 2009-08-30
A friend of mine, confused57, told me he used nautilus for copying files from the lost+found to another disk and recovered all of his files that way, from a live cd,
```
gksudo nautilus
``` Navigate to your lost+found and then just drag 'n drop.
Otherwise it might be quicker to do the same thing from the command line, I'm not sure. I won't know until it happens to me some day, I hope that won't be for a long time though.

I like the -p option in the e2fsck command, it repairs most file system problems and prints an 'exit code' message if it can't. I save the -y option for extreme circumstances.
Here's my favorite file system checking command,
```
e2fsck -C0 -p -f -v /dev/sdxy
```Regards, Herman :)

---

### Post by Bill_ on 2009-08-30
> **Herman said:**
> A friend of mine, confused57, told me he used nautilus for copying files from the lost+found to another disk and recovered all of his files that way, from a live cd,
```
gksudo nautilus
``` Navigate to your lost+found and then just drag 'n drop.
Otherwise it might be quicker to do the same thing from the command line, I'm not sure. I won't know until it happens to me some day, I hope that won't be for a long time though.

I like the -p option in the e2fsck command, it repairs most file system problems and prints an 'exit code' message if it can't. I save the -y option for extreme circumstances.
Here's my favorite file system checking command,
```
e2fsck -C0 -p -f -v /dev/sdxy
```Regards, Herman :)

Thanks Herman,

Yeah I originally started off using the -p option, but quickly gave up because it said it needed to be run without -a or -p, which then resulted in me having to press enter thousands of times until I realised that it could take forever without the -y option.

When I finally ended up partly fixing it using gparted anyway, by default it ran 'e2fsck -f -v -y /dev/sdxy'.

Thanks for the help with trying to recover those files, I'll try it one day soon and see how it goes.

---

### Post by Herman on 2009-08-30
:) Oh, okay then, in that case it sounds like it really needed the -y option then.

Have you tried out the cool new 'Disk Utility' in Karmic Koala yet? That and GSmartControl are interesting and useful programs for keeping an eye on our hard disks. :)

---

