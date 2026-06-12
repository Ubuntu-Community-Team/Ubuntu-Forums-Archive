---
title: "Cant boot my ubuntu computer"
date: 2013-09-29
forum: Installation &amp; Upgrades
---

### Post by nigel4 on 2013-09-29
Hello,

My computer is ASUS Aspire Atheros, dual boot Ubuntu/Windows 7

I was working on ubuntu laptop, then I go tired and just closed the computer cover (screen). The computer went to sleep. About an hour later, I tried using it it wouldnt boot up anymore.

I created a live-USB flash drive using another computer, and booted into the computer using that. Then ran boot repair, it said it was successful.

 However it still cant boot. I have valuable files on there I spent over a year working on, but the stupid thing wont boot, trying to ruin my life by making me loose all my work.

Here is the URL I got from running the boot repair (no idea what good is a URL)  [http://paste.ubuntu.com/6169668](http://paste.ubuntu.com/6169668)

Here is the information (attached) after running the boot info script below.

Does anybody know how I can get my computer to boot again, I'm so desperate I'm willing to pay someone who can get it to boot again.

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

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
    Mounting failed:   ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read of MFT, mft=6 count=1 br=-1: Input/output error
Failed to open inode FILE_Bitmap: Input/output error
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read of MFT, mft=6 count=1 br=-1: Input/output error
Failed to open inode FILE_Bitmap: Input/output error
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20120131
    Boot sector info:  Syslinux looks at sector 1479624 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,465,145,343 1,464,938,496   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8004 MB, 8004304896 bytes
247 heads, 62 sectors/track, 1020 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62    15,620,279    15,620,218   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       8a7619c3-7e37-4270-9e5c-1e20f2076e1d   ext3       
/dev/sda1        B04AB8BD4AB881A0                       ntfs       System Reserved
/dev/sda2        E28ABB6E8ABB3DBB                       ntfs       Acer
/dev/sdb1        89B5-0F00                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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

---

### Post by sudodus on 2013-09-29
Welcome to the Ubuntu Forums :-)

> NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. [COLOR=#ff0000]In the first case run chkdsk /f on Windows
then reboot into Windows twice[/COLOR]. The usage of the /f parameter is very
important! If the device is a[COLOR=#ff0000] SoftRAID/FakeRAID[/COLOR] then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

There seems to be an error in the Windows partition. Try to repair it with a Windows tool. Have you got a Windows install disk or recovery disk? Then use it! Otherwise you could make or borrow or make a Bart PE or Windows 7 PE CD/USB drive and repair the file system from that (PE = preinstallation environment).

I did not find any linux partition. Did you really dual boot, or did you run Ubuntu in wubi?

*Edit*: Or is this one of those modern computers with a hybrid system SSD+HDD, that uses RAID for the drives to cooperate?

---

