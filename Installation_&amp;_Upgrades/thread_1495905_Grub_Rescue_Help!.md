---
title: "Grub Rescue Help!"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by goseph on 2010-05-28
Hi everybody!

I installed Ubuntu 10.04 alongside windows XP on my eeePC. all was fine until I resized the Ubuntu partition in order to increase SWAP to 3GB. (I have 2 GB of RAM)

Now when I switch on the computer I just get a[B] Grub-Rescue>

**H**ow can I rescue my system?
[/B]

---

### Post by goseph on 2010-05-28
Running the Boot Info script [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Gives this:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   151,123,454   151,123,392   7 HPFS/NTFS
/dev/sda2         296,126,145   302,214,779     6,088,635   f W95 Ext d (LBA)
/dev/sda5         296,126,208   302,214,779     6,088,572  82 Linux swap / Solaris
/dev/sda3         302,230,845   312,480,314    10,249,470   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.1 GB, 16064184320 bytes
255 heads, 63 sectors/track, 1953 cylinders, total 31375360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    31,375,359    31,375,297   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4A30C94A30C93E27                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        CCED-990E                              vfat       PE                            
/dev/sda5        ac87daa3-3f07-4328-bf69-407d9994106b   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C4FA-0C34                              vfat       Äè%                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

```

---

### Post by darkod on 2010-05-28
You don't have a Ubuntu (Linux) partition reported at all:

```
Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   [COLOR=Red]151,123,454[/COLOR]   151,123,392   7 HPFS/NTFS
/dev/sda2         [COLOR=Red]296,126,145[/COLOR]   302,214,779     6,088,635   f W95 Ext d (LBA)
/dev/sda5         296,126,208   302,214,779     6,088,572  82 Linux swap / Solaris
/dev/sda3         302,230,845   312,480,314    10,249,470   c W95 FAT32 (LBA)
```

I guess it is (it was) between /dev/sda1 and /dev/sda2. You really messed up when resizing...

If you have important data to save, you could try recovering the partition with testdisk, otherwise, a simple reinstall might be better option.
Just delete /dev/sda5 and then /dev/sda2 and install into that unallocated space.

---

### Post by goseph on 2010-05-29
Bah! Did a re-install. All I did to mess things up was resize my swap in GParted - if I mess around with partitions in the future and get error messages (which I basically ignored this time round). Is it possible to undo the changes? Is there a program that is safer to use?

---

### Post by darkod on 2010-05-29
If you want to save this partition, there is a program called testdisk. You can install it and run it in live mode with:

sudo apt-get install testdisk
sudo testdisk

Here is their guide about restoring a partition:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

People have reported good success with it restoring a deleted partition. It basically scans your hdd and if it finds the partition, you can write it back in the partition table.

But be careful with it, you can mess up all of the current partition, as with any software of this kind. As long as you pay attention of the sectors /start/end, so the partitions don't overlap, you should be fine.

Otherwise, Gparted is a very good tool for partition management but it all depends what you actually did. For example, it looks like you actually resized not the swap partition /dev/sda5, but the whole extended partition /dev/sda2 which was probably also holding your root partition.

An extended partition is just like a container, and the logical partitions are inside. When you want to resize a logical partition, make sure you do that, and not resizing the extended container.

---

### Post by goseph on 2010-05-29
Thankyou for your wise words Darkod,

Incidentally, running sudo apt-get install testdisk doesn't do anything - the terminal can't find it.

running apt-cache search test gives lots of results but no testdisk

This is all on an unaltered live USB of Lucid netbook remix and following a sudo apt-get update.

I downloaded the binaries from here [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

and it worked fine, any ideas as to why it is not in the repositories?

---

### Post by darkod on 2010-05-29
Ups, I now remember that it seems you need to enable another repository called universe. I think it's not in the default ones. Sorry. :)

---

