---
title: "Another Grub Rescue Problem"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by BacteriaEP on 2010-10-05
I know this issue has been posted before and I honestly tried to follow those other posts threads, but it's just not working, maybe because of my unique issue? Not sure... Here's what happened:

I installed Ubuntu 10.04 64-bit as a dual boot from Windows 7 about 2 months ago. Today, I decided to remove the 64 bit version and reinstall a 32 bit version since the 64 bit version simply didn't work. So I followed all the natural steps:

1. Delete the Ubuntu partition in Windows, clear it and start over fresh.
2. Download and burn Ubuntu 32 bit onto a CD.
3. Boot the CD and install directly from there.

Everything was going great until mid-install I got an error message saying something about my HDD messed up, yada yada yada. I don't remember the exact message, my install only got about 40% through. Once I clicked "Continue" the system just went into a sort of blank Ubuntu state. I had a mouse and the purple wallpaper, but no UI to speak of or anything like that.

At this point I was annoyed, but I figured... whatever, I'll just boot back into Windows delate the partition again, and start the process over again. No big deal right? 

Unfortunately, when I went to boot into Windows I got nothing but a "grub rescue:" prompt before I could do anything. The only thing I can seem to do is boot into the live CD, which is what I've done now.

I've read the other threads so I know you guys are going to look for this boot info script (BELOW).

Any help is greatly appreciated, even if it's only to get me back into Windows.

Thank you.

---

### Post by Darkness Des on 2010-10-05
Well, you were on the right track and you were, in all honesty, doing quite well until you hit the boot info script. That is the source behind it. We need you to actually run it.

---

### Post by BacteriaEP on 2010-10-05
> **Darkness Des said:**
> Well, you were on the right track and you were, in all honesty, doing quite well until you hit the boot info script. That is the source behind it. We need you to actually run it.

Ah... blond moment. Hopefully this is what you were looking for:

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sdb5 starts at sector 331370496.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    30,796,604    30,796,542   7 HPFS/NTFS
/dev/sda2    *     30,796,605   625,137,344   594,340,740   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    37,372,501    37,372,439   7 HPFS/NTFS
/dev/sdb2          37,373,950   625,141,759   587,767,810   5 Extended
/dev/sdb5         331,370,496   613,130,239   281,759,744   7 HPFS/NTFS
/dev/sdb6         613,132,288   625,141,759    12,009,472  82 Linux swap / Solaris
/dev/sdb7          37,373,952   319,348,735   281,974,784  83 Linux
/dev/sdb8         319,350,784   331,356,159    12,005,376  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C6F86154F86143B1                       ntfs       Recovery                      
/dev/sda2        78B48EC4B48E847A                       ntfs       Partition_1                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        124C91674C9145FF                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        B0A209C1A2098D52                       ntfs       New Volume                    
/dev/sdb6        79eca2e6-0a16-4051-9f67-72f6f515648a   swap                                     
/dev/sdb7        39cf119c-5653-4d17-ae71-3e1fdc7262ec   ext4                                     
/dev/sdb8        b9df6388-f8ff-4b64-8173-4f5a0a1d0998   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=39cf119c-5653-4d17-ae71-3e1fdc7262ec /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=b9df6388-f8ff-4b64-8173-4f5a0a1d0998 none            swap    sw              0       0
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

