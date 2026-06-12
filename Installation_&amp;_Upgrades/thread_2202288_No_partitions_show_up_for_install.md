---
title: "No partitions show up for install"
date: 2014-01-28
forum: Installation &amp; Upgrades
---

### Post by benjamin9 on 2014-01-28
I have tried a couple forum posts that deal with this problem but have found no solutions. I am trying to install 13.10 on HP e9300z which has Windows 7 installed. I shrank my existing partition to create free space and then formatted it as ext4. I then reboot and run off the usb which has the iso. It boots to the installation screen fine and when I come to the installion type screen there are no partitions to select. The New partition button is grayed out and if i select the change, +, or - keys the install will freeze. If I select install now it tells me no root system is defined and to fix it in the partition table. The solutions I have looked up all seem to have extra steps in the installation program so I am unsure why mine is different. I tried removing dmraid but that did not change and thing. I've played around with different ways of formatting the partitions but have had no success. Anyone have any ideas?

---

### Post by TheFu on 2014-01-28
Please run **boot-info** on the machine and post a link. My sign has links, if you need it.

---

### Post by benjamin9 on 2014-01-28
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/mapper/pdc_bcgfabgecg.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 59856 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/BOOT/grubx64.efi

pdc_bcgfabgecg1: _______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

pdc_bcgfabgecg2: _______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

pdc_bcgfabgecg3: _______________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

pdc_bcgfabgecg4: _______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/BCD

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,143,939,071 1,143,732,224   7 NTFS / exFAT / HPFS
/dev/sda3       1,143,941,057 1,226,348,543    82,407,487   f W95 Extended (LBA)
Empty Partition.
/dev/sda4       1,226,348,544 1,249,996,799    23,648,256   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 15.7 GB, 15707668480 bytes
256 heads, 63 sectors/track, 1902 cylinders, total 30679040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    30,679,039    30,676,992   c W95 FAT32 (LBA)


Drive: pdc_bcgfabgecg _____________________________________________________________________

Disk /dev/mapper/pdc_bcgfabgecg: 640.0 GB, 640000000000 bytes
255 heads, 63 sectors/track, 77808 cylinders, total 1250000000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/pdc_bcgfabgecg1   *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/pdc_bcgfabgecg2            206,848 1,143,939,071 1,143,732,224   7 NTFS / exFAT / HPFS
/dev/mapper/pdc_bcgfabgecg3      1,143,941,057 1,226,348,543    82,407,487   f W95 Extended (LBA)
Empty Partition.
/dev/mapper/pdc_bcgfabgecg4      1,226,348,544 1,249,996,799    23,648,256   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2666028866025947                       ntfs       SYSTEM
/dev/sda2        01CF1BBCBDFD2800                       ntfs       HP
/dev/sda4        2666546366543631                       ntfs       FACTORY_IMAGE
/dev/sdb1        0F0D-317F                              vfat       UUI

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
pdc_bcgfabgecg
pdc_bcgfabgecg3

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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  e9 39 87 31 00 00 ea 6f  e8 39 87 31 00 20 3f 2d  |.9.1...o.9.1. ?-|
00000010  09 42 6b 4a 58 58 58 28  0a 42 ac 52 aa 6a 6a 00  |.BkJXXX(.B.R.jj.|
00000020  8c 52 09 42 fe fc fe 55  2a 42 6b 4a aa 95 95 08  |.R.B...U*BkJ....|
00000030  6b 4a 09 3a 28 22 aa fd  6b 4a 09 3a e0 80 aa 57  |kJ.:("..kJ.:...W|
00000040  4a 4a e9 39 02 00 aa d7  8b 4a 2a 42 2a 02 02 f5  |JJ.9.....J*B*...|
00000050  ac 52 2a 42 aa 8a aa 55  8c 52 4a 42 aa aa fe 7d  |.R*B...U.RJB...}|
00000060  8b 4a 2a 42 08 00 0a a7  ac 52 2b 42 00 a8 5e 57  |.J*B.....R+B..^W|
00000070  ac 52 0a 3a 2a 0a ed ff  6b 4a ea 39 20 28 ae 7e  |.R.:*...kJ.9 (.~|
00000080  4b 4a e9 39 c0 60 70 eb  6a 4a e9 39 0d 0d ab bf  |KJ.9.`p.jJ.9....|
00000090  ac 5a 4a 42 2b 2b ad f5  cc 5a 09 42 89 2d a7 a7  |.ZJB++...Z.B.-..|
000000a0  6b 4a 08 42 8b af 35 35  ed 5a 6b 4a a2 a0 62 c2  |kJ.B..55.ZkJ..b.|
000000b0  ed 5a 6b 52 2e 2c 5e 5e  cd 5a 6b 52 aa 8e ad ed  |.ZkR.,^^.ZkR....|
000000c0  ac 52 09 42 02 8a fc 56  4a 42 c8 39 e8 e8 7e 7f  |.R.B...VJB.9..~.|
000000d0  09 42 87 31 62 6a bd 35  2a 4a 66 29 e2 62 62 e2  |.B.1bj.5*Jf).bb.|
000000e0  c8 39 66 29 28 a2 6a 7e  c7 39 45 21 dc fc fe fe  |.9f)(.j~.9E!....|
000000f0  a7 31 66 29 82 ea 0d c5  a7 31 45 29 ff ae 0e ea  |.1f).....1E)....|
00000100  a7 39 66 29 1e d7 ff 7f  c8 39 65 29 f7 a5 2f 3b  |.9f).....9e)../;|
00000110  08 42 66 29 58 58 fa f8  e8 39 86 31 5d db a3 02  |.Bf)XX...9.1]...|
00000120  0a 42 66 29 b5 b7 2f ae  09 42 66 29 72 78 a0 20  |.Bf)../..Bf)rx. |
00000130  09 42 87 31 d5 d5 5e 3a  4a 4a c8 39 a9 bb b9 f8  |.B.1..^:JJ.9....|
00000140  4a 4a c8 39 9c ba ba bf  ed 5a e8 41 62 7a 7a 7a  |JJ.9.....Z.Abzzz|
00000150  09 42 a7 31 a2 01 01 8d  29 42 a7 39 e2 da 9c f8  |.B.1....)B.9....|
00000160  49 4a 66 31 9c 2a 0a 02  8b 52 08 42 fe e2 72 72  |IJf1.*...R.B..rr|
00000170  29 42 a7 39 7c a8 ef 2f  09 42 86 31 5e 58 f8 f0  |)B.9|../.B.1^X..|
00000180  c7 39 66 29 b9 3f ed bf  a7 31 45 29 57 80 03 8b  |.9f).?...1E)W...|
00000190  c7 39 66 29 b9 b7 56 ff  e8 39 86 31 a5 03 a1 fd  |.9f)..V..9.1....|
000001a0  c7 39 66 29 ee f8 f0 5a  e8 39 66 29 f2 db 5f 55  |.9f)...Z.9f).._U|
000001b0  e8 39 67 31 2a ab bd fd  e8 41 87 31 2e b7 00 00  |.9g1*....A.1....|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on pdc_bcgfabgecg3

00000000  e9 39 87 31 00 00 ea 6f  e8 39 87 31 00 20 3f 2d  |.9.1...o.9.1. ?-|
00000010  09 42 6b 4a 58 58 58 28  0a 42 ac 52 aa 6a 6a 00  |.BkJXXX(.B.R.jj.|
00000020  8c 52 09 42 fe fc fe 55  2a 42 6b 4a aa 95 95 08  |.R.B...U*BkJ....|
00000030  6b 4a 09 3a 28 22 aa fd  6b 4a 09 3a e0 80 aa 57  |kJ.:("..kJ.:...W|
00000040  4a 4a e9 39 02 00 aa d7  8b 4a 2a 42 2a 02 02 f5  |JJ.9.....J*B*...|
00000050  ac 52 2a 42 aa 8a aa 55  8c 52 4a 42 aa aa fe 7d  |.R*B...U.RJB...}|
00000060  8b 4a 2a 42 08 00 0a a7  ac 52 2b 42 00 a8 5e 57  |.J*B.....R+B..^W|
00000070  ac 52 0a 3a 2a 0a ed ff  6b 4a ea 39 20 28 ae 7e  |.R.:*...kJ.9 (.~|
00000080  4b 4a e9 39 c0 60 70 eb  6a 4a e9 39 0d 0d ab bf  |KJ.9.`p.jJ.9....|
00000090  ac 5a 4a 42 2b 2b ad f5  cc 5a 09 42 89 2d a7 a7  |.ZJB++...Z.B.-..|
000000a0  6b 4a 08 42 8b af 35 35  ed 5a 6b 4a a2 a0 62 c2  |kJ.B..55.ZkJ..b.|
000000b0  ed 5a 6b 52 2e 2c 5e 5e  cd 5a 6b 52 aa 8e ad ed  |.ZkR.,^^.ZkR....|
000000c0  ac 52 09 42 02 8a fc 56  4a 42 c8 39 e8 e8 7e 7f  |.R.B...VJB.9..~.|
000000d0  09 42 87 31 62 6a bd 35  2a 4a 66 29 e2 62 62 e2  |.B.1bj.5*Jf).bb.|
000000e0  c8 39 66 29 28 a2 6a 7e  c7 39 45 21 dc fc fe fe  |.9f)(.j~.9E!....|
000000f0  a7 31 66 29 82 ea 0d c5  a7 31 45 29 ff ae 0e ea  |.1f).....1E)....|
00000100  a7 39 66 29 1e d7 ff 7f  c8 39 65 29 f7 a5 2f 3b  |.9f).....9e)../;|
00000110  08 42 66 29 58 58 fa f8  e8 39 86 31 5d db a3 02  |.Bf)XX...9.1]...|
00000120  0a 42 66 29 b5 b7 2f ae  09 42 66 29 72 78 a0 20  |.Bf)../..Bf)rx. |
00000130  09 42 87 31 d5 d5 5e 3a  4a 4a c8 39 a9 bb b9 f8  |.B.1..^:JJ.9....|
00000140  4a 4a c8 39 9c ba ba bf  ed 5a e8 41 62 7a 7a 7a  |JJ.9.....Z.Abzzz|
00000150  09 42 a7 31 a2 01 01 8d  29 42 a7 39 e2 da 9c f8  |.B.1....)B.9....|
00000160  49 4a 66 31 9c 2a 0a 02  8b 52 08 42 fe e2 72 72  |IJf1.*...R.B..rr|
00000170  29 42 a7 39 7c a8 ef 2f  09 42 86 31 5e 58 f8 f0  |)B.9|../.B.1^X..|
00000180  c7 39 66 29 b9 3f ed bf  a7 31 45 29 57 80 03 8b  |.9f).?...1E)W...|
00000190  c7 39 66 29 b9 b7 56 ff  e8 39 86 31 a5 03 a1 fd  |.9f)..V..9.1....|
000001a0  c7 39 66 29 ee f8 f0 5a  e8 39 66 29 f2 db 5f 55  |.9f)...Z.9f).._U|
000001b0  e8 39 67 31 2a ab bd fd  e8 41 87 31 2e b7 00 00  |.9g1*....A.1....|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

ERROR: ddf1: seeking device "/dev/dm-4" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-4" to 4608
ERROR: hpt45x: seeking device "/dev/dm-4" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-4" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-4" to 18446744073709289984
/home/ubuntu/Downloads/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
cat: /tmp/BootInfo-G6BOePjO/Tmp_Log: No such file or directory
ERROR: ddf1: seeking device "/dev/dm-4" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-4" to 4608
ERROR: hpt45x: seeking device "/dev/dm-4" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-4" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-4" to 18446744073709289984
  No volume groups found

---

### Post by benjamin9 on 2014-01-29
bump

---

### Post by Bucky Ball on 2014-01-29
Delete the EXT* partition you created and just leave free space. When you get to the partitioning section of the install choose 'Something Else'. You should see the free space there and it should allow you to create your partitions. 

I presume you are not using EFI? In that case, you are limited to four partitions per physical disk. These can be a combination of primary and extended partitions. That could be your problem. If you already have four partitions, you aren't going anywhere.

If you have four partitions then you are going to need to delete one and do some thinking and shrinking. Manipulate Win partitions with Win software and Ubuntu partitions with Ubuntu (but you don't have any of them yet).

* Just checked your boot info script and if you're attempting to install on sda, then yes, that's your problem; you already have four partitions. 

Delete the empty one and my first suggestion should work as you'll then only have three partitions. When you choose 'Something Else' to manually partition first thing to do is create an extended partition using the free space. Install Ubuntu to logical partitions inside the extended. You are going to need the partitions / (15Gb at least) and /swap (2Gb or size of RAM if you hibernate) at least. 

Good luck.

---

### Post by fantab on 2014-01-29
> **benjamin9 said:**
> I am trying to install 13.10 on HP e9300z which has Windows 7 installed. 
I shrank my existing partition to create free space and then formatted it as ext4. I then reboot and run off the usb which has the iso. It boots to the installation screen fine and when I come to the installion type screen there are no partitions to select. ...............
 I tried removing dmraid but that did not change and thing. I've played around with different ways of formatting the partitions but have had no success. Anyone have any ideas?

Is your Windows 'Hibernating'? If it is then _Disable Hibernation_.
Check your BIOS for IntelSRT, if it is enabled then _Disable IntelSRT_. On some computers IntelSRT can be found in Windows Programs.

Boot with Live Ubuntu and post the output of the following commands:
```
sudo parted -l
sudo fdisk -l
```

Post a screen shot of your HDD partitions from 'Windows Disk Management'.

---

### Post by oldfred on 2014-01-29
You are showing some sort of RAID. Was BIOS set in RAID mode? Or Intel SRT as suggested above?

This is often BIOS RAID or Intel SRT:
Disk /dev/mapper/pdc_bcgfabgecg

You usually need to remove RAID settings on drive to get Ubuntu to install if Intel SRT. If not running RAID and have only one drive, it may also better to remove RAID, but otherwise it may cause issues.

Whatever you do the first thing you need to do is a full backup of Windows.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

