---
title: "Ubuntu 16.04 &amp; Win7 dual-boot -&gt; cannot boot -&gt; grub rescue"
date: 2017-07-18
forum: Installation &amp; Upgrades
---

### Post by alptaciroglu on 2017-07-18
Using Win7 & Ubuntu 16.04 as dualboot on my laptop. Had a problematic installation, partitioned drive and messed up booting. Was unable to boot using Fast Bios mode in the laptop, disable that everything works fine. Anyways, I thought I should clean up the mess. Merged several partitions, renamed them etc etc.. Now, I cannot boot in either Fast Bios or normal. Trying to fix this using a USB live stick which ended up working for several hours and no progress. Any help is appreciated.

Here is my bootinfoscript output: 
```

                Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 97 for .
 => Windows is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 0x4d8ae235
    Boot sector info:  Syslinux looks at sector 3170272 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the / 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

sdb: ___________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,419,615,854 1,419,409,007   7 NTFS / exFAT / HPFS
/dev/sda3       1,419,626,496 1,465,147,391    45,520,896  27 Hidden NTFS (Recovery Environment)


Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  64 1,431,648,539 1,431,648,476   7 NTFS / exFAT / HPFS
/dev/sdc2       1,431,658,494 1,465,147,391    33,488,898   f W95 Extended (LBA)
/dev/sdc5       1,431,658,496 1,465,147,391    33,488,896  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________
Disk /dev/sdd: 14.9 GiB, 16005464064 bytes, 31260672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             32    31,260,671    31,260,640   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2E5414585414255D                       ntfs       SYSTEM
/dev/sda2        84DEB33DDEB325F8                       ntfs       First Drive
/dev/sda3        8066BE7D66BE738E                       ntfs       SAMSUNG_REC
/dev/sdb                                                           
/dev/sdc1        01D2FFFDDDC46490                       ntfs       Second Drive
/dev/sdc5        957a0007-90c4-4b96-a5d5-04ff395a40ec   swap       
/dev/sdd1        771E-15AA                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=========================== sdd1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdd1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash ---

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash ---

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash ---

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---

label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---

label ubnentry8
menu label OEM install (for manufacturers)
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---

label ubnentry9
menu label Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash ---

--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdd1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdd1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc2



=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-Zj2iAt6W/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-Zj2iAt6W/Tmp_Log: No such file or directory
hexdump: /dev/sdc2: No such device or address
hexdump: /dev/sdc2: No such device or address
cat: /tmp/BootInfo-Zj2iAt6W/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-Zj2iAt6W/Tmp_Log: No such file or directory
```

---

### Post by oldfred on 2017-07-18
Better to post link from Boot-Repair for its summary report. It also uses bootinfoscript for part of its report and the version of bootinfoscript is an updated fork.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You are not showing sdb drive?
You have grub in MBR of sda, which looks like a Windows drive.
And swap in sdc5, but no Linux partitions shown.

Does BIOS show sdb?

---

### Post by alptaciroglu on 2017-07-18
Thank you for quick reply.

I checked in BIOS but I think I only have an unallocated space in the  sdb. Might it be possible that I wiped linux distribution trying to fix  my partitions? And if that's the case would it be possible to save some  data from it?

I tried running Boot repair but I think while I was trying to fix, I  changed the root from grub which caused some post-errors. Couldn't get a  link from Paste.org but here is the updated Boot-Repair. It  unfortunately didn't fix my issue

 Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]

```

============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ntfs part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Windows 2000/XP/2003 is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 0x4d8ae235
    Boot sector info:  Syslinux looks at sector 3170272 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the / 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

sdb: ___________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,419,615,854 1,419,409,007   7 NTFS / exFAT / HPFS
/dev/sda3       1,419,626,496 1,465,147,391    45,520,896  27 Hidden NTFS (Recovery Environment)


Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             64 1,431,648,539 1,431,648,476   7 NTFS / exFAT / HPFS
/dev/sdc2       1,431,658,494 1,465,147,391    33,488,898   f W95 Extended (LBA)
/dev/sdc5       1,431,658,496 1,465,147,391    33,488,896  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________
Disk /dev/sdd: 14.9 GiB, 16005464064 bytes, 31260672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             32    31,260,671    31,260,640   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2E5414585414255D                       ntfs       SYSTEM
/dev/sda2        84DEB33DDEB325F8                       ntfs       First Drive
/dev/sda3        8066BE7D66BE738E                       ntfs       SAMSUNG_REC
/dev/sdb                                                           
/dev/sdc1        01D2FFFDDDC46490                       ntfs       Second Drive
/dev/sdc5        957a0007-90c4-4b96-a5d5-04ff395a40ec   swap       
/dev/sdd1        771E-15AA                              vfat       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jul 18 23:59 ata-Hitachi_HTS727575A9E364_J3740084HBE3GE -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 18 23:59 ata-Hitachi_HTS727575A9E364_J3740084HBE3GE-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jul 18 23:59 ata-Hitachi_HTS727575A9E364_J3740084HBE3GE-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jul 18 23:59 ata-Hitachi_HTS727575A9E364_J3740084HBE3GE-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 Jul 18 23:59 ata-Hitachi_HTS727575A9E364_J3740084HJE98E -> ../../sdc
lrwxrwxrwx 1 root root 10 Jul 18 23:59 ata-Hitachi_HTS727575A9E364_J3740084HJE98E-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Jul 18 23:59 ata-Hitachi_HTS727575A9E364_J3740084HJE98E-part2 -> ../../sdc2
lrwxrwxrwx 1 root root 10 Jul 18 23:59 ata-Hitachi_HTS727575A9E364_J3740084HJE98E-part5 -> ../../sdc5
lrwxrwxrwx 1 root root  9 Jul 18 23:59 ata-SanDisk_iSSD_P4_8GB_121600105998 -> ../../sdb
lrwxrwxrwx 1 root root  9 Jul 18 23:59 ata-TSSTcorp_DVDWBD_TS-LB23D_R8BU6GRC2008L5 -> ../../sr0
lrwxrwxrwx 1 root root  9 Jul 18 23:59 usb-SanDisk_Cruzer_Blade_4C531001640610113031-0:0 -> ../../sdd
lrwxrwxrwx 1 root root 10 Jul 18 23:59 usb-SanDisk_Cruzer_Blade_4C531001640610113031-0:0-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  9 Jul 18 23:59 wwn-0x5000cca68cd348ce -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 18 23:59 wwn-0x5000cca68cd348ce-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jul 18 23:59 wwn-0x5000cca68cd348ce-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jul 18 23:59 wwn-0x5000cca68cd348ce-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 Jul 18 23:59 wwn-0x5000cca68cd58f5d -> ../../sdc
lrwxrwxrwx 1 root root 10 Jul 18 23:59 wwn-0x5000cca68cd58f5d-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Jul 18 23:59 wwn-0x5000cca68cd58f5d-part2 -> ../../sdc2
lrwxrwxrwx 1 root root 10 Jul 18 23:59 wwn-0x5000cca68cd58f5d-part5 -> ../../sdc5
lrwxrwxrwx 1 root root  9 Jul 18 23:59 wwn-0x5001b4475b835a0e -> ../../sdb

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /cdrom                   vfat        (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdd1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed  boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdd1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash ---

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash ---

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash ---

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---

label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---

label ubnentry8
menu label OEM install (for manufacturers)
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed  boot=casper only-ubiquity quiet splash oem-config/enable=true ---

label ubnentry9
menu label Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash ---

--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdd1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1

============== sdd1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc2



=============================== StdErr Messages: ===============================

hexdump: /dev/sdc2: No such device or address
hexdump: /dev/sdc2: No such device or address
File descriptor 9 (/proc/17980/mounts) leaked on lvs invocation. Parent PID 25968: bash
File descriptor 63 (pipe:[144406]) leaked on lvs invocation. Parent PID 25968: bash

ADDITIONAL INFORMATION :
=================== log of boot-repair 2017-07-18__23h58 ===================
boot-repair version : 4ppa40
boot-sav version : 4ppa40
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa40
boot-repair is executed in live-session (Ubuntu 16.04.2 LTS, xenial, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
ls: cannot access '/home/usr/.config': No such file or directory
sdb may have broken partition table.
Partition 2 does not start on physical sector boundary.

=================== os-prober:


=================== blkid:
/dev/sda1: LABEL="SYSTEM" UUID="2E5414585414255D" TYPE="ntfs" PARTUUID="cd24a570-01"
/dev/sda2: LABEL="First Drive" UUID="84DEB33DDEB325F8" TYPE="ntfs" PARTUUID="cd24a570-02"
/dev/sda3: LABEL="SAMSUNG_REC" UUID="8066BE7D66BE738E" TYPE="ntfs" PARTUUID="cd24a570-03"
/dev/sdc1: LABEL="Second Drive" UUID="01D2FFFDDDC46490" TYPE="ntfs" PARTUUID="92cda70e-01"
/dev/sdd1: UUID="771E-15AA" TYPE="vfat"
/dev/loop0: TYPE="squashfs"
/dev/sdc5: UUID="957a0007-90c4-4b96-a5d5-04ff395a40ec" TYPE="swap" PARTUUID="92cda70e-05"
/dev/sdb: PTUUID="085500a9" PTTYPE="dos"

Windows not detected by os-prober on sda2.
Partition 2 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
=================== No kernel in /mnt/boot-sav/sda2/boot:
grub_old


ls /sys/firmware/efi/vars :  WdtPersistentData-78ce2354-cfbc-4643-aeba-07a27fa892bf,UsbSupport-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,USB_POINT-8be4df61-93ca-11d2-aa0d-00e098032b8c,UsbMassDevValid-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,UsbMassDevNum-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,Timeout-8be4df61-93ca-11d2-aa0d-00e098032b8c,TdtAdvancedSetupDataVar-7b77fb8b-1e0d-4d7e-953f-3980a261e076,StdDefaults-4599d26f-1a11-49b8-b91f-858745cff824,SetupSnbPpmFeatures-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,SetupPlatformData-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,Setup-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,SetupDptfFeatures-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,SecVolatileData-9d07a422-9e73-433c-8c00-f778e63d3f0f,SecSleepType-8be4df61-93ca-11d2-aa0d-00e098032b8c,SecSaveD29Usb-8be4df61-93ca-11d2-aa0d-00e098032b8c,SecSaveD26Usb-8be4df61-93ca-11d2-aa0d-00e098032b8c,SecSaveBootMode-8be4df61-93ca-11d2-aa0d-00e098032b8c,SecPrevTP-8be4df61-93ca-11d2-aa0d-00e098032b8c,SecHddInfo4PowerOff-6d4a284d-b3a4-4c96-8ceb-fa7359e7ed5d,SecFrcLcdType-8be4df61-93ca-11d2-aa0d-00e098032b8c,SECBootOpt-8be4df61-93ca-11d2-aa0d-00e098032b8c,SecBiosUpdateFlag-8be4df61-93ca-11d2-aa0d-00e098032b8c,ScramblerBaseSeed-87f22dcb-7304-4105-bb7c-317143ccc23b,SbAslBufferPtrVar-01f33c25-764d-43ea-aeea-6b5a41f3f3e8,SaPegData-c4975200-64f1-4fb6-9773-f6a9f89d985e,S3SS-4bafc2b4-02dc-4104-b236-d6f1b98d9e84,RecoveryEntry-8be4df61-93ca-11d2-aa0d-00e098032b8c,PreviousMemoryTypeInformation-4c19049f-4137-4dd3-9c10-8b97a83ffdfa,PNP0501_0_VV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0501_0_NV-560bf58a-1e0d-4d7e-953f-2980a261e031,PlatformLangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c,PlatformLang-8be4df61-93ca-11d2-aa0d-00e098032b8c,PchS3Peim-e6c2f70a-b604-4877-85ba-deec89e117eb,PchInit-e6c2f70a-b604-4877-85ba-deec89e117eb,OldLegacyDevOrder-a56074db-65fe-45f7-bd21-2d2bdd8e9652,OemCpuData-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,NvRamSpdMap-717fc150-abd9-4614-8015-0b3323eab95c,new_var,NetworkStackVar-d1405d16-7afc-4695-bb12-41459d3695a2,NBPlatformData-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,MrcS3Resume-87f22dcb-7304-4105-bb7c-317143ccc23b,MonotonicCounter-8be4df61-93ca-11d2-aa0d-00e098032b8c,MokListRT-605dab50-e046-4300-abb6-3dd810dd8b23,MemCeil.-8be4df61-93ca-11d2-aa0d-00e098032b8c,LegacySabiBuffPtr-8be4df61-93ca-11d2-aa0d-00e098032b8c,LegacyDevOrder-a56074db-65fe-45f7-bd21-2d2bdd8e9652,LangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c,Lang-8be4df61-93ca-11d2-aa0d-00e098032b8c,KBDBacklitLvl-8be4df61-93ca-11d2-aa0d-00e098032b8c,IccAdvancedSetupDataVar-7b77fb8b-1e0d-4d7e-953f-3980a261e077,HobRomImage-dde1bc72-d45e-4209-ab85-14462d2f5074,HddChkCount-8be4df61-93ca-11d2-aa0d-00e098032b8c,GnvsAreaVar-8be4df61-93ca-11d2-aa0d-00e098032b8c,FPDT_Variable-8be4df61-93ca-11d2-aa0d-00e098032b8c,FastLegacyBootOption-b540a530-6978-4da7-91cb-7207d764d262,FacsHwSigValue-8e3fd961-d300-4773-8777-73c4c9a6022b,ErrOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ErrOut-8be4df61-93ca-11d2-aa0d-00e098032b8c,EnteringSetupLogging-8e3fd961-d300-4773-8777-73c4c9a6022b,DriverHlthEnable-0885f288-418c-4be1-a6af-8bad61da08fe,DriverHealthCount-7459a7d4-6533-4480-bba7-79e25a4443c9,del_var,DefaultLegacyDevOrder-3c4ead08-45ae-4315-8d15-a60eaa8caf69,DefaultBootOrder-45cf35f6-0d6e-4d04-856a-0370a5b16f53,CountForPDate-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConOut-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConInDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConIn-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootRecoveryMethod-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootOrder-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootOptionSupport-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootCurrent-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0005-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0004-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0003-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0002-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0001-8be4df61-93ca-11d2-aa0d-00e098032b8c,AMITSESetup-c811fa38-42c8-4579-a9bb-60e94eddfb34,AcpiGlobalVariable-af9ffd67-ec10-488a-9dfc-6cbf5ee22c2e,
Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

=================== efibootmgr -v
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0004,0005,0002,0003,0001
Boot0001* Hitachi HTS727575A9E364    BBS(HD,,0x0)AMBO
Boot0002* Hitachi HTS727575A9E364    BBS(HD,,0x0)AMBO
Boot0003* TSSTcorp DVDWBD TS-LB23D    BBS(CDROM,,0x0)AMBO
Boot0004* UEFI: SanDisk    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(4,0)/HD(1,MBR,0x0,0x20,0x1dcffe0)AMBO
Boot0005* SanDisk    BBS(USB,,0x0)AMBO

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot maybe enabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,     part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,     no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,     nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,     standard,    not-far,    /media/ubuntu/SYSTEM.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-kernel,    is-os,    not--efi--part,     part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,     no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,     nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,     standard,    farbios,    /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,     part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,     recovery-or-hidden,    bootmgr,    is-winboot,    nopakmgr,     nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,     standard,    farbios,    /mnt/boot-sav/sda3.
sdc1    : sdc,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,     part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,     no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,     nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,     standard,    farbios,    /mnt/boot-sav/sdc1.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sdc    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    64 sectors * 512 bytes


=================== parted -l:

Model: ATA Hitachi HTS72757 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size    Type     File system  Flags
1      1049kB  106MB  105MB   primary  ntfs         boot
2      106MB   727GB  727GB   primary  ntfs
3      727GB   750GB  23.3GB  primary  ntfs         diag


Model: ATA SanDisk iSSD P4 (scsi)
Disk /dev/sdb: 8012MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start  End  Size  Type  File system  Flags


Model: ATA Hitachi HTS72757 (scsi)
Disk /dev/sdc: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size    Type      File system     Flags
1      32.8kB  733GB  733GB   primary   ntfs            boot
2      733GB   750GB  17.1GB  extended                  lba
5      733GB   750GB  17.1GB  logical   linux-swap(v1)


Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sdd: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  16.0GB  16.0GB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:750GB:scsi:512:4096:msdos:ATA Hitachi HTS72757:;
1:1049kB:106MB:105MB:ntfs::boot;
2:106MB:727GB:727GB:ntfs::;
3:727GB:750GB:23.3GB:ntfs::diag;

BYT;
/dev/sdb:8012MB:scsi:512:512:msdos:ATA SanDisk iSSD P4:;

BYT;
/dev/sdc:750GB:scsi:512:4096:msdos:ATA Hitachi HTS72757:;
1:32.8kB:733GB:733GB:ntfs::boot;
2:733GB:750GB:17.1GB:::lba;
5:733GB:750GB:17.1GB:linux-swap(v1)::;

BYT;
/dev/sdd:16.0GB:scsi:512:512:msdos:SanDisk Cruzer Blade:;
1:16.4kB:16.0GB:16.0GB:fat32::boot, lba;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sdd   disk           14.9G
sdd1  part vfat      14.9G
sdb   disk            7.5G
sr0   rom            1024M
loop0 loop squashfs   1.4G
sdc   disk          698.7G
sdc5  part swap        16G
sdc1  part ntfs     682.7G Second Drive
sda   disk          698.7G
sda2  part ntfs     676.8G First Drive
sda3  part ntfs      21.7G SAMSUNG_REC
sda1  part ntfs       100M SYSTEM

KNAME ROTA RO RM STATE   MOUNTPOINT
sdd      1  0  1 running
sdd1     1  0  1         /cdrom
sdb      0  0  0 running
sr0      1  0  1 running
loop0    1  1  0         /rofs
sdc      1  0  0 running
sdc5     1  0  0         [SWAP]
sdc1     1  0  0         /mnt/boot-sav/sdc1
sda      1  0  0 running
sda2     1  0  0         /mnt/boot-sav/sda2
sda3     1  0  0         /mnt/boot-sav/sda3
sda1     1  0  0         /media/ubuntu/SYSTEM


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8184972k,nr_inodes=2046243,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1640112k,mode=755)
/dev/sdd1 on /cdrom type vfat  (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
aufs on / type aufs (rw,noatime,si=aa81a8de31ddf98a)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup  (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs  (rw,relatime,fd=25,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=10595)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=1640112k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sda1 on /media/ubuntu/SYSTEM type fuseblk  (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdc1 on /mnt/boot-sav/sdc1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset badblocks bdi capability  dev device discard_alignment events events_async events_poll_msecs  ext_range holders inflight integrity power queue range removable ro sda1  sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset badblocks bdi capability  dev device discard_alignment events events_async events_poll_msecs  ext_range holders inflight integrity power queue range removable ro size  slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset badblocks bdi capability  dev device discard_alignment events events_async events_poll_msecs  ext_range holders inflight integrity power queue range removable ro sdc1  sdc2 sdc5 size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset badblocks bdi capability  dev device discard_alignment events events_async events_poll_msecs  ext_range holders inflight integrity power queue range removable ro sdd1  size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset badblocks bdi capability  dev device discard_alignment events events_async events_poll_msecs  ext_range holders inflight integrity power queue range removable ro size  slaves stat subsystem trace uevent
/dev (filtered):  agpgart audio audio1 audio2 audio3 audioctl autofs  block bsg btrfs-control bus cdrom cdrw char console core cpu  cpu_dma_latency cuse disk dri drm_dp_aux0 drm_dp_aux1 dsp dsp1 dsp2 dsp3  dvd dvdrw ecryptfs fb0 fb1 fb2 fb3 fb4 fb5 fb6 fb7 fd full fuse hidraw0  hpet hugepages hwrng i2c-0 i2c-1 i2c-10 i2c-11 i2c-12 i2c-13 i2c-2  i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 initctl input kmem kmsg kvm  lightnvm log mapper mcelog media0 mei0 mem memory_bandwidth midi0 midi00  midi01 midi02 midi03 midi1 midi2 midi3 mixer mixer1 mixer2 mixer3  mpu401data mpu401stat mqueue net network_latency network_throughput null  port ppp psaux ptmx pts random rfkill rmidi0 rmidi1 rmidi2 rmidi3 rtc  rtc0 sda sda1 sda2 sda3 sdb sdc sdc1 sdc2 sdc5 sdd sdd1 sequencer sg0  sg1 sg2 sg3 sg4 shm smpte0 smpte1 smpte2 smpte3 snapshot snd sndstat sr0  stderr stdin stdout uhid uinput urandom userio v4l vfio vga_arbiter  vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 1f 03 00 00 00 00 00  |................|
00000030  55 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U!..............|
00000040  f6 00 00 00 01 00 00 00  5d 25 14 54 58 14 54 2e  |........]%.TX.T.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 03 00  |........?....(..|
00000020  00 00 00 00 80 00 80 00  6e 76 9a 54 00 00 00 00  |........nv.T....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  f8 25 b3 de 3d b3 de 84  |.........%..=...|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 c8 9d 54  |........?......T|
00000020  00 00 00 00 80 00 80 00  ff 97 b6 02 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  8e 73 be 66 7d be 66 80  |.........s.f}.f.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sdc1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 40 00 00 00  |........?...@...|
00000020  00 00 00 00 80 00 80 00  db 38 55 55 00 00 00 00  |.........8UU....|
00000030  03 00 00 00 00 00 00 00  8d 53 55 05 00 00 00 00  |.........SU.....|
00000040  f6 00 00 00 01 00 00 00  90 64 c4 dd fd ff d2 01  |.........d......|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200
Partition 2 does not start on physical sector boundary.

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.9G     0  7.9G   0% /dev
tmpfs          tmpfs     1.6G  9.5M  1.6G   1% /run
/dev/sdd1      vfat       15G  1.6G   14G  11% /cdrom
/dev/loop0     squashfs  1.4G  1.4G     0 100% /rofs
aufs           aufs      7.9G  3.0G  4.9G  39% /
tmpfs          tmpfs     7.9G   36M  7.8G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.9G     0  7.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     7.9G  1.3M  7.9G   1% /tmp
tmpfs          tmpfs     1.6G   92K  1.6G   1% /run/user/999
/dev/sda1      fuseblk   100M   28M   73M  28% /media/ubuntu/SYSTEM
/dev/sda2      fuseblk   677G  441G  237G  66% /mnt/boot-sav/sda2
/dev/sda3      fuseblk    22G   21G  948M  96% /mnt/boot-sav/sda3
/dev/sdc1      fuseblk   683G   86M  683G   1% /mnt/boot-sav/sdc1

=================== fdisk -l:
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1497772032 bytes, 2925336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xcd24a570

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048     206847     204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2           206848 1419615854 1419409007 676.8G  7 HPFS/NTFS/exFAT
/dev/sda3       1419626496 1465147391   45520896  21.7G 27 Hidden NTFS WinRE


Disk /dev/sdb: 7.5 GiB, 8012390400 bytes, 15649200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x085500a9




Disk /dev/sdc: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x92cda70e

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdc1  *            64 1431648539 1431648476 682.7G  7 HPFS/NTFS/exFAT
/dev/sdc2       1431658494 1465147391   33488898    16G  f W95 Ext'd (LBA)
/dev/sdc5       1431658496 1465147391   33488896    16G 82 Linux swap / Solaris



Disk /dev/sdd: 14.9 GiB, 16005464064 bytes, 31260672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdd1  *       32 31260671 31260640 14.9G  c W95 FAT32 (LBA)


No OS or WinEFI system
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
No OS or WinEFI system


=================== Default settings of Boot Repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems  fix-windows-boot


=================== User settings
The settings chosen by the user will not act on the MBR.
Additional repair will be performed:  repair-filesystems  fix-windows-boot


Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var

ntfsfix /dev/sda1
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
Checking the alternate boot sector... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully.

ntfsfix /dev/sda2
Refusing to operate on read-write mounted device /dev/sda2.

ntfsfix /dev/sda3
Refusing to operate on read-write mounted device /dev/sda3.

ntfsfix /dev/sdc1
Refusing to operate on read-write mounted device /dev/sdc1.
Quantity of real Windows: 1

Boot successfully repaired.

You can now reboot your computer.

```

---

### Post by efflandt on 2017-07-18
You should use code tags around large blocks of data, like your first post here, not quote tags or whatever you used around last post.

It appears that although you have grub on the mbr of your first drive /dev/sda and Linux swap on /dev/sdc5 (a logical partition in extended partition /dev/sdc2, you have no Linux partition or any /boot/grub on any hard drive, and therefore no grub menu to boot anything. /dev/sdb is apparently an 8 GB Sandisk device with msdos partition table, but no partitions on it (is that an SD card in a slot or something else?).

If you have a bootable Windows DVD you could do: **bootrec /fixmbr**

Otherwise you could use a live/install system write a syslinux mbr.bin to the mbr of /dev/sda to restore a standard mbr (assuming path to mbr.bin is same as an installed system):```
sudo dd bs=440 count=1 conv=notrunc if=/usr/lib/syslinux/mbr/mbr.bin of=/dev/sda
```Doing either of those 2 things should allow you to boot Windows as long as it is not corrupted. Although, since bootrepair says "The settings chosen by the user will not act on the MBR." maybe it has a setting to restore a standard mbr (under MBR Options?}. I have not used bootrepair.

Then you could figure out if or where you want to install Ubuntu. Since some occasional Win7 updates can fail if it is not in command of its boot with standard mbr, and you have 2 hard drives, I would suggest either using Windows own Disk Management to shrink the NTFS partition on /dev/sdc to leave unallocated space for Linux, or use the entire /dev/sdc for Linux, depending upon what you are going to do. You would not normally need that entire drive for Linux unless you intend to do a lot of Steam gaming ("one" Steam game I recently installed was a 26 GB compressed download thant required 42 GB disk space). In either case, I would use **Other** during partitioning part of Ubuntu install to put whatever partition(s) on /dev/sdc and specifically put grub in mbr of /dev/sdc (drop down list at bottom of partitioning screen?). Then set your BIOS to boot your 2nd drive with grub normally, but if a Win7 update fails during its reboot, temporary switch BIOS to boot your 1st (Win7) drive. This all assumes that you are using legacy BIOS because I do not see any sign of using UEFI.

---

### Post by oldfred on 2017-07-18
It is not even showing a partition table on sdb.
I would restore a Windows boot loader to sda, you can use Boot-Repair for that, but chkdsk or other Windows repairs will need a Windows repair flash drive, if directly booting Windows from sda and f8 does not get you into Windows internal repair console.

You can see if testdisk or parted rescue shows partitions on sdb.
       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[URL="http://www.cgsecurity.org/wiki/TestDisk"]http://www.cgsecurity.org/wiki/TestDisk
[/URL]
 [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) 

This was for where Windows rewrote partition table on upgrade and removed the Linux logical partition. If you know partition start & end that would help a lot.

 Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405) 

[URL="http://www.cgsecurity.org/wiki/TestDisk"]
[/URL]

---

### Post by alptaciroglu on 2017-07-19
Thank you very much for your help. Your time is highly appreciated. Anyways, I was able to recover my all of my data lost in the removed Linux partition using TestDisk and then I had no reason not to purge the hard drive and reinstall Ubuntu. Then I was able to do  dual-boot using BootRepair within newly installed Ubuntu. 

Dual-boot works fine just with a small exception. I do not have an urgent issue anymore, but if you manage to spare some time for this, I would appreciate it. 

I cannot dual-boot when Fast Bios mode is activated. When deactivated, everything works fine. 

Here is the BootRepair Log;

```
ADDITIONAL INFORMATION :

=================== log of boot-repair 2017-07-19__16h29 ===================

boot-repair version : 4ppa40

boot-sav version : 4ppa40

glade2script version : 3.2.3~ppa1

boot-sav-extra version : 4ppa40

boot-repair is executed in installed-session (Ubuntu 16.04.2 LTS, xenial, Ubuntu, x86_64)

CPU op-mode(s):        32-bit, 64-bit

BOOT_IMAGE=/boot/vmlinuz-4.8.0-36-generic root=UUID=a12ffa7d-e979-45a3-83ce-fb426a3d1c08 ro quiet splash vt.handoff=7

sdb may have broken partition table.

sdb may have broken partition table.

Unmount sda2 from /media/alp/First Drive to avoid space incompatibilities

Partition 2 does not start on physical sector boundary.



=================== os-prober:

/dev/sdc6:The OS now in use - Ubuntu 16.04.2 LTS CurrentSession:linux

/dev/sda1:Windows 7 (loader):Windows:chain

/dev/sda3:Windows Recovery Environment (loader):Windows1:chain



=================== blkid:

/dev/sda1: LABEL="SYSTEM" UUID="2E5414585414255D" TYPE="ntfs" PARTUUID="cd24a570-01"

/dev/sda2: LABEL="First Drive" UUID="84DEB33DDEB325F8" TYPE="ntfs" PARTUUID="cd24a570-02"

/dev/sda3: LABEL="SAMSUNG_REC" UUID="8066BE7D66BE738E" TYPE="ntfs" PARTUUID="cd24a570-03"

/dev/sdc1: LABEL="Second Drive" UUID="01D2FFFDDDC46490" TYPE="ntfs" PARTUUID="92cda70e-01"

/dev/sdc5: UUID="957a0007-90c4-4b96-a5d5-04ff395a40ec" TYPE="swap" PARTUUID="92cda70e-05"

/dev/sdc6: UUID="a12ffa7d-e979-45a3-83ce-fb426a3d1c08" TYPE="ext4" PARTUUID="92cda70e-06"

/dev/sdd1: UUID="771E-15AA" TYPE="vfat"

/dev/sdb: PTUUID="085500a9" PTTYPE="dos"





2 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.



Windows not detected by os-prober on sda2.

Partition 2 does not start on physical sector boundary.

Partition 2 does not start on physical sector boundary.



=================== /etc/grub.d/ :

drwxr-xr-x  2 root root    4096 Jul 19 16:15 grub.d

total 80

-rwxr-xr-x 1 root root  9791 Jan 13  2017 00_header

-rwxr-xr-x 1 root root  6258 Mar 15  2016 05_debian_theme

-rwxr-xr-x 1 root root 12512 May 20 21:27 10_linux

-rwxr-xr-x 1 root root 11082 Jan 13  2017 20_linux_xen

-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+

-rwxr-xr-x 1 root root 11692 Jan 13  2017 30_os-prober

-rwxr-xr-x 1 root root  1418 Jan 13  2017 30_uefi-firmware

-rwxr-xr-x 1 root root   214 Jan 13  2017 40_custom

-rwxr-xr-x 1 root root   216 Jan 13  2017 41_custom

-rw-r--r-- 1 root root   483 Jan 13  2017 README









=================== /etc/default/grub :



# If you change this file, run 'update-grub' afterwards to update

# /boot/grub/grub.cfg.

# For full documentation of the options in this file, see:

#   info -f grub -n 'Simple configuration'



GRUB_DEFAULT=0

#GRUB_HIDDEN_TIMEOUT=0

GRUB_HIDDEN_TIMEOUT_QUIET=true

GRUB_TIMEOUT=10

GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

GRUB_CMDLINE_LINUX=""



# Uncomment to enable BadRAM filtering, modify to suit your needs

# This works with Linux (no patch required) and with any kernel that obtains

# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)

#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"



# Uncomment to disable graphical terminal (grub-pc only)

#GRUB_TERMINAL=console



# The resolution used on graphical terminal

# note that you can use only modes which your graphic card supports via VBE

# you can see them in real GRUB with the command `vbeinfo'

#GRUB_GFXMODE=640x480



# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux

#GRUB_DISABLE_LINUX_UUID=true



# Uncomment to disable generation of recovery mode menu entries

#GRUB_DISABLE_RECOVERY="true"



# Uncomment to get a beep at grub start

#GRUB_INIT_TUNE="480 440 1"







/boot/grub/menu.lst detected

=================== No kernel in /mnt/boot-sav/sda2/boot:

grub_old





=================== No kernel in /media/alp/771E-15AA/boot:

grub







=================== UEFI/Legacy mode:

This installed-session is not in EFI-mode.

SecureBoot disabled.





=================== PARTITIONS & DISKS:

sdc6	: sdc,	not-sepboot,	grubenv-ok	grub2,	signed grub1 grub-pc ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	.

sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/media/alp/SYSTEM.

sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-kernel,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda2.

sda3	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda3.

sdc1	: sdc,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdc1.

sdd1	: sdd,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-kernel,	no-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/media/alp/771E-15AA.



sdc	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	64 sectors * 512 bytes

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	2048 sectors * 512 bytes

sdd	: not-GPT,	BIOSboot-not-needed,	has-correctEFI, 	liveusb,	no-os,	32 sectors * 512 bytes





=================== parted -l:



Model: ATA Hitachi HTS72757 (scsi)

Disk /dev/sda: 750GB

Sector size (logical/physical): 512B/4096B

Partition Table: msdos

Disk Flags:



Number  Start   End    Size    Type     File system  Flags

1      1049kB  106MB  105MB   primary  ntfs         boot

2      106MB   727GB  727GB   primary  ntfs

3      727GB   750GB  23.3GB  primary  ntfs         diag





Model: ATA SanDisk iSSD P4 (scsi)

Disk /dev/sdb: 8012MB

Sector size (logical/physical): 512B/512B

Partition Table: msdos

Disk Flags:



Number  Start  End  Size  Type  File system  Flags





Model: ATA Hitachi HTS72757 (scsi)

Disk /dev/sdc: 750GB

Sector size (logical/physical): 512B/4096B

Partition Table: msdos

Disk Flags:



Number  Start   End    Size    Type      File system     Flags

1      32.8kB  363GB  363GB   primary   ntfs            boot

2      363GB   750GB  387GB   extended                  lba

6      363GB   733GB  370GB   logical   ext4

5      733GB   750GB  17.1GB  logical   linux-swap(v1)





Model: SanDisk Cruzer Blade (scsi)

Disk /dev/sdd: 16.0GB

Sector size (logical/physical): 512B/512B

Partition Table: msdos

Disk Flags:



Number  Start   End     Size    Type     File system  Flags

1      16.4kB  16.0GB  16.0GB  primary  fat32        boot, lba



=================== parted -lm:



BYT;

/dev/sda:750GB:scsi:512:4096:msdos:ATA Hitachi HTS72757:;

1:1049kB:106MB:105MB:ntfs::boot;

2:106MB:727GB:727GB:ntfs::;

3:727GB:750GB:23.3GB:ntfs::diag;



BYT;

/dev/sdb:8012MB:scsi:512:512:msdos:ATA SanDisk iSSD P4:;



BYT;

/dev/sdc:750GB:scsi:512:4096:msdos:ATA Hitachi HTS72757:;

1:32.8kB:363GB:363GB:ntfs::boot;

2:363GB:750GB:387GB:::lba;

6:363GB:733GB:370GB:ext4::;

5:733GB:750GB:17.1GB:linux-swap(v1)::;



BYT;

/dev/sdd:16.0GB:scsi:512:512:msdos:SanDisk Cruzer Blade:;

1:16.4kB:16.0GB:16.0GB:fat32::boot, lba;



=================== lsblk:

KNAME TYPE FSTYPE   SIZE LABEL

sdd   disk         14.9G

sdd1  part vfat    14.9G

sdb   disk          7.5G

sr0   rom          1024M

sdc   disk        698.7G

sdc2  part            1K

sdc5  part swap      16G

sdc1  part ntfs     338G Second Drive

sdc6  part ext4   344.7G

sda   disk        698.7G

sda2  part ntfs   676.8G First Drive

sda3  part ntfs    21.7G SAMSUNG_REC

sda1  part ntfs     100M SYSTEM



KNAME ROTA RO RM STATE   MOUNTPOINT

sdd      1  0  1 running

sdd1     1  0  1         /media/alp/771E-15AA

sdb      0  0  0 running

sr0      1  0  1 running

sdc      1  0  0 running

sdc2     1  0  0

sdc5     1  0  0         [SWAP]

sdc1     1  0  0         /mnt/boot-sav/sdc1

sdc6     1  0  0         /

sda      1  0  0 running

sda2     1  0  0         /mnt/boot-sav/sda2

sda3     1  0  0         /mnt/boot-sav/sda3

sda1     1  0  0         /media/alp/SYSTEM





=================== mount:

sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)

proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)

udev on /dev type devtmpfs (rw,nosuid,relatime,size=8180012k,nr_inodes=2045003,mode=755)

devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)

tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1640244k,mode=755)

/dev/sdc6 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)

securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)

tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)

tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)

tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)

cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)

pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)

cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)

cgroup on /sys/fs/cgroup/blkio
 type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)

cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)

cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)

cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)

cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)

cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)

cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)

cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)

cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)

systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=31,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=10964)

mqueue on /dev/mqueue type mqueue (rw,relatime)

debugfs on /sys/kernel/debug type debugfs (rw,relatime)

hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)

tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)

fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)

tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1640244k,mode=700,uid=1000,gid=1000)

gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)

/dev/sdd1 on /media/alp/771E-15AA type vfat (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)

/dev/sda1 on /media/alp/SYSTEM type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)

/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)

/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)

/dev/sdc1 on /mnt/boot-sav/sdc1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)





=================== ls:

/sys/block/sda (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent

/sys/block/sdb (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent

/sys/block/sdc (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdc1 sdc2 sdc5 sdc6 size slaves stat subsystem trace uevent

/sys/block/sdd (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdd1 size slaves stat subsystem trace uevent

/sys/block/sr0 (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent

/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 drm_dp_aux1 dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hpet hugepages hwrng i2c-0 i2c-1 i2c-10 i2c-11 i2c-12 i2c-13 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 initctl input kmsg kvm lightnvm log mapper mcelog media0 mei0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdc sdc1 sdc2 sdc5 sdc6 sdd sdd1 sg0 sg1 sg2 sg3 sg4 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom userio v4l vfio vga_arbiter vhci vhost-net video0 zero

ls /dev/mapper:  control

ls: cannot access '': No such file or directory



=================== hexdump -n512 -C /dev/sda1

00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|

00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|

00000020  00 00 00 00 80 00 80 00  ff 1f 03 00 00 00 00 00  |................|

00000030  55 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U!..............|

00000040  f6 00 00 00 01 00 00 00  5d 25 14 54 58 14 54 2e  |........]%.TX.T.|

00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|

00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|

00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|

00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|

00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|

000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|

000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|

000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|

000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|

000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|

000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|

00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|

00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|

00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|

00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|

00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|

00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|

00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|

00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|

00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |

00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |

000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|

000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|

000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|

000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|

000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|

000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|

00000200



=================== hexdump -n512 -C /dev/sda2

00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|

00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 03 00  |........?....(..|

00000020  00 00 00 00 80 00 80 00  6e 76 9a 54 00 00 00 00  |........nv.T....|

00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|

00000040  f6 00 00 00 01 00 00 00  f8 25 b3 de 3d b3 de 84  |.........%..=...|

00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|

00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|

00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|

00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|

00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|

000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|

000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|

000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|

000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|

000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|

000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|

00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|

00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|

00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|

00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|

00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|

00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|

00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|

00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|

00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |

00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |

000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|

000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|

000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|

000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|

000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|

000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|

00000200



=================== hexdump -n512 -C /dev/sda3

00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|

00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 c8 9d 54  |........?......T|

00000020  00 00 00 00 80 00 80 00  ff 97 b6 02 00 00 00 00  |................|

00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|

00000040  f6 00 00 00 01 00 00 00  8e 73 be 66 7d be 66 80  |.........s.f}.f.|

00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|

00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|

00000070  54 46 53 75 15
 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|

00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|

00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|

000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|

000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|

000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|

000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|

000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|

000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|

00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|

00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|

00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|

00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|

00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|

00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|

00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|

00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|

00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |

00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |

000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|

000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|

000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|

000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|

000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|

000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|

00000200



=================== hexdump -n512 -C /dev/sdc1

00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|

00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 40 00 00 00  |........?...@...|

00000020  00 00 00 00 80 00 80 00  68 cb 40 2a 00 00 00 00  |........h.@*....|

00000030  03 00 00 00 00 00 00 00  b6 0c a4 02 00 00 00 00  |................|

00000040  f6 00 00 00 01 00 00 00  90 64 c4 dd fd ff d2 01  |.........d......|

00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|

00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|

00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|

00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|

00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|

000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|

000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|

000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|

000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|

000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|

000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|

00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|

00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|

00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|

00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|

00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|

00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|

00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|

00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|

00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|

00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|

000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|

000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|

000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|

000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|

000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|

000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|

00000200

ls sdd1/efi: /BOOT/grubx64.efi /BOOT/BOOTx64.EFI

ls sdd1: boot

casper

dists

EFI

install

isolinux

ldlinux.sys

md5sum.txt

menu.c32

pics

pool

preseed

README.diskdefines

refcard.pdf

RunSanDiskSecureAccess_Win.exe

SanDiskSecureAccess

syslinux.cfg

System Volume Information

ubnfilel.txt

ubninit

ubnkern

ubnpathl.txt  . Please report this message to boot.repair@gmail.com

ls: cannot access '/boot/efi/efi': No such file or directory

ls /boot/efi/efi :

Error efitmp. Please report this message to boot.repair@gmail.com



=================== hexdump -n512 -C /dev/sdd1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 20 26 00  |.X.SYSLINUX.. &.|

00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|

00000020  e0 ff dc 01 cd 1d 00 00  00 00 00 00 02 00 00 00  |................|

00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|

00000040  80 01 29 aa 15 1e 77 4e  4f 20 4e 41 4d 45 20 20  |..)...wNO NAME  |

00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|

00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|

00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|

00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||

00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP....U..u|

000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|

000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|

000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|

000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|

000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||

000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|

00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|

00000110  c6 06 45 7d 00 66 b8 e0  5f 30 00 66 ba 00 00 00  |..E}.f.._0.f....|

00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e cb e0 38 73  |...~...f.>$~..8s|

00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|

00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|

00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|

00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|

00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|

00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|

00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|

000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|

000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|

000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|

000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|

000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|

000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|

00000200

Partition 2 does not start on physical sector boundary.



=================== df -Th:



Filesystem     Type      Size  Used Avail Use% Mounted on

udev           devtmpfs  7.9G     0  7.9G   0% /dev

tmpfs          tmpfs     1.6G  9.5M  1.6G   1% /run

/dev/sdc6      ext4      340G  4.3G  318G   2% /

tmpfs          tmpfs     7.9G   60M  7.8G   1% /dev/shm

tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock

tmpfs          tmpfs     7.9G     0  7.9G   0% /sys/fs/cgroup

tmpfs          tmpfs     1.6G   52K  1.6G   1% /run/user/1000

/dev/sdd1      vfat       15G  1.6G   14G  11% /media/alp/771E-15AA

/dev/sda1      fuseblk   100M   28M   73M  28% /media/alp/SYSTEM

/dev/sda2      fuseblk   677G  441G  237G  66% /mnt/boot-sav/sda2

/dev/sda3      fuseblk    22G   21G  948M  96% /mnt/boot-sav/sda3

/dev/sdc1      fuseblk   339G   75M  338G   1% /mnt/boot-sav/sdc1



=================== fdisk -l:

Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes





Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes





Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes





Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes





Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes





Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes





Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size
 (minimum/optimal): 4096 bytes / 4096 bytes





Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes





Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes





Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes





Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes





Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes





Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes





Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes





Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes





Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes





Disk /dev/sda: 698.7 GiB, 750156374016 bytes, 1465149168 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disklabel type: dos

Disk identifier: 0xcd24a570



Device     Boot      Start        End    Sectors   Size Id Type

/dev/sda1  *          2048     206847     204800   100M  7 HPFS/NTFS/exFAT

/dev/sda2           206848 1419615854 1419409007 676.8G  7 HPFS/NTFS/exFAT

/dev/sda3       1419626496 1465147391   45520896  21.7G 27 Hidden NTFS WinRE





Disk /dev/sdb: 7.5 GiB, 8012390400 bytes, 15649200 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disklabel type: dos

Disk identifier: 0x085500a9









Disk /dev/sdc: 698.7 GiB, 750156374016 bytes, 1465149168 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disklabel type: dos

Disk identifier: 0x92cda70e



Device     Boot      Start        End   Sectors   Size Id Type

/dev/sdc1  *            64  708889513 708889450   338G  7 HPFS/NTFS/exFAT

/dev/sdc2        708890622 1465147391 756256770 360.6G  f W95 Ext'd (LBA)

/dev/sdc5       1431658496 1465147391  33488896    16G 82 Linux swap / Solaris

/dev/sdc6        708890624 1431658495 722767872 344.7G 83 Linux



Partition table entries are not in disk order.





Disk /dev/sdd: 14.9 GiB, 16005464064 bytes, 31260672 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disklabel type: dos

Disk identifier: 0x00000000



Device     Boot Start      End  Sectors  Size Id Type

/dev/sdd1  *       32 31260671 31260640 14.9G  c W95 FAT32 (LBA)





Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.

User choice: Is sdc (750GB) a removable disk? no







=================== Recommended repair

The default repair of the Boot-Repair utility will purge (in order to fix legacy files) and reinstall the grub2 of sdc6 into the MBRs of all disks (except USB without OS).

Grub-efi will not be selected by default because: no-win-efi

Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot





Quantity of real Windows: 1

apt-get -y --force-yes update

Purge the GRUB of sdc6

grub-pc available





The following package was automatically installed and is no longer required:

libc6-i386

Use 'sudo apt autoremove' to remove it.

The following additional packages will be installed:

grub-gfxpayload-lists grub2-common

The following packages will be REMOVED

grub

The following NEW packages will be installed

grub-gfxpayload-lists grub-pc grub2-common

0 to upgrade, 3 to newly install, 1 to remove and 254 not to upgrade.

W: --force-yes is deprecated, use one of the options starting with --allow instead.

DEBCHECK debOK, grub-pc

DEBCHECK debOK

shim-signed available

linux-signed-generic available

Please type: sudo dpkg --configure -ansudo apt-get install -fynsudo apt-get purge -y --force-yes grub*-common grub-common:i386 shim-signed linux-signed*



=================== /etc/grub.d/ :

drwxr-xr-x  2 root root    4096 Jul 19 16:30 grub.d

total 4

-rwxr-xr-x 1 root root 1992 Jan 28  2016 20_memtest86+





ls: cannot access '/usr/share/boot-sav': No such file or directory





=================== /etc/default/grub :



# If you change this file, run 'update-grub' afterwards to update

# /boot/grub/grub.cfg.

# For full documentation of the options in this file, see:

#   info -f grub -n 'Simple configuration'



GRUB_DEFAULT=0

#GRUB_HIDDEN_TIMEOUT=0

GRUB_HIDDEN_TIMEOUT_QUIET=true

GRUB_TIMEOUT=10

GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

GRUB_CMDLINE_LINUX=""



# Uncomment to enable BadRAM filtering, modify to suit your needs

# This works with Linux (no patch required) and with any kernel that obtains

# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)

#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"



# Uncomment to disable graphical terminal (grub-pc only)

#GRUB_TERMINAL=console



# The resolution used on graphical terminal

# note that you can use only modes which your graphic card supports via VBE

# you can see them in real GRUB with the command `vbeinfo'

#GRUB_GFXMODE=640x480



# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux

#GRUB_DISABLE_LINUX_UUID=true



# Uncomment to disable generation of recovery mode menu entries

#GRUB_DISABLE_RECOVERY="true"



# Uncomment to get a beep at grub start

#GRUB_INIT_TUNE="480 440 1"







/boot/grub/menu.lst detected

ls: cannot access '/media/alp/SYSTEM/': No such file or directory

=================== No kernel in /media/alp/771E-15AA/boot:

grub





Then type: sudo apt-get install -y --force-yes grub-pc os-prober linux-generic



=================== /etc/grub.d/ :

drwxr-xr-x  2 root root    4096 Jul 19 16:33 grub.d

drwxr-xr-x  2 root root    4096 Jul 19 16:30 grub.d.bak

total 76

-rwxr-xr-x 1 root root  9791 May 20 21:27 00_header

-rwxr-xr-x 1 root root  6258 Mar 15  2016 05_debian_theme

-rwxr-xr-x 1 root root 12512 May 20 21:27 10_linux

-rwxr-xr-x 1 root root 11082 May 20 21:27 20_linux_xen

-rwxr-xr-x 1 root root 11692 May 20 21:27 30_os-prober

-rwxr-xr-x 1 root root  1418 May 20 21:27 30_uefi-firmware

-rwxr-xr-x 1 root root   214 May 20 21:27 40_custom

-rwxr-xr-x 1 root root   216 May 20 21:27 41_custom

-rw-r--r-- 1 root root   483 May 20 21:27 README





ls: cannot access '/usr/share/boot-sav': No such file or directory





=================== /etc/default/grub :



# If you change this file, run 'update-grub' afterwards to update

# /boot/grub/grub.cfg.

# For full documentation of the options in this file, see:

#   info -f grub -n 'Simple configuration'



GRUB_DEFAULT=0

#GRUB_HIDDEN_TIMEOUT=0

GRUB_HIDDEN_TIMEOUT_QUIET=true

GRUB_TIMEOUT=10

GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

GRUB_CMDLINE_LINUX=""



# Uncomment to enable BadRAM filtering, modify to suit your needs

# This works with Linux (no patch required) and with any kernel that obtains

# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)

#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"



# Uncomment to disable graphical terminal (grub-pc only)

#GRUB_TERMINAL=console



# The resolution used on graphical terminal

# note that you can use only modes which your graphic card supports via VBE

# you can see them in real GRUB with the command `vbeinfo'

#GRUB_GFXMODE=640x480



# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux

#GRUB_DISABLE_LINUX_UUID=true



# Uncomment to disable generation of recovery mode menu entries

#GRUB_DISABLE_RECOVERY="true"



# Uncomment to get a beep at grub start

#GRUB_INIT_TUNE="480 440 1"







ls: cannot access '/media/alp/SYSTEM/': No such file or directory

=================== No kernel in /media/alp/771E-15AA/boot:

grub







=================== /etc/grub.d/ :

drwxr-xr-x  2 root root    4096 Jul 19 16:33 grub.d

drwxr-xr-x  2 root root    4096 Jul 19 16:30 grub.d.bak

total 76

-rwxr-xr-x 1 root root  9791 May 20 21:27 00_header

-rwxr-xr-x 1 root root  6258 Mar 15  2016 05_debian_theme

-rwxr-xr-x 1 root root 12512 May 20 21:27 10_linux

-rwxr-xr-x 1 root root 11082 May 20 21:27 20_linux_xen

-rwxr-xr-x 1 root root 11692 May 20 21:27 30_os-prober

-rwxr-xr-x 1 root root  1418 May 20 21:27 30_uefi-firmware

-rwxr-xr-x 1 root root   214 May 20 21:27 40_custom

-rwxr-xr-x 1 root root   216 May 20 21:27 41_custom

-rw-r--r-- 1 root root   483 May 20 21:27 README





ls: cannot access '/usr/share/boot-sav': No such file or directory





=================== /etc/default/grub :



# If you change this file, run 'update-grub' afterwards to update

# /boot/grub/grub.cfg.

# For full documentation of the options in this file, see:

#   info -f grub -n 'Simple configuration'



GRUB_DEFAULT=0

#GRUB_HIDDEN_TIMEOUT=0

GRUB_HIDDEN_TIMEOUT_QUIET=true

GRUB_TIMEOUT=10

GRUB_DISTRIBUTOR=`lsb_release
 -i -s 2> /dev/null || echo Debian`

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

GRUB_CMDLINE_LINUX=""



# Uncomment to enable BadRAM filtering, modify to suit your needs

# This works with Linux (no patch required) and with any kernel that obtains

# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)

#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"



# Uncomment to disable graphical terminal (grub-pc only)

#GRUB_TERMINAL=console



# The resolution used on graphical terminal

# note that you can use only modes which your graphic card supports via VBE

# you can see them in real GRUB with the command `vbeinfo'

#GRUB_GFXMODE=640x480



# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux

#GRUB_DISABLE_LINUX_UUID=true



# Uncomment to disable generation of recovery mode menu entries

#GRUB_DISABLE_RECOVERY="true"



# Uncomment to get a beep at grub start

#GRUB_INIT_TUNE="480 440 1"







ls: cannot access '/media/alp/SYSTEM/': No such file or directory

=================== No kernel in /media/alp/771E-15AA/boot:

grub







Reinstall the GRUB of sdc6 into all MBRs of disks with OS or not-USB



*******lspci -nnk | grep -iA3 vga

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF114M [GeForce GTX 675M] [10de:1212] (rev a1)

Subsystem: Samsung Electronics Co Ltd GF114M [GeForce GTX 675M] [144d:c0d0]

Kernel driver in use: nouveau

Kernel modules: nvidiafb, nouveau

*******



grub-install --version

grub-install (GRUB) 2.02~beta2-36ubuntu3.11,grub-install (GRUB) 2.



Reinstall the GRUB of sdc6 into the MBR of sda

Installing for i386-pc platform.

Installation finished. No error reported.

grub-install /dev/sda: exit code of grub-install /dev/sda:0



*******lspci -nnk | grep -iA3 vga

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF114M [GeForce GTX 675M] [10de:1212] (rev a1)

Subsystem: Samsung Electronics Co Ltd GF114M [GeForce GTX 675M] [144d:c0d0]

Kernel driver in use: nouveau

Kernel modules: nvidiafb, nouveau

*******



grub-install --version

grub-install (GRUB) 2.02~beta2-36ubuntu3.11,grub-install (GRUB) 2.



Reinstall the GRUB of sdc6 into the MBR of sdc

Installing for i386-pc platform.

Installation finished. No error reported.

grub-install /dev/sdc: exit code of grub-install /dev/sdc:0



update-grub

Generating grub configuration file ...

Found linux image: /boot/vmlinuz-4.8.0-36-generic

Found initrd image: /boot/initrd.img-4.8.0-36-generic

Found linux image: /boot/vmlinuz-4.4.0-83-generic

Found initrd image: /boot/initrd.img-4.4.0-83-generic

Found Windows 7 (loader) on /dev/sda1

Found Windows Recovery Environment (loader) on /dev/sda3

Unhide GRUB boot menu in sdc6/boot/grub/grub.cfg



Boot successfully repaired.



You can now reboot your computer.

Please do not forget to make your BIOS boot on sdc (750GB) disk!



The boot files of [The OS now in use - Ubuntu 16.04.2 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)


```

---

### Post by oldfred on 2017-07-19
UEFI/BIOS fast boot was (I thought) only on the newer UEFI systems. And that is different than Windows 8 or 10 fast start up which is really just hibernation. 
If Windows 7 then it only has separate full hibernation settings.

Grub only boots working Windows, or Windows that is not hibernated nor needs chkdsk. Why best to have Windows boot loader on Windows drive if multiple drives, so you can directly boot Windows. Windows 8 or 10 will regularly turn fast start up on updates.

Not sure if just BIOS setting why you would not be able to easily dual boot. But many systems have various settings that can cause issues.

With newer systems, the fast boot setting, assumes you have made no changes to system and skips the normal UEFI/BIOS scan of hardware & writing that info for operating system to use. It just jumps to booting.

---

