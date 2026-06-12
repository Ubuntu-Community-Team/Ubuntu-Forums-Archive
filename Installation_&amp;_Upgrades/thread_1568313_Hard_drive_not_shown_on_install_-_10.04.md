---
title: "Hard drive not shown on install - 10.04"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by shootscore on 2010-09-05
Trying to install Ubuntu 10.04 desktop 64-bit using live CD.  After choosing keyboard layout on step 3 of 7, the next screen is not the 'Prepare Disk Space' screen that I should expect according to [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall).  Instead I get a blank screen titled 'Prepare Partitions' with nothing listed and everything but 'Quit', 'Back', and 'Forward' grayed out.
 [ATTACH]168541[/ATTACH]

However, when I boot from the live cd, the disk utility (screenshot below), Gparted, fdisk, and parted all display the WD 640GB hard drive. But for some reason, it doesn't show up during the install.
[ATTACH]168542[/ATTACH]

Currently, all drive space is unallocated except for a 40GB partition with Win7 installed.  Could this be due to WD's 'Advanced Format' using 4kb sectors?

Also tried installing Ubuntu 9.04 server 64-bit, but that is also giving me a blank screen at the same point in the process.

Thoughts?

---

### Post by sanderj on 2010-09-05
What do you see when you use the Ubuntu **10.10 Beta** live CD?

---

### Post by Jamppi on 2010-09-05
I have the same problem with 10.04.1 and 10.10 Pre-release. No hard drive was shown until I selected the option "try without any modifcation" then I could see the hard drive. When I doubl-clicked the "Install Ubuntu", the hard drive disappeared immediately. When I had to restart because installer crashed. Then I tried the Live CD again, this time I openeg Gparted. This program had problems with the hard drive. Then I took Disk Utility, formatted the drive to ext4 - now this time Disk Utility managed to do what GParted did not. I could see the hd during installation, but there is a strange bug in my pc -* it does not like Ubuntu.

When I try the CD installation, it gives me the I/O error.
When I try the USB HD boot, it loads forever and forever for hours and never do I see the point when I can start installing.

The only OP systems I can install here is Debian 5.0 x64 through net install and Windows by DVD/CD. I do not like both of them....

---

### Post by dino99 on 2010-09-05
there you will find a little help about how to install ubuntu:
[http://ubuntuforums.org/showpost.php...4&postcount=14](http://ubuntuforums.org/showpost.php...4&postcount=14)

---

### Post by shootscore on 2010-09-06
sanderj - I haven't tried installing 10.10 pre-release yet, as this machine hasn't been connected to the internet (probably tomorrow)--and it looks like the install for 10.10 requires an internet connection.  I'll let you know what happens with that install attempt.

Jamppi - what make/model hard drive are you using?

dino99 - when I click on the link in your reply, it dropped me into the Ubuntu Forums main page.  Is that what you were intending?

Thanks for your replies.

---

### Post by shootscore on 2010-09-08
Tried installing again today using the 10.10 beta live CD.  Still not recognizing the hard drive per the following screenshot.

[ATTACH]168841[/ATTACH]

---

### Post by sanderj on 2010-09-08
Have you tried Jamppi's method "Then I took Disk Utility, formatted the drive to ext4 - now this time Disk Utility managed to do what GParted did not. I could see the hd during installation"?

---

### Post by srs5694 on 2010-09-08
Could you post the output of "sudo fdisk -lu", preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility? I'm far from positive, but it could be you're running into the problem described [here.](http://nessus.rodsbooks.com/missing-parts/index.html) If so, the fdisk output will show it. Note that the fdisk parameters are a lowercase L and lowercase U, not a digit 1 and lowercase U.

---

### Post by Turboaaa2001 on 2010-09-08
I am running into the same problem. When installing 10.4 (or latest edubuntu) the installer cannot see the drive.

I am able to format and partition the drive via the live CD, but as soon as I run the installer the drive cannot be found thus I cannot install. This is the first problem I have ever had installing Ubuntu on any system. Makes me sad :(

AMD 4050e
2GB
A poorly made PC Chips A33G mobo
WDC 160GB SATA

This system is intended for my 2 and 3 year old to mess around with.

---

### Post by shootscore on 2010-09-08
Thanks for all your replies.

Here's the output from 'fdisk -lu':

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x401de083

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    83896959    41947456    7  HPFS/NTFS
```The  partition shown here is the 'shrunk' ntfs partition which contains Win 7  Home 64-bit.  I'm hoping to keep this partition for dual-booting using a  method similar to the one [described here]("http://ubuntuguide.org/wiki/Multiple_OS_Installation").  This is the only thing keeping me from using Jamppi's method of formatting the entire drive to ext4.

Originally  I thought that this was due to having an 'Advanced Format' hard drive  using physical sectors of 4096 bytes, each broken into 8 logical sectors  of 512 bytes.  Taking a closer look at the specs on the WDC page, the  hard drive I'm using (model WD6400aaks) does use 512 byte sectors...so  I'm even more confused.

---

### Post by tommcd on 2010-09-08
Try formatting the space you intend to use for Ubuntu using the Parted Magic live CD:
[http://partedmagic.com/](http://partedmagic.com/)
You can create your Ubuntu root, swap, and home partitions with the Parted Magic live CD. Then boot the Ubuntu install CD and see if it will find the partitions for install.

---

### Post by shootscore on 2010-09-09
tommcd- I used Gparted to create several new partitions on the drive.  This was before I read your response, so didn't use Parted Magic.  Following are the 'fdisk -lu' output and the print output from parted:
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x401de083

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    83896959    41947456    7  HPFS/NTFS
/dev/sda2        83907495  1059069059   487580782+   b  W95 FAT32
/dev/sda3      1059069060  1059277904      104422+  83  Linux
/dev/sda4      1059277905  1248025589    94373842+   5  Extended
/dev/sda5      1059277968  1071856799     6289416   82  Linux swap / Solaris
/dev/sda6      1071856863  1176713054    52428096   83  Linux
/dev/sda7      1176713118  1239623594    31455238+  83  Linux
ubuntu@ubuntu:~$ sudo parted
GNU Parted 2.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s
(parted) print                                                            
Model: ATA WDC WD6400AAKS-2 (scsi)
Disk /dev/sda: 1250263728s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start        End          Size        Type      File system     Flags
 1      2048s        83896959s    83894912s   primary   ntfs            boot
 2      83907495s    1059069059s  975161565s  primary   fat32
 3      1059069060s  1059277904s  208845s     primary   ext3
 4      1059277905s  1248025589s  188747685s  extended
 5      1059277968s  1071856799s  12578832s   logical   linux-swap(v1)
 6      1071856863s  1176713054s  104856192s  logical   ext4
 7      1176713118s  1239623594s  62910477s   logical   ext3


```
After searching the forum some more, I used the Boot Info Script referred to [here ]("http://ubuntuforums.org/showthread.php?t=1486004")and [here]("http://ubuntuforums.org/showpost.php?p=8844901&postcount=4").  This script gave the following output:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdg
 => Windows is installed in the MBR of /dev/mapper/pdc_cdcabhcdbd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 83907495.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda2 already mounted or sda2 busy

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda2 already mounted or sda2 busy
mount: /dev/sda3 already mounted or sda3 busy

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda2 already mounted or sda2 busy
mount: /dev/sda3 already mounted or sda3 busy
mount: /dev/sda6 already mounted or sda6 busy

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sda2 already mounted or sda2 busy
mount: /dev/sda3 already mounted or sda3 busy
mount: /dev/sda6 already mounted or sda6 busy
mount: /dev/sda7 already mounted or sda7 busy

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

pdc_cdcabhcdbd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

pdc_cdcabhcdbd2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, 
                       pdc_cdcabhcdbd2 starts at sector 0. But according to 
                       the info from fdisk, pdc_cdcabhcdbd2 starts at sector 
                       83907495.
    Operating System:  
    Boot files/dirs:   

pdc_cdcabhcdbd3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

pdc_cdcabhcdbd4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

pdc_cdcabhcdbd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

pdc_cdcabhcdbd6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

pdc_cdcabhcdbd7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    83,896,959    83,894,912   7 HPFS/NTFS
/dev/sda2          83,907,495 1,059,069,059   975,161,565   b W95 FAT32
/dev/sda3       1,059,069,060 1,059,277,904       208,845  83 Linux
/dev/sda4       1,059,277,905 1,248,025,589   188,747,685   5 Extended
/dev/sda5       1,059,277,968 1,071,856,799    12,578,832  82 Linux swap / Solaris
/dev/sda6       1,071,856,863 1,176,713,054   104,856,192  83 Linux
/dev/sda7       1,176,713,118 1,239,623,594    62,910,477  83 Linux


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             80    15,663,103    15,663,024   c W95 FAT32 (LBA)


Drive: pdc_cdcabhcdbd ___________________ _____________________________________________________

Disk /dev/mapper/pdc_cdcabhcdbd: 640.1 GB, 640067895296 bytes
255 heads, 63 sectors/track, 77817 cylinders, total 1250132608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_cdcabhcdbd1   *          2,048    83,896,959    83,894,912   7 HPFS/NTFS
/dev/mapper/pdc_cdcabhcdbd2         83,907,495 1,059,069,059   975,161,565   b W95 FAT32
/dev/mapper/pdc_cdcabhcdbd3      1,059,069,060 1,059,277,904       208,845  83 Linux
/dev/mapper/pdc_cdcabhcdbd4      1,059,277,905 1,248,025,589   188,747,685   5 Extended
/dev/mapper/pdc_cdcabhcdbd5      1,059,277,968 1,071,856,799    12,578,832  82 Linux swap / Solaris
/dev/mapper/pdc_cdcabhcdbd6      1,071,856,863 1,176,713,054   104,856,192  83 Linux
/dev/mapper/pdc_cdcabhcdbd7      1,176,713,118 1,239,623,594    62,910,477  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/pdc_cdcabhcdbd1 2ACA074FCA07172B                       ntfs       Acer                          
/dev/mapper/pdc_cdcabhcdbd2 00DD-88E6                              vfat       Storage                       
/dev/mapper/pdc_cdcabhcdbd3 ebc6e0eb-f7c4-425b-ad90-7ebd059d3059   ext3       grub                          
/dev/mapper/pdc_cdcabhcdbd5 c37d509f-9509-4fe5-a085-0a36b1fe6b9a   swap       swap                          
/dev/mapper/pdc_cdcabhcdbd6 8cde4a19-dfe1-42d9-912c-519e5cbf3814   ext4       Ubuntu                        
/dev/mapper/pdc_cdcabhcdbd7 568b5518-43b1-497a-97dd-c45878ac178a   ext3       linuxOther                    
/dev/mapper/pdc_cdcabhcdbd: PTTYPE="dos" 
/dev/sda1        2ACA074FCA07172B                       ntfs       Acer                          
/dev/sda2        00DD-88E6                              vfat       Storage                       
/dev/sda3        ebc6e0eb-f7c4-425b-ad90-7ebd059d3059   ext3       grub                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        c37d509f-9509-4fe5-a085-0a36b1fe6b9a   swap       swap                          
/dev/sda6        8cde4a19-dfe1-42d9-912c-519e5cbf3814   ext4       Ubuntu                        
/dev/sda7        568b5518-43b1-497a-97dd-c45878ac178a   ext3       linuxOther                    
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdg1        79D0-DBE4                              vfat       Lexar                         
/dev/sdg: PTTYPE="dos" 
error: /dev/mapper/pdc_cdcabhcdbd4: No such file or directory
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdg1        /media/Lexar             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on pdc_cdcabhcdbd4



=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf 
=============================== StdErr Messages: ===============================

hexdump: /dev/mapper/pdc_cdcabhcdbd4: No such file or directory
hexdump: /dev/mapper/pdc_cdcabhcdbd4: No such file or directory

```Am I correct in reading this to mean that the MBR is messed up?  Any recommendations for backing up and modifying the MBR using 'sfdisk'?

Thanks!

---

### Post by Turboaaa2001 on 2010-09-09
I ran pmagic-5.4 and tried formatting a 100GB ext4 and a 4GB swap partition. I received the following error message when creating the ext4 partition:

```
mke2fs 1.41.11 (14-Mar-2010)
Could not stat /dev/sda1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
```


Note: The partitions I created using the Ubuntu live CD were found. I deleted them and attempted to make new ones.

However there were no problems when creating an ext3 partition, but Ubuntu was still unable to see the drive when installing. Also Windows is able to recognize the drive and install to it.

---

### Post by shootscore on 2010-09-11
Tried installing again using an older version (9.04) of Ubuntu--this time the desktop version (originally it was the server version). Not sure why, but this time there were no problems. The installation process showed the disk partitions, and I was able to install grub to the boot sector. Can still dual-boot to windows.
 
Now all that's left to do is install the 10.04 version....
 
Thanks for all the help on this!

---

