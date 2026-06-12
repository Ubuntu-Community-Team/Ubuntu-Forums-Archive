---
title: "Ubuntu 10.10 won't boot"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by Fracta on 2010-11-13
Ok my ubuntu won't boot anymore.
I was trying to format a drive (a broken one) and the whole pc kinda froze. Couldn't open System Monitor to see what was going on (it wouldn't load), top in bash didn't give me any extra info, whenever I opened anything it wouldn't close, so I ended up just having to reboot. The hard way. Tried shutting down from the menu and nothing happened. I gave it enough time. Also, I have system monitor on the panel so I could see the cpu usage, and it was going nuts but nothing was showing in top that was using more than 5% cpu.
When I tried to boot up again, I get something like:

mounting /dev on /root/dev : failed, no such file or directory
mounting /sys on /root/sys : failed, no such file or directory
mounting /proc on /root/proc : failed, no such file or directory

Target filesystem doesn't have requested /sbin/init
no init found. Try passing init= bootarg

And here is the result of the boot info script:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Grub 0.97 is installed in the MBR of /dev/sdd and looks on boot drive #2 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   163,842,047   163,840,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   104,450,047   104,243,200   7 HPFS/NTFS
/dev/sdb3         104,450,048   488,392,703   383,942,656   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 2,930,274,303 2,930,272,256   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048   409,602,047   409,600,000   7 HPFS/NTFS
/dev/sdd2         409,602,048   781,418,495   371,816,448   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       54e4e0e5-bf11-43d4-9260-908e5864988f   ext4                                     
/dev/sda1        4C0250C30250B424                       ntfs       Linux                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D46CFDA16CFD7F14                       ntfs       System Reserved               
/dev/sdb2        AACC0975CC093D57                       ntfs       Windows                       
/dev/sdb3        E6003E9C003E7421                       ntfs       stor                          
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        BC2848252847DD50                       ntfs       Data Storage                  
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        647A3B8C7A3B5A4E                       ntfs       Games                         
/dev/sdd2        EC00434A00431B4A                       ntfs       Apps                          
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


```The problem seems to be here:
File system:       ext4
mount: wrong fs type

The filesystem linux is on is ntfs because I used wubi to install so I can have dual boot easily (not like I ever use windows anyway, but its handy when other people need it).

Any ideas anyone? I already did a chkdsk with windows (because that still boots up fine and still leaves a bad taste in my mouth) because I remember trying fscking an ntfs and it complained and people tell me if i want to do a check to use windows for ntfs.

One of these days I do intend to put ubuntu on its own drive with its own filesystem. 

thanks

---

### Post by bcbc on 2010-11-13
Try a previous kernel. Bootinfoscript often reports not being able to mount root.disk - doesn't always mean there's a problem.
If you can't boot a prior kernel, then boot from a live CD and run fsck on the root.disk as described in the [wubi guide]("https://wiki.ubuntu.com/WubiGuide").

---

### Post by Fracta on 2010-11-14
When I try to mount root.disk to do a scan it just says Killed. 
No error message or anything.

---

### Post by bcbc on 2010-11-14
> **Fracta said:**
> When I try to mount root.disk to do a scan it just says Killed. 
No error message or anything.

You don't (shouldn't) mount the root.disk to scan it. Just mount the windows partition and fsck the root.disk.

If you can mount the root.disk, can you see all your data? If so, it might be wise to back it up.

---

### Post by Fracta on 2010-11-15
Ubuntu isn't installed in the windows partition. I gave it its own drive and set the size to the biggest I could which was 30gb.

Yeah as soon as I realised what root.disk was, I made a copy.

Do you have any idea what actually went wrong here and if the OS is recoverable or am I looking at a reinstall? The only real problem with a reinstall is getting all my personal data out of root.disk because I already copied over most of the updates ubuntu has downloaded.

I shall have a go at fscking the root.disk file. I was just following the instructions from the page you gave me and it told me to mount root.disk.

---

### Post by bcbc on 2010-11-15
Are you getting stuck at a busybox prompt? I've seen a lot of these since 10.04.1 with kernel updates. It seems like there is a problem completing the update and in some cases the initramfs isn't properly updated.
If you only have one kernel then it's more difficult to fix - you have to chroot into your install and update the initramfs. And this doesn't always fix it either in my experience. 

So, if you can mount root.disk you can copy your data off it. Also there are programs you can use to access the root.disk from windows in read only mode. The wubi guide lists some, but I've found ext2read works. [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)

If you have a separate partition ('drive') for ubuntu it might be better to install direct to partition, instead of using wubi. Wubi uses the virtual disk which means you don't need to partition to use it. And as you've discovered it limits the size of the root.disk.

---

### Post by Fracta on 2010-11-25
I used ext2read to get all my data off root.disk and then reinstalled. Also got all of my updates out of uh /archives and put them in my new install so i don't need to redownload everything. Annoying process, but it works now.

---

