---
title: "Ubuntu and raid 0 &amp; 1 (two stripes)"
date: 2012-03-15
forum: Installation &amp; Upgrades
---

### Post by Danielsann on 2012-03-15
Hello from spain Ladies and gentlemans xD

First, sorry for my english :)

OK! Today i decided to install ubuntu 12.04 in my desktop PC. in my pc i was mounted a array with two disk, with 2 striped volumed, stripe 0 raid 0 and stripe 1 raid 1 in a chipset x58 (ich10) .

well, the installation of distro surprised me, ubuntu 12.04 64 alternate, has detected the array but only the first stripe (raid 0). The installation has ran very well and i  happy!

But i need to access to stripe 1 because is my "security folder". 
how i can do for access to this stripe??

Thank you! and sorry for my english i hope that you understand me!! (i don't use google translate haha)

greetings!

LOL i restart after installation and... grub fail!!!!! 

I think the grub need to install in other disc out of the raid? or maybe it can to install in raid with enything, i hope!!

---

### Post by Danielsann on 2012-03-15
Ok my problem with the stripes go away!!!

But a cant install grub2 into /dev/mapper/...

with fdisk -l or gparted dont appear the partitions "/" or swap When i start with the live-cd.

maybe i can install in sda?? or another disk.... um maybe in the raid 1... I will try it!!!

Try install grub2 from live-cd in the partition /... 

> sudo mount /dev/mapper/isw_ibgjhgigh_RAID0p6 /mnt
this@this:~$ sudo mount --bind /dev /mnt/dev
this@this:~$ sudo mount --bind /dev/pts /mnt/dev/pts
this@this:~$ sudo mount --bind /proc /mnt/proc
this@this:~$ sudo mount --bind /sys /mnt/sys
this@this:~$ sudo chroot /mnt
root@this:/# grub-install --recheck /dev/mapper/isw_ibgjhgigh_RAID0p6/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
root@this:/# grub-install --recheck /dev/mapper/isw_ibgjhgigh_RAID0p6
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.

---

### Post by darkod on 2012-03-15
Why are you trying to install grub to p6, the partition #6?

It should be installed to the MBR of the array, the /dev/mapper device without any partition number. Try that.

---

### Post by Danielsann on 2012-03-15
> **darkod said:**
> Why are you trying to install grub to p6, the partition #6?

It should be installed to the MBR of the array, the /dev/mapper device without any partition number. Try that.

Yeah! u are right and in a normal  situation i install grub for example in /dev/sda or sdb...

:-k upss... i try it. Thanks a lot!!!

---

### Post by Danielsann on 2012-03-15
Ok! 

I think grub is already install, but it can see 3 errors that i suppose almost one of these are the entry of W 7 instalation or others volumes or partitions. I dont know. 

Y try to restart and let's keep my fingers crossed  :lolflag:



> this@this:~$ sudo mount /dev/mapper/isw_ibgjhgigh_RAID0p5 /mnt
mount: /dev/mapper/isw_ibgjhgigh_RAID0p5 already mounted or /mnt busy
mount: according to mtab, /dev/mapper/isw_ibgjhgigh_RAID0p5 is already mounted on /mnt
this@this:~$ sudo mount --bind /dev /mnt/dev
this@this:~$ sudo mount --bind /dev/pts /mnt/dev/pts
this@this:~$ sudo mount --bind /proc /mnt/proc
this@this:~$ sudo mount --bind /sys /mnt/sys
this@this:~$ sudo chroot /mnt
root@this:/# update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-18-generic
Found initrd image: /boot/initrd.img-3.2.0-18-generic
Found memtest86+ image: /boot/memtest86+.bin
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
done
Thanks and greetings!

ED.

ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid
ERROR: mkdir /var/lock/dmraid

 these errors are my headache!!!

---

### Post by darkod on 2012-03-15
Hmmm, first you were mounting p6 as root, now you are mounting p5 as root. Be careful, don't just try unless you know which partition is your root. Find out first.

Lets see what happens after you restart but if it couldn't find the win7 than even if grub2 works fine it will boot only ubuntu.

If you want to you can run the boot info script from the link in my signature that will show more details. All the instructions and how to post the results are there.

Also, you might have some weird windows install on the raid, who knows.

---

### Post by Danielsann on 2012-03-15
> **darkod said:**
> Hmmm, first you were mounting p6 as root, now you are mounting p5 as root. Be careful, don't just try unless you know which partition is your root. Find out first.

Lets see what happens after you restart but if it couldn't find the win7 than even if grub2 works fine it will boot only ubuntu.

If you want to you can run the boot info script from the link in my signature that will show more details. All the instructions and how to post the results are there.

Also, you might have some weird windows install on the raid, who knows.

Yes p6 and p5, i formated the partitions and they changes the numeration, but this is OK. the problem is another. i try run boot info script and show the results here. 

I think ( i read about i to) maybe i need to put in grub.cfg some entries... 

ED. 
look at that: select on the recovery entry of the kernel (yes grub is installed and run ok) say this:

boot arg's (cat /proc/cmdline)
check rootdelay= (did the system wait long enough?)
check root = (did the system wait for the right device?)
and HERE ! Missing modules ( cat /proc/modules; ls /dev)
ALERT! /dev/disk/by_uuid/b52c3121-3eaf..........ca3c0d does not exist
here is the problem. i suppose. :)





Thanks!!

---

### Post by Danielsann on 2012-03-15
Ok the results of the boot script

  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.
 => Windows is installed in the MBR of /dev/sde.
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/isw_ibgjhgigh_RAID0 
    and looks at sector 1 of the same hard drive for core.img. core.img is at 
    this location and looks in partition 1 for .
 => Windows is installed in the MBR of /dev/mapper/isw_ibgjhgigh_RAID1.

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:   Syslinux looks at sector 61102 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the /multiboot 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

isw_ibgjhgigh_RAID01: __________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

isw_ibgjhgigh_RAID02: __________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_ibgjhgigh_RAID03: __________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_ibgjhgigh_RAID05: __________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_ibgjhgigh_RAID06: __________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_ibgjhgigh_RAID11: __________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 32.0 GB, 32015679488 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62530624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             32    62,530,623    62,530,592   c W95 FAT32 (LBA)


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048 3,907,026,943 3,907,024,896   7 NTFS / exFAT / HPFS


Drive: sde _____________________________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
224 heads, 19 sectors/track, 229504 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1               2,048   976,771,071   976,769,024   7 NTFS / exFAT / HPFS


Drive: isw_ibgjhgigh_RAID0 _____________________________________________________________________

Disk /dev/mapper/isw_ibgjhgigh_RAID0: 375.8 GB, 375809900544 bytes
255 heads, 63 sectors/track, 45689 cylinders, total 734003712 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_ibgjhgigh_RAID01   *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/isw_ibgjhgigh_RAID02            206,848   529,201,151   528,994,304   7 NTFS / exFAT / HPFS
/dev/mapper/isw_ibgjhgigh_RAID03        529,201,662   734,003,711   204,802,050   5 Extended
/dev/mapper/isw_ibgjhgigh_RAID05        529,201,664   721,423,871   192,222,208  83 Linux
/dev/mapper/isw_ibgjhgigh_RAID06        721,424,384   734,003,711    12,579,328  82 Linux swap / Solaris


Drive: isw_ibgjhgigh_RAID1 _____________________________________________________________________

Disk /dev/mapper/isw_ibgjhgigh_RAID1: 312.2 GB, 312197910528 bytes
255 heads, 63 sectors/track, 37955 cylinders, total 609761544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_ibgjhgigh_RAID11              2,048   609,759,231   609,757,184   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_ibgjhgigh_RAID0p1 32CC0C67CC0C27A5                       ntfs       System Reserved
/dev/mapper/isw_ibgjhgigh_RAID0p2 CEF4570CF456F5E5                       ntfs       
/dev/mapper/isw_ibgjhgigh_RAID0p5 b25c3112-3eaf-4361-8155-3f910eca3c0d   ext4       
/dev/mapper/isw_ibgjhgigh_RAID0p6 790391cf-a77e-4752-af33-dc951ab53c8b   swap       
/dev/mapper/isw_ibgjhgigh_RAID1p1 D0E01A35E01A21F0                       ntfs       
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 
/dev/sdc1        1A12-1627                              vfat       MULTIBOOT
/dev/sdd1        C22C8C782C8C696D                       ntfs       Datos
/dev/sde1        127C28527C283341                       ntfs       DATA

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_ibgjhgigh_RAID0
isw_ibgjhgigh_RAID0p1
isw_ibgjhgigh_RAID0p2
isw_ibgjhgigh_RAID0p3
isw_ibgjhgigh_RAID0p5
isw_ibgjhgigh_RAID0p6
isw_ibgjhgigh_RAID1
isw_ibgjhgigh_RAID1p1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on isw_ibgjhgigh_RAID01


Unknown BootLoader on isw_ibgjhgigh_RAID02


Unknown BootLoader on isw_ibgjhgigh_RAID03


Unknown BootLoader on isw_ibgjhgigh_RAID05


Unknown BootLoader on isw_ibgjhgigh_RAID06


Unknown BootLoader on isw_ibgjhgigh_RAID11



=============================== StdErr Messages: ===============================

unlzma: (stdin): Compressed data is corrupt
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
hexdump: /dev/mapper/isw_ibgjhgigh_RAID01: No such file or directory
hexdump: /dev/mapper/isw_ibgjhgigh_RAID01: No such file or directory
hexdump: /dev/mapper/isw_ibgjhgigh_RAID02: No such file or directory
hexdump: /dev/mapper/isw_ibgjhgigh_RAID02: No such file or directory
hexdump: /dev/mapper/isw_ibgjhgigh_RAID03: No such file or directory
hexdump: /dev/mapper/isw_ibgjhgigh_RAID03: No such file or directory
hexdump: /dev/mapper/isw_ibgjhgigh_RAID05: No such file or directory
hexdump: /dev/mapper/isw_ibgjhgigh_RAID05: No such file or directory
hexdump: /dev/mapper/isw_ibgjhgigh_RAID06: No such file or directory
hexdump: /dev/mapper/isw_ibgjhgigh_RAID06: No such file or directory
hexdump: /dev/mapper/isw_ibgjhgigh_RAID11: No such file or directory
hexdump: /dev/mapper/isw_ibgjhgigh_RAID11: No such file or directory
```

---

### Post by Danielsann on 2012-03-16
Ok! It seem the problem is a bug on the 12.04. I try to install 10.04 lts and it has been rapid and secure. 

I dont know that actually was so easy install linux in a fakeraid, i only follow the installation and voila!!

Well i will left 12.04 installation for the future. Thanks darkod for your requests.

bye!

---

