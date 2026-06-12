---
title: "Kernel panic, cannot boot ~~"
date: 2012-07-15
forum: Installation &amp; Upgrades
---

### Post by utopiatw on 2012-07-15
Dear all:
   My ubuntu server don't work for some unknown reason.
   When the server boot, the screen show: 
 
             Kernel panic -- not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

   And I had used the "Boot Info Script" to produce the "RESULTS.txt" and paste it below.
   
   Could anyone tell me what's wrong with my server, and how to solve the problem?

   Many thanks in advance!

----------------------------- Begin of  RESULTS.txt  -----------------------------------------------

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /grub.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

ee-root': _______________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

ee-swap_1': _____________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders, total 41943040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       499,711       497,664  83 Linux
/dev/sda2             501,758    41,940,991    41,439,234   5 Extended
/dev/sda5             501,760    41,940,991    41,439,232  8e Linux LVM


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/ee-root ef97e75a-f396-414e-95fa-c03bb9a1c491   ext4       
/dev/mapper/ee-swap_1 278c3bf6-ca57-4cc8-8ade-cdc45d2947c8   swap       
/dev/sda1        ed4f4ea4-0d72-42fa-962f-ec64328a1116   ext2       
/dev/sda5        LspBW7-uI2C-kXnt-Jlo0-Qcad-uuHW-dH1mCo LVM2_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
ee-root
ee-swap_1
control

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/ee-root /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /boot                    ext2       (rw)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on ee-root'


Unknown BootLoader on ee-swap_1'



=============================== StdErr Messages: ===============================

  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/ee-root': No such file or directory
hexdump: /dev/mapper/ee-root': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/ee-swap_1': No such file or directory
hexdump: /dev/mapper/ee-swap_1': No such file or directory

----------------------------- End of  RESULTS.txt  ---------------------------------------------

---

### Post by dino99 on 2012-07-15
is it the same problem when you try booting in recovery mode or with an other kernel ?

---

