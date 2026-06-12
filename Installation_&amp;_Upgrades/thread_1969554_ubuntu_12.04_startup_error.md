---
title: "ubuntu 12.04 startup error"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by zastrawhat on 2012-04-30
i get this error in startup "no root file system is defined" after installing ubuntu 12.04 from wubi.

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub4Dos is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /menu.lst /grldr /bootmgr /Boot/BCD /grldr

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:  Syslinux looks at sector 7762 of /dev/sdb1 for its 
                       second stage. The integrity of Syslinux couldn't be 
                       verified (install gawk). According to the info in the 
                       boot sector, sdb1 starts at sector 0. But according to 
                       the info from fdisk, sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   151,589,339   151,179,740   7 NTFS / exFAT / HPFS
/dev/sda3         151,589,340   625,137,344   473,548,005   f W95 Extended (LBA)
/dev/sda5         151,589,403   370,458,899   218,869,497   7 NTFS / exFAT / HPFS
/dev/sda6         370,458,963   590,517,269   220,058,307   7 NTFS / exFAT / HPFS
/dev/sda4         590,526,464   624,928,767    34,402,304   7 NTFS / exFAT / HPFS

/dev/sda3 overlaps with /dev/sda4

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2027 MB, 2027945984 bytes
63 heads, 62 sectors/track, 1014 cylinders, total 3960832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     3,960,683     3,960,622   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1E6615106614E9F3                       ntfs       SYSTEM
/dev/sda2        023C17DC3C17C995                       ntfs       
/dev/sda4        1458342D58340FCA                       ntfs       RECOVERY
/dev/sda5        0D8309300D830930                       ntfs       ENTERTAINMENT
/dev/sda6        0D7E15E70D7E15E7                       ntfs       WORK
/dev/sdb1        3086-3B64                              vfat       ZA

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda1/menu.lst: ================================

--------------------------------------------------------------------------------
# menu.lst produced by grub4dosconfig-v1.7
color white/blue black/cyan white/black cyan/black
timeout 10
default 0

# Frugal installed Puppy

title Lupu 528 (sda5/puppy528)
  find --set-root --ignore-floppies --ignore-cd /puppy528/initrd.gz
  kernel /puppy528/vmlinuz  pmedia=atahd psubdir=puppy528 pfix=fsck
  initrd /puppy528/initrd.gz

title Lupu 528 (sda5/puppy528) RAM mode\nBoot up Puppy without pupsave
  find --set-root --ignore-floppies --ignore-cd /puppy528/initrd.gz
  kernel /puppy528/vmlinuz  pmedia=atahd psubdir=puppy528 pfix=ram,fsck
  initrd /puppy528/initrd.gz

title Lupu 528 (sdb1)
  uuid 4433-2211
  kernel /vmlinuz  pmedia=usbflash  pfix=fsck
  initrd /initrd.gz

# Windows
# this entry searches Windows on the HDD and boot it up
title Windows\nBoot up Windows if installed
  errorcheck off
  find --set-root --ignore-floppies --ignore-cd  /bootmgr
  chainloader /bootmgr
  find --set-root --ignore-floppies --ignore-cd  /ntldr
  chainloader /ntldr
  find --set-root --ignore-floppies --ignore-cd   /io.sys
  chainloader /io.sys
  errorcheck on

title Windows Vista/2008/7 (sda1)
  uuid 1E6615106614E9F3
  chainloader /bootmgr

title Windows Vista/2008/7 (sda2)
  uuid 023C17DC3C17C995
  chainloader /bootmgr

title Windows Vista/2008/7 (sda4)
  uuid 1458342D58340FCA
  chainloader /bootmgr

# Boot from Partition Boot Sector

title Windows Vista/2008/7 (sda1:PBS)
  uuid 1E6615106614E9F3
  chainloader +1

title Windows Vista/2008/7 (sda2:PBS)
  uuid 023C17DC3C17C995
  chainloader +1

title Windows Vista/2008/7 (sda4:PBS)
  uuid 1458342D58340FCA
  chainloader +1

title Lupu 528 (sda5:PBS)
  uuid 0D8309300D830930
  chainloader +1

title Unknown (sda6:PBS)
  uuid 0D7E15E70D7E15E7
  chainloader +1

title Lupu 528 (sdb1:PBS)
  map (hd1) (hd0)
  map (hd0) (hd1)
  map --hook
  uuid 4433-2211
  chainloader +1

# additionals

title Find Grub2\nBoot up grub2 if installed
  find --set-root --ignore-floppies --ignore-cd /boot/grub/core.img
  kernel /boot/grub/core.img

title Grub4Dos commandline\n(for experts only)
  commandline

title Reboot computer
  reboot

title Halt computer
  halt
--------------------------------------------------------------------------------

========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
pxe detect
configfile
default 0
timeout 1
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             menu.lst                                       1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)


```

---

### Post by zastrawhat on 2012-04-30
Anyone................!!!
someone.............!!!

have any idea how to solve this, it looks like its a similar problem like others have but dont want to mess around..........

---

### Post by maxweld on 2012-04-30
Try reversing the boot sequence of your two disks in the System Bios.

It might be looking to boot from the incorrect disk. If this does not work, then return to the original boot sequence to avoid further confusion.

---

### Post by zastrawhat on 2012-05-01
> **maxweld said:**
> Try reversing the boot sequence of your two disks in the System Bios.

It might be looking to boot from the incorrect disk. If this does not work, then return to the original boot sequence to avoid further confusion.

two disks????, i only have one HD

---

### Post by zastrawhat on 2012-05-01
by start up i meant , ubuntu is available in microsoft's boot and after selecting ubuntu, ubuntu starts up and shows the top panel where the shutdown button is , then it says verifying installation and then this error shows up.:(

---

