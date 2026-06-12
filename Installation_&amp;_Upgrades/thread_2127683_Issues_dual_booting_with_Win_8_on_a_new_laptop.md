---
title: "Issues dual booting with Win 8 on a new laptop"
date: 2013-03-20
forum: Installation &amp; Upgrades
---

### Post by lucascacho on 2013-03-20
Hi everyone.
After quite some time searching for a solution to my particular problem with no luck, i have decided to turn to the forums with hopes of getting some help :)


Here's what's up: I am on a new Sony Vaio T-Series Netbook running Windows 8, which has an EFI bootloader.


IN my attempt to dual boot, I created a 10gb partition for ubuntu, downloaded the 64-bit version (as suggested by the website due to the EFI boot) and proceeded to boot it from a flashdrive.
The install worked perfectly and ubuntu was up and running.
Thing is, I wasn't able to choose what OS to boot each time the computer booted up, so in my ignorance I used the boot repair software to try and solve the issue. I ended up getting a GRUB RESCUE console interface and had to rebuild my MBR and boot using the windows recovery console.
So now I have ubuntu installed on a separate partition, but have no way of booting into it.

I ran the Boot Info script, here is the output:

```
                  Boot Info Script 0.61      [1 April 2012]




============================= Boot Info Summary: ===============================


 => Windows is installed in the MBR of /dev/sda.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/grubx64.efi


sda2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


sda3: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/linuxmint/grubx64.efi 
                       /efi/ubuntu/grubx64.efi /bootmgr /boot/bcd


sda4: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''


sda5: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe


sda6: __________________________________________________________________________


    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info: 
    Operating System:  
    Boot files:        


sda7: __________________________________________________________________________


    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''


sda8: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb: ___________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 1615808 of /dev/sdb for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                   1   500,118,191   500,118,191  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       534,527       532,480 -
/dev/sda2         534,528     3,553,279     3,018,752 Windows Recovery Environment (Windows)
/dev/sda3       3,553,280     4,085,759       532,480 EFI System partition
/dev/sda4       4,085,760     4,347,903       262,144 Microsoft Reserved Partition (Windows)
/dev/sda5       4,347,904   399,984,639   395,636,736 Data partition (Windows/Linux)
/dev/sda6     399,984,640   420,956,159    20,971,520 Data partition (Windows/Linux)
/dev/sda7     420,958,208   437,768,191    16,809,984 -
/dev/sda8     437,768,192   500,117,503    62,349,312 Windows Recovery Environment (Windows)


"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        C46A-065D                              vfat       SONYSYS
/dev/sda2        F274DA3D74DA046F                       ntfs       Windows RE tools
/dev/sda3        FEA6-8C3B                              vfat       
/dev/sda5        DCAEAB63AEAB34C4                       ntfs       
/dev/sda6        1f0df31a-fd48-48ed-bc1f-71ff5a5b5056   ext2       
/dev/sda8        18E2E459E2E43D1E                       ntfs       Recovery
/dev/sdb         E0A8-ACA7                              vfat       UBUNTU


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)




=========================== sdb/boot/grub/grub.cfg: ============================


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
    linux    /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi.signed  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------


============================== sdb/syslinux.cfg: ===============================


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
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --


label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --


label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
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
kernel /casper/vmlinuz.efi.signed
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --


label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz.efi.signed
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --


label ubnentry8
menu label OEM install (for manufacturers)
kernel /casper/vmlinuz.efi.signed
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --


label ubnentry9
menu label Check disc for defects
kernel /casper/vmlinuz.efi.signed
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --


--------------------------------------------------------------------------------


==================== sdb: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


            ?? = ??             boot/grub/grub.cfg                             1


================== sdb: Location of files loaded by Syslinux: ==================


           GiB - GB             File                                 Fragment(s)


            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1


=============== sdb: Version of COM32(R) files used by Syslinux: ===============


 menu.c32                           :  COM32R module (v4.xx)


======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown GPT Partiton Type
329701f46e06124e8273346c5641494f
Unknown GPT Partiton Type
dee2bfd3af3ddf11ba40e3a556d89593
Unknown BootLoader on sda1


00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 5d 06 6a c4 4e  4f 20 4e 41 4d 45 20 20  |..)].j.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200


Unknown BootLoader on sda3


00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 01 7e 20  |.X.MSDOS5.0...~ |
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 38 36 00  |........?....86.|
00000020  00 20 08 00 c1 0f 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 3b 8c a6 fe 4e  4f 20 4e 41 4d 45 20 20  |..);...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200


Unknown BootLoader on sda6


00000000  eb 58 90 00 53 44 4f 53  35 2e 30 00 02 10 16 10  |.X..SDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 48 d7 17  |........?....H..|
00000020  00 00 40 01 f5 27 00 00  00 00 00 00 02 00 00 00  |..@..'..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 3e 08 45 4a 4e  4f 20 4e 41 4d 45 20 20  |..)>.EJNO NAME  |
00000050  20 20 00 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  .AT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 00 00  |................|
00000200


Unknown BootLoader on sda7


00000000  70 a5 41 16 ae 99 e0 05  00 00 00 00 00 00 00 00  |p.A.............|
00000010  00 00 00 00 00 00 00 00  00 ff ff 1f 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 40 fc 1f 00 00 00 00  |.........@......|
00000030  00 00 00 00 01 04 74 84  f0 43 00 40 80 fe ff ff  |......t..C.@....|
00000040  c1 03 e0 ff ff ff ff ff  53 02 ff ff ff ff ff ff  |........S.......|
00000050  60 20 00 00 00 a0 01 00  00 20 4a 00 0b 00 00 00  |` ....... J.....|
00000060  0c 03 80 00 40 10 80 10  3e f8 cf fc e3 9c 01 00  |....@...>.......|
00000070  81 9e f0 df ff ff ff ff  3f 09 10 80 12 80 87 c1  |........?.......|
00000080  20 01 00 59 80 09 98 01  c1 00 00 03 02 00 84 d0  | ..Y............|
00000090  18 08 08 00 00 00 8b 03  3e 11 36 72 1c a6 c2 30  |........>.6r...0|
000000a0  e1 0e 08 f8 00 3c cc db  6a 3c 34 c8 e1 3e 00 3c  |.....<..j<4..>.<|
000000b0  5e 57 cf 05 02 80 c1 03  24 82 f7 03 0e 80 00 00  |^W......$.......|
000000c0  40 88 aa bb 19 40 18 d8  ff ff ff ff ff ff ff ff  |@....@..........|
000000d0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000100  ff ff ff ff ff ff ff ff  04 10 00 b8 11 59 00 88  |.............Y..|
00000110  62 10 18 19 98 0d 00 00  c0 c2 00 00 04 00 1c 69  |b..............i|
00000120  00 40 00 08 00 00 c0 19  00 28 00 04 20 00 03 00  |.@.......(.. ...|
00000130  e0 fe f7 03 16 00 1c 00  00 f2 2c 02 08 80 fd fd  |..........,.....|
00000140  00 c0 00 00 70 12 60 40  ff ff ff ff ff ff ff ff  |....p.`@........|
00000150  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001c0  ff ff ff ff ff ff ff ff  ff 10 15 18 a4 5a 12 d8  |.............Z..|
000001d0  21 78 cc 20 10 25 00 88  44 01 00 00 05 60 0c 00  |!x. .%..D....`..|
000001e0  00 20 00 00 82 00 06 49  d6 0c 00 00 40 04 02 00  |. .....I....@...|
000001f0  00 86 4d 10 c2 20 00 08  d0 2f f8 f1 83 61 ff ff  |..M.. .../...a..|
00000200




========= Devices which don't seem to have a corresponding hard drive: =========


sdc 


=============================== StdErr Messages: ===============================


ls: reading directory sda6/: Input/output error
  No volume groups found
bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
```

Thanks for reading, regards

---

### Post by oldfred on 2013-03-21
Was this an older copy of Mint? Some old versions of grub2 had a bug where it overwrote the entire efi partition erasing Windows. And you do not have the Windows efi files in your efi partition.

You do show a Windows boot loader in the MBR, so did you convert your Windows install from UEFI to BIOS/CSM/legacy?

You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI  systems with Secure Boot enabled (using signed versions of Shim, GRUB,  and the Linux kernel). This is only currently set up for Ubuntu  (desktop, alternate, and server) and Edubuntu images due to pressures of  time; we expect to enable it across the entire Ubuntu family for  12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePango.../UbuntuDesktop]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop")

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by lucascacho on 2013-03-21
> **oldfred said:**
> Was this an older copy of Mint? Some old versions of grub2 had a bug where it overwrote the entire efi partition erasing Windows. And you do not have the Windows efi files in your efi partition.

You do show a Windows boot loader in the MBR, so did you convert your Windows install from UEFI to BIOS/CSM/legacy?

You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI  systems with Secure Boot enabled (using signed versions of Shim, GRUB,  and the Linux kernel). This is only currently set up for Ubuntu  (desktop, alternate, and server) and Edubuntu images due to pressures of  time; we expect to enable it across the entire Ubuntu family for  12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePango.../UbuntuDesktop]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop")

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

I did attempt to install Linux Mint on this HD before installing Ubuntu. That must've caused the issues you have listed.

While waiting for your reply, I attempted to install Ubuntu once more. The instalation was succesful and now when I boot I get the GRUB bootloader. Thing is that, while I am able to boot into Ubuntu, trying to boot into windows (by selecting the option labeled ***Windows 8 (loader) (on /dev/sda3)**)* returns the following error:
```
 error: can't find command 'drivemap'.
error: invalid EFI file path.
```

How can I fix that?

Here's the link to the BootInfo report: [http://paste.ubuntu.com/5635388](http://paste.ubuntu.com/5635388)


Just to clarify, I installed Ubuntu 12.10 64bit on an ext2 filesystem partition (sda8)

---

### Post by oldfred on 2013-03-21
Grub2's os-prober still has a bug and only creates BIOS type boot entries.

 grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

Why ext2? That is now very old, the Ubuntu standard install is ext4 and has been since 9.10. With ext2 you have no journal so repair is difficult or very slow.

---

### Post by lucascacho on 2013-03-21
> **oldfred said:**
> Grub2's os-prober still has a bug and only creates BIOS type boot entries.

 grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

Why ext2? That is now very old, the Ubuntu standard install is ext4 and has been since 9.10. With ext2 you have no journal so repair is difficult or very slow.


Honestly, I used ext2 out of ignorance. Since I hadn't done anything with that install, just performed a clean install using ext4 instead.

Now, regarding the bootloader, I'm sorry but I wasn't able to understand how to proceed. Did you mean that I will be unable to dual boot as I want? Should I use the "Recommended Repair" in Boot-Repair?

---

### Post by oldfred on 2013-03-21
After reinstall not sure what recommended repair is, but Boot-Repair usually does the correct thing. 

You need Boot-Repair to add correct chain entries as os-prober does not currently work.

If both Windows & Ubuntu are installed in UEFI mode, you can dual boot with most UEFI systems, but not all. 
Some need secure boot off, some work with secure boot on and some will only dual boot with Linux in BIOS mode and you have to leap thru the hoops of going into UEFI menu can turning UEFI on or off depending on which system you are booting.

But that is an UEFI issue and the vendor has to update his UEFI. You have to be able to secure boot with Ubuntu or Window as Ubuntu is using the Microsoft key.

---

