---
title: "Need to restore id=83 linux partition, after vista deletion"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by CountMist on 2010-07-20
I deleted my Vista Partition, but it seems like it deleted my entire linux partition along with it.  All that is left now is the linux swap.  Both the id=83 ootreclinux partition and the ext3 are gone.

I have tried..
> 
sudo grub
find /boot/grub/stage1
Error 15: File not found
I have also tried using Super Grub options
most return the same Error 15

I have also tried booting into a windows CD and used the auto repair and command prompt
> 
Bootrec.exe /FixMbr
it returns successful, but the problem got worse from there.  I used to be able to see the Grub Error 22 at startup.  Now it just exits intel start up all together.

I have also tried the other Bootrec.exe options( Fixboot, ScanOs...) 

And I did not use Wubi, ubuntu 9.04 was installed on a separate partition.

So I want to restore my linux partitions.  Any Idea on what I can do?  

Restoring a deleted partition by creating an exact size partition is also an option.  Any suggestion on that?

Thanks in advance.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
240 heads, 63 sectors/track, 64601 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcc0cd81e

Partition  Boot         Start           End          Size  Id System

/dev/sda1         419,432,448   557,424,639   137,992,192   7 HPFS/NTFS
/dev/sda2    *    557,424,640   804,886,527   247,461,888   7 HPFS/NTFS
/dev/sda3         804,888,630   976,768,064   171,879,435   5 Extended
/dev/sda5         969,683,463   976,768,064     7,084,602  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D860DD0E60DCF3EA                       ntfs                                     
/dev/sda2        6CD2748FD2745F70                       ntfs       Windows 7                     
/dev/sda5        9cb3b823-2fbd-40e2-94f0-3ad8d8c8906b   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

---

### Post by bcbc on 2010-07-20
Try testdisk. It's pretty good at finding partitions. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

You can install it in a live cd environment (universe repository required). ```
sudo apt-get install testdisk
sudo testdisk
```

Once you've recovered your partition, you can reinstall grub. Assuming it's /dev/sda5
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```

---

### Post by CountMist on 2010-07-20
Thanks. I used TestDisk and it seems to be see my partitions again :).

```



ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69a12ce6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26109   209715200    7  HPFS/NTFS
/dev/sda2           26109       34699    68996096    7  HPFS/NTFS
/dev/sda3           34699       50102   123730944    7  HPFS/NTFS
/dev/sda4           50103       60802    85947750    f  W95 Ext'd (LBA)
/dev/sda5           50103       60360    82397352   83  Linux
/dev/sda6           60361       60801     3542292   82  Linux swap / Solaris


```but i'm getting this error

```

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by bcbc on 2010-07-20
that doesn't sound good. I'd start by running fsck on it. see if that helps.

Before doing that you might want to consider whether there is data on there you don't want to lose. It might be better to make a backup image or attempt to recover the data prior to anything else.

---

### Post by CountMist on 2010-07-20
crap....i did this already

```

ubuntu@ubuntu:~$ sudo e2fsck -f /dev/sda5
e2fsck 1.41.4 (27-Jan-2009)
Superblock has an invalid journal (inode 8).
Clear<y>? yes

*** ext3 journal has been deleted - filesystem is now ext2 only ***


```is it too late for me to do

```

dd if=/dev/sda5 of=/media/disk/backup-sda5.img

```I have space on 'disk'

---

### Post by bcbc on 2010-07-20
> **CountMist said:**
> is it too late for me to do

```

dd if=/dev/sda5 of=/media/disk/backup-sda5.img

```I have space on 'disk'

I honestly can't say one way or the other at this point (i.e. I don't know). I'd be inclined to see if it mounts and whether the data is intact. If the data was crucial I might take a more conservative approach.

---

