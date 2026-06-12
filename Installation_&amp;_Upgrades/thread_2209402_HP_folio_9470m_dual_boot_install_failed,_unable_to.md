---
title: "HP folio 9470m: dual boot install failed, unable to boot anything"
date: 2014-03-05
forum: Installation &amp; Upgrades
---

### Post by tomrevilla on 2014-03-05
I tried to install Ubuntu 13.10 in an HP folio 9470m along with Windows 7 (dual boot), but I forgot to follow the steps regarding disabling UEFI (I was tired after figuring out how to resize the C partition). As a consequence I ended up with a system can't boot, neither Windows nor Ubuntu.

I can still boot the laptop with the Live-USB stick that has Ubuntu (this laptop does not have a CD/DVD unit). Using Boot-Repair from there does not solve the problem. The Windows partitions are still visible from the Live-USB.

I am wondering if it is still possible to install the Ubuntu over the whole harddrive, i.e. format the whole disk, deleting Windows, during the installation (there is no valuable data there), but this time following the instructions about disabling UEFI. I read reports of people that have installed Ubuntu on this model, but they usually do not mention if they did so along with Windows. Or is it that, sadly, the whole thing is now bricked?

I am at home right now and the laptop is in my office. Tomorrow I would be able to collect more information.

King regards,

Tomas

---

### Post by phidia on 2014-03-05
[This thread]("http://ubuntuforums.org/showthread.php?t=2183841") at the forums seems related and the 2nd post there includes a link for repairing UEFI boot.

---

### Post by tomrevilla on 2014-03-06
Here is the relevant information from boot-repair ([http://paste.ubuntu.com/7039131/](http://paste.ubuntu.com/7039131/)). The system still does not boot (Ubuntu 13.10 or Windows 7):

```
  Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda1 starts at sector 63. The info in boot sector on 
                       the starting sector of the MFT is wrong. According to 
                       the info in the boot sector, sda1 has 614399 sectors, 
                       but according to the info from fdisk, it has 1984 
                       sectors.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 616448. But according to the info from 
                       fdisk, sda2 starts at sector 2048. The info in boot 
                       sector on the starting sector of the MFT is wrong. 
                       According to the info in the boot sector, sda2 has 
                       320434175 sectors, but according to the info from 
                       fdisk, it has 614399 sectors.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       exfat
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type 'exfat'

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 935450624. But according to the info from 
                       fdisk, sda4 starts at sector 321052670. According to 
                       the info in the boot sector, sda4 has 37122047 
                       sectors, but according to the info from fdisk, it has 
                       655718401 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/BCD

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7/2008: FAT32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 972572672. But according to the info from 
                       fdisk, sda5 starts at sector 321052672. According to 
                       the info in the boot sector, sda5 has 4184064 
                       sectors.. But according to the info from the partition 
                       table, it has 65570815 sectors.
    Operating System:  
    Boot files:        /Hewlett-Packard/BIOSUpdate/CryptRSA.efi 
                       /Hewlett-Packard/BIOSUpdate/CryptRSA32.efi 
                       /Hewlett-Packard/BIOSUpdate/HpBiosUpdate.efi 
                       /Hewlett-Packard/BIOSUpdate/HpBiosUpdate32.efi 
                       /Hewlett-Packard/SystemDiags/CryptRSA.efi 
                       /Hewlett-Packard/SystemDiags/CryptRSA32.efi 
                       /Hewlett-Packard/SystemDiags/SystemDiags.efi 
                       /Hewlett-Packard/SystemDiags/SystemDiags32.efi

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type 'exfat'
mount: unknown filesystem type ''

sda7: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type 'exfat'
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20120702
    Boot sector info:  Syslinux looks at sector 1857192 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       616,447       614,400  42 SFS
/dev/sda3             616,448   321,050,623   320,434,176  42 SFS
/dev/sda4         321,052,670   976,771,071   655,718,402   5 Extended
/dev/sda5         321,052,672   386,623,487    65,570,816  83 Linux
/dev/sda6         386,625,536   390,836,223     4,210,688  82 Linux swap / Solaris
/dev/sda7         390,838,272   976,771,071   585,932,800  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2003 MB, 2003828736 bytes
43 heads, 42 sectors/track, 2167 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     3,913,727     3,913,696   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1640978A40976EED                       ntfs       SYSTEM
/dev/sda2        180098B200989878                       ntfs       
/dev/sda3        6095-543E                              exfat      
/dev/sda4        F8A6D018A6CFD572                       ntfs       HP_RECOVERY
/dev/sda5        4099-228A                              vfat       HP_TOOLS
/dev/sdb1        D010-0EAA                              vfat       USB DISK

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
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
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
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

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
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --

label ubnentry8
menu label OEM install (for manufacturers)
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --

label ubnentry9
menu label Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --

--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

MFT Sector of sda1

00000000  46 49 4c 45 30 00 03 00  e0 22 10 00 00 00 00 00  |FILE0...."......|
00000010  01 00 01 00 38 00 01 00  98 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  03 00 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  be d6 5b 97 f8 37 cf 01  be d6 5b 97 f8 37 cf 01  |..[..7....[..7..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  be d6 5b 97 f8 37 cf 01  |..........[..7..|
000000c0  be d6 5b 97 f8 37 cf 01  be d6 5b 97 f8 37 cf 01  |..[..7....[..7..|
000000d0  be d6 5b 97 f8 37 cf 01  00 40 00 00 00 00 00 00  |..[..7...@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  3f 00 00 00 00 00 00 00  |........?.......|
00000120  40 00 00 00 00 00 00 00  00 00 04 00 00 00 00 00  |@...............|
00000130  00 00 04 00 00 00 00 00  00 00 04 00 00 00 00 00  |................|
00000140  21 40 00 64 00 f8 ff ff  b0 00 00 00 48 00 00 00  |!@.d........H...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  01 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 20 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |. ..............|
00000180  08 10 00 00 00 00 00 00  21 01 ff 63 11 01 ff 00  |........!..c....|
00000190  ff ff ff ff 00 00 00 00  00 00 04 00 00 00 00 00  |................|
000001a0  00 00 04 00 00 00 00 00  21 40 00 64 00 f8 ff ff  |........!@.d....|
000001b0  b0 00 00 00 48 00 00 00  01 00 40 00 00 00 05 00  |....H.....@.....|
000001c0  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  21 01 ff 63 11 01 ff 00  ff ff ff ff 00 00 03 00  |!..c............|
00000200
MFT Sector of sda2

00000000  46 49 4c 45 30 00 03 00  0d 69 1d 3f 00 00 00 00  |FILE0....i.?....|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  60 01 ff ff 00 00 00 00  10 00 00 00 60 00 00 00  |`...........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  b5 2b 26 98 f8 37 cf 01  b5 2b 26 98 f8 37 cf 01  |.+&..7...+&..7..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  b5 2b 26 98 f8 37 cf 01  |.........+&..7..|
000000c0  b5 2b 26 98 f8 37 cf 01  b5 2b 26 98 f8 37 cf 01  |.+&..7...+&..7..|
000000d0  b5 2b 26 98 f8 37 cf 01  00 40 00 00 00 00 00 00  |.+&..7...@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 50 00 00 00  01 00 40 00 00 00 01 00  |....P.....@.....|
00000110  00 00 00 00 00 00 00 00  3f 8d 01 00 00 00 00 00  |........?.......|
00000120  40 00 00 00 00 00 00 00  00 00 d4 18 00 00 00 00  |@...............|
00000130  00 00 d4 18 00 00 00 00  00 00 d4 18 00 00 00 00  |................|
00000140  33 75 52 01 00 00 0c 32  cb 3a 76 52 01 00 ff ff  |3uR....2.:vR....|
00000150  b0 00 00 00 48 00 00 00  01 00 40 00 00 00 05 00  |....H.....@.....|
00000160  00 00 00 00 00 00 00 00  0d 00 00 00 00 00 00 00  |................|
00000170  40 00 00 00 00 00 00 00  00 e0 00 00 00 00 00 00  |@...............|
00000180  08 d0 00 00 00 00 00 00  08 d0 00 00 00 00 00 00  |................|
00000190  11 0e 03 00 a0 f8 ff ff  ff ff ff ff 00 00 00 00  |................|
000001a0  ff ff ff ff 00 00 00 00  ff ff ff ff 00 00 00 00  |................|
*
000001e0  ff ff ff ff 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  31 01 ff ff 0b 11 01 ff  00 78 e8 09 80 fa 60 01  |1........x....`.|
00000200
Unknown BootLoader on sda3

00000000  eb 76 90 45 58 46 41 54  20 20 20 00 00 00 00 00  |.v.EXFAT   .....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000040  3f 00 00 00 00 00 00 00  00 f8 9e 24 00 00 00 00  |?..........$....|
00000050  00 08 00 00 00 4a 00 00  00 58 00 00 a0 9e 24 00  |.....J...X....$.|
00000060  06 00 00 00 3e 54 95 60  00 01 00 00 09 08 01 80  |....>T.`........|
00000070  00 00 00 00 00 00 00 00  33 c9 8e d1 bc f0 7b 8e  |........3.....{.|
00000080  d9 a0 fb 7d b4 7d 8b f0  ac 98 40 74 0c 48 74 0e  |...}.}....@t.Ht.|
00000090  b4 0e bb 07 00 cd 10 eb  ef a0 fd 7d eb e6 cd 16  |...........}....|
000000a0  cd 19 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  0d 0a 52 65 74 69 72 65  7a 20 6c 65 20 64 69 73  |..Retirez le dis|
00000110  71 75 65 ff 0d 0a 45 72  72 2e 20 64 69 73 71 75  |que...Err. disqu|
00000120  65 ff 0d 0a 50 72 65 73  73 65 7a 20 75 6e 65 20  |e...Pressez une |
00000130  74 6f 75 63 68 65 20 70  6f 75 72 20 72 65 64 82  |touche pour red.|
00000140  6d 61 72 72 65 72 0d 0a  00 00 00 00 00 00 00 00  |marrer..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 ff ff  |................|
000001c0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001f0  ff ff ff ff ff ff ff ff  ff ff ff 00 14 22 55 aa  |............."U.|
00000200

Unknown BootLoader on sda6


Unknown BootLoader on sda7



=============================== StdErr Messages: ===============================

hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda7: No such file or directory
hexdump: /dev/sda7: No such file or directory
cat: /tmp/BootInfo-HynDHBTw/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-HynDHBTw/Tmp_Log: No such file or directory
File descriptor 9 (/proc/4305/mounts) leaked on lvscan invocation. Parent PID 12724: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-03-05__15h44 ===================
boot-repair version : 3.199~ppa40~saucy
boot-sav version : 3.199~ppa40~saucy
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 3.199~ppa40~saucy
boot-repair is executed in live-session (Ubuntu 13.10, saucy, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- BOOT_IMAGE=/casper/vmlinuz.efi
mount: unknown filesystem type 'exfat'
mount /dev/sda3 : Error code 32
mount -r /dev/sda3 /mnt/boot-sav/sda3
mount: unknown filesystem type 'exfat'
mount -r /dev/sda3 : Error code 32

=================== os-prober:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda2:Windows 7 (loader):Windows1:chain
/dev/sda4:Windows Vista (loader):Windows2:chain

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="SYSTEM" UUID="1640978A40976EED" TYPE="ntfs"
/dev/sda2: UUID="180098B200989878" TYPE="ntfs"
/dev/sda3: UUID="6095-543E" TYPE="exfat"
/dev/sda4: LABEL="HP_RECOVERY" UUID="F8A6D018A6CFD572" TYPE="ntfs"
/dev/sda5: LABEL="HP_TOOLS" UUID="4099-228A" TYPE="vfat"
/dev/sdb1: LABEL="USB DISK" UUID="D010-0EAA" TYPE="vfat"


1 disks with OS, 3 OS : 0 Linux, 0 MacOS, 3 Windows, 0 unknown type OS.

mount: unknown filesystem type 'exfat'
mount /dev/sda3 : Error code 32
mount -r /dev/sda3 /mnt/boot-sav/sda3
mount: unknown filesystem type 'exfat'
mount -r /dev/sda3 : Error code 32
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2.
sda3    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.
sda4    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda4.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA HGST HTS725050A7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  1049kB  1016kB  primary
2      1049kB  316MB   315MB   primary   ntfs            boot
3      316MB   164GB   164GB   primary   ntfs
4      164GB   500GB   336GB   extended
5      164GB   198GB   33.6GB  logical   ext4
6      198GB   200GB   2156MB  logical   linux-swap(v1)
7      200GB   500GB   300GB   logical   ext4


Model: General USB Flash Disk (scsi)
Disk /dev/sdb: 2004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  2004MB  2004MB  primary  fat32        boot

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:4096:msdos:ATA HGST HTS725050A7;
1:32.3kB:1049kB:1016kB:::;
2:1049kB:316MB:315MB:ntfs::boot;
3:316MB:164GB:164GB:ntfs::;
4:164GB:500GB:336GB:::;
5:164GB:198GB:33.6GB:ext4::;
6:198GB:200GB:2156MB:linux-swap(v1)::;
7:200GB:500GB:300GB:ext4::;

BYT;
/dev/sdb:2004MB:scsi:512:512:msdos:General USB Flash Disk;
1:16.4kB:2004MB:2004MB:fat32::boot;


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type vfat (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fd freefall full fuse hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx ptp0 pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sdb sdb1 sg0 sg1 shm snapshot snd stderr stdin stdout tpm0 uinput urandom v4l vga_arbiter vhost-net video0 watchdog watchdog0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 5f 09 00 00 00 00 00  |........._......|
00000030  00 64 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.d..............|
00000040  f6 00 00 00 01 00 00 00  ed 6e 97 40 8a 97 40 16  |.........n.@..@.|
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
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 45 72  |t.............Er|
00000190  72 65 75 72 20 6c 65 63  74 75 72 65 20 64 69 73  |reur lecture dis|
000001a0  71 75 65 00 0d 0a 42 4f  4f 54 4d 47 52 20 61 62  |que...BOOTMGR ab|
000001b0  73 65 6e 74 00 0d 0a 42  4f 4f 54 4d 47 52 20 63  |sent...BOOTMGR c|
000001c0  6f 6d 70 72 65 73 73 82  00 0d 0a 43 74 72 6c 2b  |ompress....Ctrl+|
000001d0  41 6c 74 2b 53 75 70 70  72 20 70 6f 75 72 20 72  |Alt+Suppr pour r|
000001e0  65 64 82 6d 61 72 72 65  72 0d 0a 00 6f 20 72 65  |ed.marrer...o re|
000001f0  73 74 61 72 74 0d 0a 00  8c a4 b5 c9 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 09 00  |........?....h..|
00000020  00 00 00 00 80 00 80 00  ff 6f 19 13 00 00 00 00  |.........o......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  78 98 98 00 b2 98 00 18  |........x.......|
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
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 45 72  |t.............Er|
00000190  72 65 75 72 20 6c 65 63  74 75 72 65 20 64 69 73  |reur lecture dis|
000001a0  71 75 65 00 0d 0a 42 4f  4f 54 4d 47 52 20 61 62  |que...BOOTMGR ab|
000001b0  73 65 6e 74 00 0d 0a 42  4f 4f 54 4d 47 52 20 63  |sent...BOOTMGR c|
000001c0  6f 6d 70 72 65 73 73 82  00 0d 0a 43 74 72 6c 2b  |ompress....Ctrl+|
000001d0  41 6c 74 2b 53 75 70 70  72 20 70 6f 75 72 20 72  |Alt+Suppr pour r|
000001e0  65 64 82 6d 61 72 72 65  72 0d 0a 00 6f 20 72 65  |ed.marrer...o re|
000001f0  73 74 61 72 74 0d 0a 00  8c a4 b5 c9 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sda4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 d8 c1 37  |........?......7|
00000020  00 00 00 00 80 00 80 00  ff 6f 36 02 00 00 00 00  |.........o6.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  72 d5 cf a6 18 d0 a6 f8  |........r.......|
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

=================== hexdump -n512 -C /dev/sda5
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 32 20  |.X.MSDOS5.0...2 |
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 48 f8 39  |........?....H.9|
00000020  00 d8 3f 00 e7 0f 00 00  00 00 00 00 02 00 00 00  |..?.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 8a 22 99 40 4e  4f 20 4e 41 4d 45 20 20  |..).".@NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  74 69 72 65 7a 20 6c 65  20 64 69 73 71 75 65 ff  |tirez le disque.|
000001c0  0d 0a 45 72 72 2e 20 64  69 73 71 75 65 ff 0d 0a  |..Err. disque...|
000001d0  50 72 65 73 73 65 7a 20  75 6e 65 20 74 6f 75 63  |Pressez une touc|
000001e0  68 65 20 70 6f 75 72 20  72 65 64 82 6d 61 72 72  |he pour red.marr|
000001f0  65 72 0d 0a 00 00 00 00  00 ac c0 ce 00 00 55 aa  |er............U.|
00000200

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  3.9G  116M  3.8G   3% /
udev           devtmpfs   3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs      785M  1.2M  784M   1% /run
/dev/sdb1      vfat       1.9G  903M 1005M  48% /cdrom
/dev/loop0     squashfs   843M  843M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      3.9G  1.1M  3.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      3.9G   76K  3.9G   1% /run/shm
none           tmpfs      100M   52K  100M   1% /run/user
/dev/sda1      fuseblk    300M   36M  265M  12% /mnt/boot-sav/sda1
/dev/sda2      fuseblk    153G   40G  114G  26% /mnt/boot-sav/sda2
/dev/sda4      fuseblk     18G   16G  2.7G  85% /mnt/boot-sav/sda4
/dev/sda5      vfat       2.0G   15M  2.0G   1% /mnt/boot-sav/sda5

=================== fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x5454786a

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
Partition 1 does not start on physical sector boundary.
/dev/sda2   *        2048      616447      307200   42  SFS
/dev/sda3          616448   321050623   160217088   42  SFS
/dev/sda4       321052670   976771071   327859201    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       321052672   386623487    32785408   83  Linux
/dev/sda6       386625536   390836223     2105344   82  Linux swap / Solaris
/dev/sda7       390838272   976771071   292966400   83  Linux

Disk /dev/sdb: 2003 MB, 2003828736 bytes
43 heads, 42 sectors/track, 2167 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     3913727     1956848    b  W95 FAT32



=================== Recommended repair
Recommended-Repair
This setting will restore the [(generic mbr)] MBR in sda, and make it boot on sda2.
Additional repair will be performed: unhide-bootmenu-10s repair-filesystems


Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var

fsck -fyM /dev/sda1
fsck from util-linux 2.20.1

fsck -fyM /dev/sda2
fsck from util-linux 2.20.1

fsck -fyM /dev/sda3
fsck from util-linux 2.20.1
fsck: fsck.exfat: not found
fsck: error 2 while executing fsck.exfat for /dev/sda3

fsck -fyM /dev/sda4
fsck from util-linux 2.20.1

fsck -fyM /dev/sda5
fsck from util-linux 2.20.1
mount: unknown filesystem type 'exfat'
mount /dev/sda3 : Error code 32
mount -r /dev/sda3 /mnt/boot-sav/sda3
mount: unknown filesystem type 'exfat'
mount -r /dev/sda3 : Error code 32
Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out

Boot successfully repaired.

You can now reboot your computer.
```

---

### Post by tomrevilla on 2014-03-13
In the end I formatted the whole disk and installed only Ubuntu. Solved.

---

