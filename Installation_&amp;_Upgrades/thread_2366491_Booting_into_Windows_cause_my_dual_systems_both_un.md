---
title: "Booting into Windows cause my dual systems both unbootable."
date: 2017-07-18
forum: Installation &amp; Upgrades
---

### Post by iamlazynic on 2017-07-18
[FONT=lucida sans unicode]Dear all, I have dual boot Win10 and Ubuntu (Ubuntu Gnome 17.04) on my laptop (Dell XPS13). Since I installed Ubuntu I never launched Windows and everything is fine. Today I selected to boot into Windows, then Windows can't function well. I then reboot seeing that it "auto diagnose" and keep rebooting, and rebooting into GNU grub command line (complete black background). Now neither of the two systems can boot. Help help :(   I am writing this on live USB and here is some information that should be useful. Thank you in advance for anyone who is willing to help me!!! Oh, I tried boot-repair using recommand repair mode but didn't work.

I think I know what caused this but I don't know why and how to fix. I have installed Ubuntu along with Win10 before this onw and went well. However, on this machine, I once booted into live USB and used GParted to increase the partition size of my Ubuntu OS (and shrink the size of Win10). I think this is the bad thing I shouldn't have done... 

PS. I would like to use two systems both for different uses. Maybe some master could teach how to make my computer safe so that I can boot into either one freely in the future. :)
[/FONT]
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/fwupx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   mount: unknown filesystem type ''
Failed to open ntfs attribute: No such file or directory
Failed to load $MFT: No such file or directory
Failed to mount '/dev/sda5': No such file or directory
Failed to open ntfs attribute: No such file or directory
Failed to load $MFT: No such file or directory
Failed to mount '/dev/sda5': No such file or directory

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 17.04
    Boot files:        /etc/fstab

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 32800 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   500,118,191   500,118,191  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,026,047     1,024,000 EFI System partition
/dev/sda2       1,026,048     1,107,967        81,920 -
/dev/sda3       1,107,968     1,370,111       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       1,370,112     5,564,415     4,194,304 Windows Recovery Environment (Windows)
/dev/sda5       5,564,416   204,879,871   199,315,456 Data partition (Windows/Linux)
/dev/sda6     472,641,536   482,596,863     9,955,328 Swap partition (Linux)
/dev/sda7     482,596,864   483,518,463       921,600 Windows Recovery Environment (Windows)
/dev/sda8     483,518,464   500,116,143    16,597,680 Windows Recovery Environment (Windows)
/dev/sda9     204,879,872   472,641,535   267,761,664 Data partition (Linux)

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 14.3 GiB, 15376000000 bytes, 30031250 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    30,031,249    30,029,202   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3EFF-CAE1                              vfat       ESP
/dev/sda2        0842-66B8                              vfat       DIAGS
/dev/sda3                                                          
/dev/sda4        DA3E44043E43D7E1                       ntfs       WINRETOOLS
/dev/sda5        DCF84B97F84B6EB8                       ntfs       OS
/dev/sda6        29b05249-1312-49ee-997b-63569f634bfc   swap       
/dev/sda7        5ED4C40CD4C3E3FD                       ntfs       
/dev/sda8        C0E890ECE890E248                       ntfs       PBR Image
/dev/sda9        7eb0e6ab-5e49-4e79-8dac-34e3793e8df8   ext4       Ubuntu
/dev/sdb1        5A93-73E2                              vfat       UBUNTU-GNOM

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda9        /mnt                     ext4       (rw,relatime,data=ordered)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=7eb0e6ab-5e49-4e79-8dac-34e3793e8df8 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=3EFF-CAE1  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda6 during installation
UUID=29b05249-1312-49ee-997b-63569f634bfc none            swap    sw              0       0
UUID=3EFF-CAE1    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

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

menuentry "Try Ubuntu GNOME without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu-gnome.seed boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu GNOME" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu-gnome.seed boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu-gnome.seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash ---
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


================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown GPT Partiton Type
d3ad6b79bf6b9f4db631466eb71a4965
Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 3e 18  |.X.MSDOS5.0...>.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 a0 0f 00 e1 03 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 e1 ca ff 3e 4e  4f 20 4e 41 4d 45 20 20  |..)...>NO NAME  |
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

Unknown BootLoader on sda2

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 01 7e 1b  |.X.MSDOS5.0...~.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 0f 00  |........?.......|
00000020  00 40 01 00 41 02 00 00  00 00 00 00 02 00 00 00  |.@..A...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 b8 66 42 08 4e  4f 20 4e 41 4d 45 20 20  |..).fB.NO NAME  |
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


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-wxbzPLaX/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-wxbzPLaX/Tmp_Log: No such file or directory

```

---

### Post by oldfred on 2017-07-18
You should always be able to boot from UEFI menu. But your Windows boot files/folder is missing from the ESP? Dual booting or install of Ubuntu should never have deleted that. But we can add that back.
And grub only boots working Windows. Which means when Windows updates turn fast start up back on, grub will not work. But you can normally boot Windows from UEFI boot menu and then turn fast start up off again.

And any resize of a NTFS partition requires chkdsk. So best to always use Windows to resize NTFS partitions and immediately reboot into Windows and run chkdsk.

From Ubuntu or any Linux you can only do minor fixes to Windows. Best to have a Windows repair/recovery drive. You can make repair flash drive from any Windows 10 system.
       How to: perform a repair upgrade using the Windows 10 ISO file
[URL="http://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085"]http://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085
[/URL]
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 

I do not know why Ubuntu would stop booting. Is boot mode still set to UEFI boot mode. Are you booting Boot-Repair in UEFI boot mode. You posted bootinfoscript which is also used by Boot-Repair, but Boot-Repair adds additional info in its report. 
Post link to its summary report.

In boot-Repair's advanced mode is the full un-install/reinstall of all of grub and you can check install new kernel. I would run that. But be sure to be in UEFI boot mode.
This also shows screens you see when you boot in BIOS or UEFI boot mode.
      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by iamlazynic on 2017-07-19
Thank you for helping! Here is what I did today: I used a USB Windows installer to reinstall Windows on that partition (I don't have anything valuable on Windows anyway). So now I have a working Win10. Again, I booted a live USB and tried boot-repair getting a same result. Recommand repair in boot-repair runs forever never stop. I quitted it after a long time's wait. 

Clicking "create bootinfo summary" gave me a similar "Boot-Info_xxx.txt" to the one I posted. I am not clear what your "summary report" means and I didn't see a "install new kernel" option. Can you explain more details? :) Thank you very much!

---

### Post by oldfred on 2017-07-19
It looks more like the bootinfoscript report which is also the first third of the Boot-Repair Summary report.
Forum may not be accepting entire report? Plus need to see changes if Windows correctly shown in ESP.  
Best to manually post to pastebin site, if auto post not working. 
Are you using Wired Ethernet, not Wireless?

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by iamlazynic on 2017-07-20
Sorry for late reply. I couldn't wait to use it again so I deleted the previous install and reinstalled Ubuntu. This time it is working and I promise I will never offend Windows again :) My files have backup on the internet so, except that I have to config a lot one more time, the problem is gone (although not solved).

Thank you again @oldfreg. :-D

---

