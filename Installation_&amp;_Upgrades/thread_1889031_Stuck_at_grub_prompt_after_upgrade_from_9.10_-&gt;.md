---
title: "Stuck at grub prompt after upgrade from 9.10 -&gt; 10.04"
date: 2011-11-30
forum: Installation &amp; Upgrades
---

### Post by ChaozUT on 2011-11-30
**Background: **

After upgrading from Ubuntu 9.10 to 10.04 via the update manager, I was stuck at grub rescue prompt after rebooting. After trying the GRUB repair utility I can now boot to a grub> prompt but no further.

I was not the original person who set this machine up. On this machine there are six 1.5TB drives, sda through sdf, with two partitions each. The first partition is 1GB (ex. sda1) and the second is the rest of the drive (ex. sda2)
- sda1 to sde1 is in a 5 drive RAID5 config to make 4GB of what I think is swap space (md126)
- sda2 to sdf2 is in a 6 drive RAID5 config to form one big ~7.5TB drive (md127)
- sdf1 is a single 1GB partition which seems to be for booting purposes.

**Problem:**

- First of all, I am now stuck at the grub> prompt when trying to boot.
- When I type "boot" it says something along the lines of "kernel not set". 
- When I type "set" it shows a bunch of config data, but mainly it shows that the root is (md127), the big 7.5TB drive, and that the prefix is (md127)/boot/grub/

What is confusing me and I think that this may be the source of the problem is that both md127 and sdf1 have grub folders on them. Also, it seems like each has only part of the files. I have listed out an overview of the directory listing for these two drives to show what I mean by this. Hopefully, whoever looks at this will be able to see what needs to be done. I have some suspicions but would rather not act on them yet without some guidance since I am not a linux expert. Here is the listing:

[COLOR="Blue"]BLUE[/COLOR] = Directory
[COLOR="DarkGreen"]GREEN[/COLOR] = File
Black = Comment

> 
**/md127/:** (7.5TB RAID5)
- [COLOR="Blue"]/boot/[/COLOR]
[INDENT]- [COLOR="blue"]/grub/[/COLOR][/INDENT]
[INDENT][INDENT]- [COLOR="blue"]/locale/[/COLOR][/INDENT][/INDENT]
[INDENT][INDENT][INDENT]- [COLOR="DarkGreen"]en_AU.mo[/COLOR][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT]- [COLOR="DarkGreen"]en_CA.mo[/COLOR][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT]- [COLOR="DarkGreen"]en_GB.mo[/COLOR][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT]- [COLOR="DarkGreen"]fs.list[/COLOR][/INDENT][/INDENT]
[INDENT][INDENT]- [COLOR="DarkGreen"]grub.cfg[/COLOR][/INDENT][/INDENT]
[INDENT][INDENT]- [COLOR="DarkGreen"]grubenv[/COLOR][/INDENT][/INDENT]
[INDENT][INDENT]- <other misc .mod .img .lst files, except no menu.lst>[/INDENT][/INDENT]
[INDENT]- <nothing else>[/INDENT]
- [COLOR="DarkGreen"]initrd.img[/COLOR] (symbolic link to boot/initrd.img-2.6.32-35-generic, which [COLOR="Red"]DOES NOT EXIST[/COLOR] on this drive)
- [COLOR="DarkGreen"]initrd.img.old[/COLOR] (symbolic link to boot/initrd.img-2.6.31-19-generic, which [COLOR="red"]DOES NOT EXIST[/COLOR] on this drive)
- [COLOR="DarkGreen"]vmlinuz[/COLOR] (same thing as above, symbolic link to something that does not exist)
- [COLOR="DarkGreen"]vmlinuz.old[/COLOR]
- <system folders such as dev, home, usr, var, etc.>


**/sdf1/:** (1GB single partition)
- [COLOR="blue"]/boot/[/COLOR]
[INDENT]- [COLOR="blue"]/grub/[/COLOR][/INDENT]
[INDENT][INDENT]- <seems to have everything except [COLOR="Red"]grub.cfg[/COLOR] and menu.lst>[/INDENT][/INDENT]
[INDENT]- <nothing else>[/INDENT]
- [COLOR="blue"]/grub/[/COLOR]
[INDENT]- <seems to have everything except menu.list>[/INDENT]
- <bunch of abi-... with latest being [COLOR="DarkGreen"]abi-2.6.32-35-generic[/COLOR]>
- <bunch of config-... with latest being [COLOR="DarkGreen"]config-2.6.32-35-generic[/COLOR]>
- <bunch of initrd... with latest being [COLOR="DarkGreen"]initrd.img-2.6.32-35-generic[/COLOR]>
- <bunch of System.map... with latest being [COLOR="DarkGreen"]System.map-2.6.32-35-generic[/COLOR]>
- <bunch of vmcoreinfo... with latest being [COLOR="DarkGreen"]vmcoreinfo-2.6.32-35-generic[/COLOR]>
- <bunch of vmlinuz... with latest being [COLOR="DarkGreen"]vmlinuz-2.6.32-35-generic[/COLOR]>
- [COLOR="DarkGreen"]memtest86+.bin[/COLOR]


Just from the above I am not sure which files are needed where for the boot to be successful. It seems that md127 contains initrd and vmlinuz symbolic links that point to files that do not exist on md127 (but does exist on sdf1). But at the same time, there are 2 grub folders on sdf1 (/boot/grub and /grub) and one of them is missing a grub.cfg file.

Any advice on how to proceed would be greatly greatly appreciated. :confused:

---

### Post by Rubi1200 on 2011-11-30
Hi and welcome to the forums :-)

Thanks for supplying us with as much information as possible as it really helps us.

One more thing we need right now is to see the results of the boot info script.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by ChaozUT on 2011-11-30
The boot_info_script output is below. One additional thing to note is that I just realized that the RAID5 (md127) partition that I reassembled is stuck in read-only mode, and auto mounts after I dismount it. I am not sure if this would have caused by problem (or perhaps cause a different problem down the line once it boots...). I am currently running the RAID repair utility on the 10.04 liveCD.

EDIT: ignore sdg. That is an external hard drive I plugged in.

>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (md127)/boot/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (md127)/boot/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (md127)/boot/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdd and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (md127)/boot/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sde and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (md127)/boot/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdf and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (md127)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdg.

sda1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdc2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdd1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdd2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sde1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sde2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdf1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdf1 and looks at sector 392063 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 1 for /grub.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img /boot/grub/core.img

sdf2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdg1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

md126: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

md127: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63     1,959,929     1,959,867  fd Linux raid autodetect
/dev/sda2           1,959,930 2,930,272,064 2,928,312,135  fd Linux raid autodetect


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     1,959,929     1,959,867  fd Linux raid autodetect
/dev/sdb2           1,959,930 2,930,272,064 2,928,312,135  fd Linux raid autodetect


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63     1,959,929     1,959,867  fd Linux raid autodetect
/dev/sdc2           1,959,930 2,930,272,064 2,928,312,135  fd Linux raid autodetect


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63     1,959,929     1,959,867  fd Linux raid autodetect
/dev/sdd2           1,959,930 2,930,272,064 2,928,312,135  fd Linux raid autodetect


Drive: sde _____________________________________________________________________

Disk /dev/sde: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1                  63     1,959,929     1,959,867  fd Linux raid autodetect
/dev/sde2           1,959,930 2,930,272,064 2,928,312,135  fd Linux raid autodetect


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *             63     1,959,929     1,959,867  83 Linux
/dev/sdf2           1,959,930 2,930,272,064 2,928,312,135  fd Linux raid autodetect


Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 1500.3 GB, 1500301910016 bytes
1 heads, 63 sectors/track, 46512336 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1                  63 2,930,272,127 2,930,272,065   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/md126       73f979af-ab81-4385-9876-cda06ff85a46   swap       
/dev/md127       fbafc46f-7238-4af5-a6e7-e9241e3acc4f   ext4       bigdrive
/dev/sda1        3444b803-6d39-fac1-486d-98e3a3ed0bff   linux_raid_member 
/dev/sda2        15135403-8c15-00bd-4955-6804d345d67a   linux_raid_member 
/dev/sdb1        3444b803-6d39-fac1-486d-98e3a3ed0bff   linux_raid_member 
/dev/sdb2        15135403-8c15-00bd-4955-6804d345d67a   linux_raid_member 
/dev/sdc1        3444b803-6d39-fac1-486d-98e3a3ed0bff   linux_raid_member 
/dev/sdc2        15135403-8c15-00bd-4955-6804d345d67a   linux_raid_member 
/dev/sdd1        3444b803-6d39-fac1-486d-98e3a3ed0bff   linux_raid_member 
/dev/sdd2        15135403-8c15-00bd-4955-6804d345d67a   linux_raid_member 
/dev/sde1        3444b803-6d39-fac1-486d-98e3a3ed0bff   linux_raid_member 
/dev/sde2        15135403-8c15-00bd-4955-6804d345d67a   linux_raid_member 
/dev/sdf1        b081ffab-a0db-4d17-969b-a8ac4899ec3b   ext4       
/dev/sdf2        15135403-8c15-00bd-4955-6804d345d67a   linux_raid_member 
/dev/sdg1        1A20A39D20A37DFF                       ntfs       Expansion Drive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/md127       /media/bigdrive          ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdf1        /media/b081ffab-a0db-4d17-969b-a8ac4899ec3b ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdg1        /media/Expansion Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


============================= sdf1/grub/grub.cfg: ==============================

---

