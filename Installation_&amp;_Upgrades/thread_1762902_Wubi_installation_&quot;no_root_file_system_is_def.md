---
title: "Wubi installation &quot;no root file system is defined&quot;"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by rbartleman on 2011-05-19
I am trying to install Ubuntu on my laptop and it works fine running from USB but during the install from WUBI I get the error "no root file system is defined". I have followed several other threads where they got the same error but my results do not appear to be the same as theirs in the analyzer script. Can someone help me figure this out?

```

                                                                     
                                                                     
                                                                     
                                             
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/mapper/isw_dcadhicajj_Volume0

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_dcadhicajj_Volume01: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_dcadhicajj_Volume02: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_dcadhicajj_Volume03: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             32    31,266,815    31,266,784   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    18,458,623    18,456,576  27 Hidden HPFS/NTFS
/dev/sdb2    *     18,458,624    18,663,423       204,800   7 HPFS/NTFS
/dev/sdb3          18,663,424   250,079,231   231,415,808   7 HPFS/NTFS

/dev/sdb3 ends after the last sector of /dev/sdb

Drive: isw_dcadhicajj_Volume0 ___________________ _____________________________________________________

Disk /dev/mapper/isw_dcadhicajj_Volume0: 128.0 GB, 128041877504 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250081792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_dcadhicajj_Volume01              2,048    18,458,623    18,456,576  27 Hidden HPFS/NTFS
/dev/mapper/isw_dcadhicajj_Volume02   *     18,458,624    18,663,423       204,800   7 HPFS/NTFS
/dev/mapper/isw_dcadhicajj_Volume03         18,663,424   250,079,231   231,415,808   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_dcadhicajj_Volume0p1 FCE05421E053E106                       ntfs       Recovery                      
/dev/mapper/isw_dcadhicajj_Volume0p2 BAB49240B491FED7                       ntfs       System Reserved               
/dev/mapper/isw_dcadhicajj_Volume0p3 28EC9304EC92CB86                       ntfs                                     
/dev/mapper/isw_dcadhicajj_Volume0: PTTYPE="dos" 
/dev/sda1        16FA-1556                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb                                                isw_raid_member                               
/dev/sdc                                                isw_raid_member                               
error: /dev/mapper/isw_dcadhicajj_Volume01: No such file or directory
error: /dev/mapper/isw_dcadhicajj_Volume02: No such file or directory
error: /dev/mapper/isw_dcadhicajj_Volume03: No such file or directory
error: /dev/sdb1: No such file or directory
error: /dev/sdb2: No such file or directory
error: /dev/sdb3: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_dcadhicajj_Volume0
isw_dcadhicajj_Volume0p1
isw_dcadhicajj_Volume0p2
isw_dcadhicajj_Volume0p3

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================


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

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e0 17 dd 01 0b 77 00 00  00 00 00 00 02 00 00 00  |.....w..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 56 15 fa 16 4e  4f 20 4e 41 4d 45 20 20  |..)V...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 3e  ee 00 00 66 ba 00 00 00  |..E}.f.>...f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
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

Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdb3


Unknown BootLoader  on isw_dcadhicajj_Volume01


Unknown BootLoader  on isw_dcadhicajj_Volume02


Unknown BootLoader  on isw_dcadhicajj_Volume03



=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/mapper/isw_dcadhicajj_Volume01: No such file or directory
hexdump: /dev/mapper/isw_dcadhicajj_Volume01: No such file or directory
hexdump: /dev/mapper/isw_dcadhicajj_Volume02: No such file or directory
hexdump: /dev/mapper/isw_dcadhicajj_Volume02: No such file or directory
hexdump: /dev/mapper/isw_dcadhicajj_Volume03: No such file or directory
hexdump: /dev/mapper/isw_dcadhicajj_Volume03: No such file or directory

```

---

### Post by Rubi1200 on 2011-05-20
Hi and welcome to the forums :-)

Which version of Ubuntu are you trying to install via Wubi?

If 11.04, please run the script again, but this time use the new script for 11.04 (rest of the instructions remain the same):

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link to download the script after the instructions.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

sudo bash ~/Desktop/boot_info_script*.sh

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

new script for 11.04
```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'
```

Next, is this a RAID or an LVM setup you have there?

I know that Wubi installs to RAID are not supported, though theoretically possible. I am not sure about LVM though.

Regardless, please post the new script results so we can take a look and try and help you sort this out.

Thanks.

---

