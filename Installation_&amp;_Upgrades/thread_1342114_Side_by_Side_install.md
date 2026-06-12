---
title: "Side by Side install?"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by bigsmitty64 on 2009-11-30
I always feel the need to start with  "Complete Newbie here!" 
That said,
I am currently running Windows vista on my "c" drive, and installed Ubuntu 9.10 on my "d" drive,and I am wondering,can I install Ubuntu STUDIO 9.10 on my "d" drive also and have 3 boot options? I no there is probably no real value to doing this,but would like the option.Space is not an issue as my "d" drive is 1 TB.
I started a thread in "Multimedia Production" about upgrade vs fresh install,but then thought why can't I just do this? Thanks in advance for any help!
Smitty

---

### Post by darkod on 2009-11-30
Hold on, we need to clarify something. C: and D: is what windows uses. The only option to install Ubuntu to D: is to actually install wubi (not ubuntu). Otherwise a proper ubuntu ext3/ext4 partition would not be seen or recognized by windows, so it can't be D:.
What did you actually do?

---

### Post by ubername on 2009-11-30
> **bigsmitty64 said:**
> I always feel the need to start with  "Complete Newbie here!" 
That said,
I am currently running Windows vista on my "c" drive, and installed Ubuntu 9.10 on my "d" drive,and I am wondering,can I install Ubuntu STUDIO 9.10 on my "d" drive also and have 3 boot options? I no there is probably no real value to doing this,but would like the option.Space is not an issue as my "d" drive is 1 TB.
I started a thread in "Multimedia Production" about upgrade vs fresh install,but then thought why can't I just do this? Thanks in advance for any help!
Smitty

Absolutely you can. Just boot from the studio live cd and when it asks for where you want to install choose your 1Tb drive. Make sure you don't select the 'use entire disk' option. Then it's up to you whether you want to manually set the partition sizes (resize your 9.10 install to eg 500Gb and use 500Gb for studio) or let the partitioner do it (which I believe will use most of the disk for the studio install and resize the existing 9.10 partition(s) with not much free space). Of course, if you want to do anything fancy like sharing /home partitions you will need to research that. It's easy enough though.

---

### Post by bigsmitty64 on 2009-11-30
> **darkod said:**
> Hold on, we need to clarify something. C: and D: is what windows uses. The only option to install Ubuntu to D: is to actually install wubi (not ubuntu). Otherwise a proper ubuntu ext3/ext4 partition would not be seen or recognized by windows, so it can't be D:.
What did you actually do?


  Windows vista is on my "c" drive,   
   Ubuntu 9.10 is on my "d" drive

I want to install Studio on "d" , AND leave the original  install of Ubuntu 9.10 on "d"

---

### Post by darkod on 2009-11-30
You mean you have two hard drives as physical devices?

---

### Post by bigsmitty64 on 2009-11-30
> **ubername said:**
> Absolutely you can. Just boot from the studio live cd and when it asks for where you want to install choose your 1Tb drive. Make sure you don't select the 'use entire disk' option. Then it's up to you whether you want to manually set the partition sizes (resize your 9.10 install to eg 500Gb and use 500Gb for studio) or let the partitioner do it (which I believe will use most of the disk for the studio install and resize the existing 9.10 partition(s) with not much free space). Of course, if you want to do anything fancy like sharing /home partitions you will need to research that. It's easy enough though.

Thanks, I think I'll use a bit smaller partitions though,as I use that drive for storage,(pics,music, etc). I'll give it a go then,and report back when done.

---

### Post by bigsmitty64 on 2009-11-30
> **darkod said:**
> You mean you have two hard drives as physical devices?
yes, "c" and "d" are seperate physical drives,but I want to install 2 versions of ubuntu on one drive  "d"

---

### Post by ubername on 2009-11-30
> **bigsmitty64 said:**
> Thanks, I think I'll use a bit smaller partitions though,as I use that drive for storage,(pics,music, etc). I'll give it a go then,and report back when done.

Cool

Sounds like you already have at least two partitions on your 1Tb drive, one of which holds your pics and stuff, which is presumably NTSF which is why you refer to it as D: and can see it in windows. The other partition(s) are for your ubuntu 9.10. You may want to just take a moment to think about how you want to partition that drive as you are limited to 4 primary partitions on a drive. So long as you only want to put studio on it as well, and not be too fancy with partitions, you should be OK but anything more than that you may want to research creating extended partitions and then use that.

---

### Post by bigsmitty64 on 2009-11-30
Uber,
Thats correct, I have 2 partitions on that drive,just as you said,I can view my pics and such in windows and Ubuntu. I am just considering this,as I already have Ubuntu but would like Ubuntu Studio,for the "Musician" in me. Still undecided. AT least I know I can do it now. Thank you all for your input.This is a great place for converts like me,and I truly appreciate the volunteers time and effort.

Smitty

---

### Post by presence1960 on 2009-11-30
It would save confusion if you refer to devices/drives as sda, sdb, sdc, etc and the partitions on those devices as sda1, sda2, sda3, etc. Linux does not label devices/drives as windows does. This is a Linux community and you should try using linux nomenclature as darkod is correct. If you hav Ubuntu installed to a partition not installed via wubi, then windows will not assign a letter to that disk/partition because windows does not have the ability to acknowledge that in my computer or windows explorer. In windows disk management it will show up as unknown.

By saying Ubuntu is installed on D: tells me that since windows sees the D: it is a wubi install.

To save confusion use the command in terminal ```
sudo fdisk -l
``` to get a listing of your devices and their linux names. If you need more intensive info run the boot info script in my signature. Use the link to download the script to your desktop then run this command in terminal ```
sudo bash ~/Desktop/boot_info_script*.sh
``` it will create a file RESULTS.txt on the desktop that contains a wealth of info about your setup & boot process.

---

### Post by presence1960 on 2009-11-30
why don't you run that boot info script so there is absolutely no confusion about your setup so you get the best advice possible.

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by ubername on 2009-11-30
Hang on in there bigsmitty, it takes time to get the hang of linux nomenclature. 
and thanks presencce1960 for showing me 
```
how to put thing in code
```

---

### Post by presence1960 on 2009-11-30
> **ubername said:**
> Hang on in there bigsmitty, it takes time to get the hang of linux nomenclature. 
and thanks presencce1960 for showing me 
```
how to put thing in code
```

You are welcome ubername. I hope bigsmitty does not think I was lambasting him. We all want him to get the help he needs. If he can use terms that will more accurately describe his setup then he can get more detailed help, and probably even more than one way to do what he wants to accomplish.

---

### Post by bigsmitty64 on 2009-11-30
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sde
 => No boot loader is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xada241d7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,953,522,143 1,953,522,081   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf7eef7ee

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2052 MB, 2052513792 bytes
16 heads, 63 sectors/track, 3977 cylinders, total 4008816 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     4,007,807     4,007,745   6 FAT16


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sde1               8,192     7,744,511     7,736,320   b W95 FAT32


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 4001 MB, 4001366016 bytes
248 heads, 19 sectors/track, 1658 cylinders, total 7815168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *          6,384     7,805,167     7,798,784   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: UUID="3ac2b7e1-5b3e-444e-acfd-acd351cdd634" TYPE="ext4" 
/dev/sda1: UUID="3CF00CD7F00C98F2" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb1: UUID="84E2D584E2D57B3E" TYPE="ntfs" 
/dev/sdc1: SEC_TYPE="msdos" LABEL="LEXAR" UUID="FC30-3DA9" TYPE="vfat" 
/dev/sde1: LABEL="^?M-^OM-qM-^MM-oM-o^M-SoM-*=" UUID="6463-3234" TYPE="vfat" 
/dev/sdf1: LABEL="" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/loop0 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda1 on /host type fuseblk (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bigsmitty/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bigsmitty)
/dev/sdc1 on /media/LEXAR type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdf1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sde1 on /media/ type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb1 on /media/84E2D584E2D57B3E type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================== sda1Wubi: ==================================

Operating System: "Ubuntu 9.10"

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
=======Devices which don't seem to have a corresponding hard drive==============

sdd 
```

---

### Post by bigsmitty64 on 2009-11-30
> **presence1960 said:**
>  I hope bigsmitty does not think I was lambasting him.

Nope,not at all! I had to run out for a while. As I do again,but I'll be back on in about an hour.Thanks !!!!

---

### Post by presence1960 on 2009-11-30
> **bigsmitty64 said:**
> ```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sde
 => No boot loader is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xada241d7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,953,522,143 1,953,522,081   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf7eef7ee

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2052 MB, 2052513792 bytes
16 heads, 63 sectors/track, 3977 cylinders, total 4008816 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     4,007,807     4,007,745   6 FAT16


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sde1               8,192     7,744,511     7,736,320   b W95 FAT32


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 4001 MB, 4001366016 bytes
248 heads, 19 sectors/track, 1658 cylinders, total 7815168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *          6,384     7,805,167     7,798,784   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: UUID="3ac2b7e1-5b3e-444e-acfd-acd351cdd634" TYPE="ext4" 
/dev/sda1: UUID="3CF00CD7F00C98F2" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb1: UUID="84E2D584E2D57B3E" TYPE="ntfs" 
/dev/sdc1: SEC_TYPE="msdos" LABEL="LEXAR" UUID="FC30-3DA9" TYPE="vfat" 
/dev/sde1: LABEL="^?M-^OM-qM-^MM-oM-o^M-SoM-*=" UUID="6463-3234" TYPE="vfat" 
/dev/sdf1: LABEL="" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/loop0 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda1 on /host type fuseblk (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bigsmitty/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bigsmitty)
/dev/sdc1 on /media/LEXAR type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdf1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sde1 on /media/ type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb1 on /media/84E2D584E2D57B3E type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================== sda1Wubi: ==================================

Operating System: "Ubuntu 9.10"

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
=======Devices which don't seem to have a corresponding hard drive==============

sdd 
```

The boot info script reveals a lot! You have Ubuntu installed inside windows with wubi. I am not sure if you can add another install via wubi inside the same Windows OS. But you have all that hard disk space why dont you partition say about 15-20 GB for Ubuntu Studio 9.10 root and an amount equal to your installed ram as swap. If you need help partitioning post back we will be glad to help you with it. That is what I would recommend to do.

---

