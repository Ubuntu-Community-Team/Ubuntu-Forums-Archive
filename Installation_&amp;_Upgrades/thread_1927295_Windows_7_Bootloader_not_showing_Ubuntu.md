---
title: "Windows 7 Bootloader not showing Ubuntu"
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by newyorkcityjay on 2012-02-17
I just got a new HP Omni220 with 64 bit i5 processor.  It's great, but the Win7 installation has a SYSTEM partition all the way at the left of the drive, which I had never seen before on other systems.  I shrank my Windows partition and tried to install Ubuntu to the new space, but I can never get it recognized by the Windows boot loader.

Any ideas?

---

### Post by darkod on 2012-02-17
Yes, install ubuntu's grub2 bootloader to the MBR and problem solved. It can boot both linux and windows. While windows bootloader can boot only windows by default.

---

### Post by newyorkcityjay on 2012-02-17
Let me see if I understand...
I should boot up to a Live USB and install GRUB2?  I can't boot to the installation of Ubuntu on the HD at the moment.

---

### Post by darkod on 2012-02-17
Apart from the fact that the install should have installed grub2 too, yes, you can install it from live mode.
It's better if you can run the boot info script from live mode. The link with instructions how to do it and post the results is in my signature. It will show more details of your setup so that we don't make a mistake being "blind".

---

### Post by newyorkcityjay on 2012-02-17
I don't quite understand what that means... do I install a package from the terminal?  Here is the output:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda5 starts at sector 105066496.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 20110518
    Boot sector info:   Syslinux looks at sector 1442248 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   105,064,959   104,858,112   7 NTFS / exFAT / HPFS
/dev/sda3         105,066,494 1,918,124,031 1,813,057,538   5 Extended
/dev/sda5         105,066,496 1,853,308,927 1,748,242,432   7 NTFS / exFAT / HPFS
/dev/sda6       1,905,739,776 1,918,124,031    12,384,256  82 Linux swap / Solaris
/dev/sda4       1,918,124,032 1,953,521,663    35,397,632   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4005 MB, 4005560320 bytes
124 heads, 62 sectors/track, 1017 cylinders, total 7823360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,818,695     7,818,634   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2C4E37004E36C1FE                       ntfs       SYSTEM
/dev/sda2        8876D26576D25412                       ntfs       OS
/dev/sda4        7490A6DB90A6A2DA                       ntfs       HP_RECOVERY
/dev/sda5        5EB80300B802D705                       ntfs       HOME
/dev/sda6        50ef3200-0256-46c5-958d-ff1ff9e50c4d   swap       
/dev/sdb1        3D4D-B524                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

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

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

/home/ubuntu/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by darkod on 2012-02-17
You have no ubuntu installed. You have 4 ntfs partitions and one linux swap partition, but no linux partition which would be your root (main system) partition.

---

### Post by newyorkcityjay on 2012-02-17
> You have no ubuntu installed.
Yeah... that would be a problem :P
I had installed and then removed it because it wasn't working and forgotten that when I ran the test.

Anyway, to fix this, I reinstalled to a clean partition from a Live USB and before restarting I ran [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") and that worked like a charm.

Now, if I just get my video driver working properly :-(
Thanks for your help!

---

### Post by darkod on 2012-02-17
Yeah, shame on ubuntu. It doesn't work after it's removed. :p

Glad you got it sorted.

---

