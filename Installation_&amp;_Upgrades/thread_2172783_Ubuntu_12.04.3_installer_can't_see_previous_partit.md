---
title: "Ubuntu 12.04.3 installer can't see previous partitions but gparted does"
date: 2013-09-06
forum: Installation &amp; Upgrades
---

### Post by skyglow on 2013-09-06
As written in the topic Gparted can see partitions on the hard disk, but when i install device is partition free.

I'm installing on a system with uefi and secure boot support, but they should be both disabled.
I already installed ubuntu before but single boot and all worked fine.
I'm now trying to install Ubuntu with Windows 7 with dual boot.
Windows 7 is already installed and working.


Boot info script
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.00-3.35) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 2012-10-23
    Boot sector info:  Syslinux looks at sector 16392 of /dev/sdb1 for its 
                       second stage. The integrity of Syslinux couldn't be 
                       verified (install gawk). SYSLINUX is installed in the  
                       directory. The 2 ADV sectors are not the same 
                       (corrupt). No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   419,432,447   419,225,600   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4127 MB, 4127195136 bytes
255 heads, 63 sectors/track, 501 cylinders, total 8060928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     8,060,927     8,058,880   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        F6E26547E2650D65                       ntfs       Riservato per il sistema
/dev/sda2        AAD4725BD47229A9                       ntfs       
/dev/sdb1        DEA5-3CD8                              vfat       UBUNTU 1204

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig 
 
LABEL loadconfig 
  CONFIG /isolinux/isolinux.cfg 
  APPEND /isolinux/ 
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux.cfg                                   1


```
As you can see sda1 and sda2 exists but the installer doesn't find them

Thank you for any help you can provide me.

---

### Post by Quackers on 2013-09-06
Welcome to UF.
It seems that your hard drive has the remnants of a GUID partition table which could be confusing the installer. When both MBR data and GPT data are on the same disc installers can get confused and report no partitions.
If you are happy using the MBR partitions I would recommend that you remove the stray GPT data on the disc. There are a few ways to do that, one of which is to download and run Fixparts (a utility written by a former member of this forum).
Once Fixparts has run I suspect you'll find that the installer behaves normally.

Download [Fixparts]("http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.7/fixparts-binaries/") for your architecture (32 bit or 64 bit) either in Windows format or Linux (.deb) format and run it following the instructions below
[http://www.rodsbooks.com/fixparts/]("http://www.rodsbooks.com/fixparts/")

---

### Post by skyglow on 2013-09-06
Problem was exactly what you said.
Only thing that differs from the guide is sfdisk supports only MBR and not GPT.
Thanks again for your support.
I already marked this topic as solved and i think it's possible to close :)

---

### Post by Quackers on 2013-09-06
Yes, that's correct. If I remember correctly Rod states that in the guide.
I'm glad it was solved so easily. It's a very handy little utility, Fixparts. You hope you don't need it but you're glad it's there if you do.
Happy Ubuntuing!

---

### Post by Geezanansa on 2013-09-06
Fixparts is for MBR/BIOS/Legacy/CSM system. Which is what Quackers recommends to use as skyglow indicates the intention of staying with MBR.

If you want to go with GPT and UEFI (Ubuntu has ability to install to GPT using MBR or UEFI) you could use gdisk to fix partition table and or efibootmgr to delete unused UEFI boot entries
> GPT fdisk consists of three programs:
  
[LIST]
[*]gdisk&#8212;An interactive text-mode program similar to     fdisk
[*]sgdisk&#8212;A command-line program intended for use in     scripts or by experts who need quick and direct access to a specific     feature
[*]cgdisk&#8212;A curses-based interactive text-mode program     similar to cfdisk
[/LIST]

Fixparts comes with these utilities.
Source: [http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)

whereas sfdisk is for MBR (as described)
>        **sfdisk**  doesn't understand the GUID Partition Table (GPT) format and it
       is not designed for large partitions.  In  these  cases  use  the  more
       advanced GNU **[parted]("http://manpages.ubuntu.com/manpages/raring/man8/parted.8.html")**(8).
Source: [http://manpages.ubuntu.com/manpages/raring/man8/sfdisk.8.html](http://manpages.ubuntu.com/manpages/raring/man8/sfdisk.8.html)

For more information regarding why and how what skyglow observes see [http://www.rodsbooks.com/gdisk/whygdisk.html](http://www.rodsbooks.com/gdisk/whygdisk.html)

Nice one Quackers.

---

