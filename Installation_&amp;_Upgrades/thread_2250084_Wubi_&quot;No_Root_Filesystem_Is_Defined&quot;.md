---
title: "Wubi &quot;No Root Filesystem Is Defined&quot;"
date: 2014-10-26
forum: Installation &amp; Upgrades
---

### Post by Dima_K. on 2014-10-26
Hello all,
Iam a new linux user, trying to install ubuntu over the WIN7 with wubi.
When I boot to linux for the first time, "No Root Filesystem is Defined" message appears preventing the installation completion...

There are some solutions here on the forum, but I afraid to apply the before I get the second opinion on my boot-info-script.

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.
 => No known boot loader is installed in the MBR of 
    /dev/mapper/isw_cjcgejjbjf_Dev_Cache.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 1342200 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg

isw_cjcgejjbjf_Dev_Cache1: _____________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_cjcgejjbjf_Dev_Cache2: _____________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_cjcgejjbjf_Dev_Cache3: _____________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_cjcgejjbjf_Dev_Cache4: _____________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    25,767,935    25,686,016   7 NTFS / exFAT / HPFS
/dev/sda3          25,767,936   903,548,927   877,780,992   7 NTFS / exFAT / HPFS
/dev/sda4         903,548,928   976,764,927    73,216,000   f W95 Extended (LBA)
/dev/sda5         903,550,976   976,764,927    73,213,952   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 29.8 GiB, 32017047552 bytes, 62533296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    16,775,167    16,773,120  84 OS/2 hidden C: drive


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1.9 GiB, 2063597056 bytes, 4030463 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *            128     4,030,335     4,030,208   7 NTFS / exFAT / HPFS


Drive: isw_cjcgejjbjf_Dev_Cache _____________________________________________________________________

Disk /dev/mapper/isw_cjcgejjbjf_Dev_Cache: 21.8 GiB, 23422173184 bytes, 45746432 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.
/dev/mapper/isw_cjcgejjbjf_Dev_Cache1    ?           224    14,483,679    14,483,456  40 Venix 80286
/dev/mapper/isw_cjcgejjbjf_Dev_Cache2         19,988,480 1,972,568,063 1,952,579,584   0 Empty
/dev/mapper/isw_cjcgejjbjf_Dev_Cache3                  0 4,294,901,759 4,294,901,760   0 Empty
/dev/mapper/isw_cjcgejjbjf_Dev_Cache4    ? 4,067,426,176 4,067,426,843           668  a9 NetBSD

/dev/mapper/isw_cjcgejjbjf_Dev_Cache1 overlaps with /dev/mapper/isw_cjcgejjbjf_Dev_Cache3
/dev/mapper/isw_cjcgejjbjf_Dev_Cache2 ends after the last sector of /dev/mapper/isw_cjcgejjbjf_Dev_Cache
/dev/mapper/isw_cjcgejjbjf_Dev_Cache2 overlaps with /dev/mapper/isw_cjcgejjbjf_Dev_Cache3
/dev/mapper/isw_cjcgejjbjf_Dev_Cache3 ends after the last sector of /dev/mapper/isw_cjcgejjbjf_Dev_Cache
/dev/mapper/isw_cjcgejjbjf_Dev_Cache3 overlaps with /dev/mapper/isw_cjcgejjbjf_Dev_Cache4
/dev/mapper/isw_cjcgejjbjf_Dev_Cache4 ends after the last sector of /dev/mapper/isw_cjcgejjbjf_Dev_Cache

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5450-4444                              vfat       DellUtility
/dev/sda2        AE08DF1408DEDB03                       ntfs       RECOVERY
/dev/sda3        74DAE2CDDAE28B26                       ntfs       OS
/dev/sda5        0CB07942B07932F6                       ntfs       Ubuntu
/dev/sdb1                                                          
/dev/sdc1        E0701D86701D6516                       ntfs       UUI

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/mapper/isw_cjcgejjbjf_Dev_Cache

00000000  49 6e 74 65 6c 20 49 4d  53 4d 20 4e 56 20 43 61  |Intel IMSM NV Ca|
00000010  63 68 65 20 43 66 67 2e  20 53 69 67 2e 20 20 20  |che Cfg. Sig.   |
00000020  06 00 aa 00 4a 01 00 00  01 00 00 00 00 00 00 00  |....J...........|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 a9 3e 7d 00 01 00  |...........>}...|
000000b0  03 00 41 54 35 39 32 31  56 33 33 47 45 39 56 31  |..AT5921V33GE9V1|
000000c0  00 00 bc fd 2b b8 45 02  00 00 7b 32 dc 83 bf 5a  |....+.E...{2...Z|
000000d0  6e 01 18 b8 0f 5a b9 da  e4 fb bc 54 7d b0 34 40  |n....Z.....T}.4@|
000000e0  65 f2 4a d6 0c 5f ac 27  f9 65 c0 e5 da 86 26 49  |e.J.._.'.e....&I|
000000f0  33 7d ba 5d b8 3c 95 74  12 3a 32 48 ae 27 36 b6  |3}.].<.t.:2H.'6.|
00000100  c8 fb 27 01 80 f8 ff ff  a8 cb dc 08 80 fa ff ff  |..'.............|
00000110  00 00 00 00 00 00 00 00  c8 fb 27 01 80 f8 ff ff  |..........'.....|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  90 cf dc 08 80 fa ff ff  55 2f 36 3d fc 2c a1 d0  |........U/6=.,..|
00000140  ea fc 37 73 4a 8f 8a ef  c8 4b 00 c2 00 00 00 4b  |..7sJ....K.....K|
00000150  01 00 01 00 00 00 00 00  12 01 00 d4 01 00 00 00  |................|
00000160  26 02 00 e7 02 00 00 e7  26 02 20 00 00 00 00 00  |&.......&. .....|
00000170  01 00 00 00 00 00 08 7c  aa 02 49 ff ff ff ff ff  |.......|..I.....|
00000180  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
00000190  ff ff ff ff ff ff 30 01  00 00 00 00 80 01 20 01  |......0....... .|
000001a0  00 00 00 40 22 00 00 20  00 00 00 00 00 00 ad ed  |...@".. ........|
000001b0  e3 3c ad ed e3 3c 00 00  00 00 00 70 27 02 a0 00  |.<...<.....p'...|
000001c0  00 00 40 00 00 00 e0 00  00 00 00 00 dd 00 00 00  |..@.............|
000001d0  00 00 00 00 00 00 00 00  31 01 00 00 62 74 00 00  |........1...bt..|
000001e0  10 37 00 00 00 00 00 00  00 00 00 00 ff ff c0 ff  |.7..............|
000001f0  f9 2d a9 02 00 00 80 ff  6f f2 9c 02 00 00 80 ff  |.-......o.......|
00000200

Unknown BootLoader on isw_cjcgejjbjf_Dev_Cache1


Unknown BootLoader on isw_cjcgejjbjf_Dev_Cache2


Unknown BootLoader on isw_cjcgejjbjf_Dev_Cache3


Unknown BootLoader on isw_cjcgejjbjf_Dev_Cache4



=============================== StdErr Messages: ===============================

hexdump: sda1/??@\E1?.\C7: Input/output error
hexdump: sda1/??@\E1?.\C7: Input/output error
hexdump: sda1/??@\E1?.\C7: Input/output error
hexdump: sda1/\EE?.?: Input/output error
hexdump: sda1/\EE?.?: Input/output error
hexdump: sda1/\EE?.?: Input/output error
hexdump: sda1/0000.1s: Input/output error
hexdump: sda1/0000.1s: Input/output error
hexdump: sda1/0000.1s: Input/output error
hexdump: sda1/16s.s: Input/output error
hexdump: sda1/16s.s: Input/output error
hexdump: sda1/16s.s: Input/output error
hexdump: sda1/?3\A03\F76\E4.\F7: Input/output error
hexdump: sda1/?3\A03\F76\E4.\F7: Input/output error
hexdump: sda1/?3\A03\F76\E4.\F7: Input/output error
hexdump: sda1/456789ab.cde: Input/output error
hexdump: sda1/456789ab.cde: Input/output error
hexdump: sda1/456789ab.cde: Input/output error
hexdump: sda1/c%02d%c.%2d: Input/output error
hexdump: sda1/c%02d%c.%2d: Input/output error
hexdump: sda1/c%02d%c.%2d: Input/output error
hexdump: sda1/COND.pm: Input/output error
hexdump: sda1/COND.pm: Input/output error
hexdump: sda1/COND.pm: Input/output error
hexdump: sda1/d%c%02d.%02: Input/output error
hexdump: sda1/d%c%02d.%02: Input/output error
hexdump: sda1/d%c%02d.%02: Input/output error
hexdump: sda1/?F?6\FA`.6\EE: Input/output error
hexdump: sda1/?F?6\FA`.6\EE: Input/output error
hexdump: sda1/?F?6\FA`.6\EE: Input/output error
hexdump: sda1/ict$prin.ter: Input/output error
hexdump: sda1/ict$prin.ter: Input/output error
hexdump: sda1/ict$prin.ter: Input/output error
hexdump: sda1/n=: Input/output error
hexdump: sda1/n=: Input/output error
hexdump: sda1/n=: Input/output error
hexdump: sda1/p\E2\A0.?f: Input/output error
hexdump: sda1/p\E2\A0.?f: Input/output error
hexdump: sda1/p\E2\A0.?f: Input/output error
hexdump: sda1/r-h-s-a-: Input/output error
hexdump: sda1/r-h-s-a-: Input/output error
hexdump: sda1/r-h-s-a-: Input/output error
hexdump: sda1/s..%s: Input/output error
hexdump: sda1/s..%s: Input/output error
hexdump: sda1/s..%s: Input/output error
hexdump: sda1/s.%s%: Input/output error
hexdump: sda1/s.%s%: Input/output error
hexdump: sda1/s.%s%: Input/output error
hexdump: sda1/st.lev: Input/output error
hexdump: sda1/st.lev: Input/output error
hexdump: sda1/st.lev: Input/output error
hexdump: sda1/ty.del: Input/output error
hexdump: sda1/ty.del: Input/output error
hexdump: sda1/ty.del: Input/output error
hexdump: sda1/untry.WS: Input/output error
hexdump: sda1/untry.WS: Input/output error
hexdump: sda1/untry.WS: Input/output error
hexdump: sda1/y.y_o: Input/output error
hexdump: sda1/y.y_o: Input/output error
hexdump: sda1/y.y_o: Input/output error
/home/ubuntu/Downloads/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
cat: /tmp/BootInfo-kB9KCmuO/Tmp_Log: No such file or directory
hexdump: /dev/mapper/isw_cjcgejjbjf_Dev_Cache1: No such file or directory
hexdump: /dev/mapper/isw_cjcgejjbjf_Dev_Cache1: No such file or directory
hexdump: /dev/mapper/isw_cjcgejjbjf_Dev_Cache2: No such file or directory
hexdump: /dev/mapper/isw_cjcgejjbjf_Dev_Cache2: No such file or directory
hexdump: /dev/mapper/isw_cjcgejjbjf_Dev_Cache3: No such file or directory
hexdump: /dev/mapper/isw_cjcgejjbjf_Dev_Cache3: No such file or directory
hexdump: /dev/mapper/isw_cjcgejjbjf_Dev_Cache4: No such file or directory
hexdump: /dev/mapper/isw_cjcgejjbjf_Dev_Cache4: No such file or directory
  No volume groups found



```

Appreciate Your help !
Dima.

---

### Post by sudodus on 2014-10-26
Welcome to the Ubuntu Forums :-)

Wubi is no longer supported and developed because it does not work with Windows 8. It was a nice way to test Ubuntu, but not intended for regular usage. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2229766"]
Forums Staff recommendations on WUBI[/URL]

I suggest that you try it live, and then make a dual boot installation. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by oldfred on 2014-10-26
Is this an UltraBook?
You show /dev/mapper mounts in sdb a 29GB drive.

It does look like a BIOS/MBR install of Windows otherwise, but the Ubuntu desktop installer does not do RAID and Intel SRT which is used for Ultrabooks to implement the cache somehow uses RAID configuration.

---

### Post by Dima_K. on 2014-10-26
Yes, actually it is DELL XPS 14 ultrabook.I tried to disable the acceleration for "Intel rapid storage" in Windows (thought it migth help some way) and also, I ran fixparts.

Here is another thing I have noticed:

I created the new partition of 34.9G for ubuntu in Windows. However, there are two partitions with this size in sudo fdisk -l /dev/sda. sda4 seems to be unused and it overlaps with sda5. Should I consider to delete sda4 ??


```

ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xc1e76092

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1              63     80324     80262  39.2M de Dell Utility
/dev/sda2  *        81920  25767935  25686016  12.3G  7 HPFS/NTFS/exFAT
/dev/sda3        25767936 903548927 877780992 418.6G  7 HPFS/NTFS/exFAT
/dev/sda4       903548928 976764927  73216000  34.9G  f W95 Ext'd (LBA)
/dev/sda5       903550976 976764927  73213952  34.9G  7 HPFS/NTFS/exFAT

Partition 2 does not start on physical sector boundary.


```

---

### Post by westie457 on 2014-10-26
> [COLOR=#000000]I created the new partition of 34.9G for ubuntu in Windows. However, there are two partitions with this size in sudo fdisk -l /dev/sda. sda4 seems to be unused and it overlaps with sda5. Should I consider to delete sda4 ??[/COLOR]

Short answer** NO. **Leave these as they are if you are preparing for a full dual-boot.

If you delete SDA4 you will remove SDA5 at the same time. SDA4 is an 'Extended Partition' which is a container for 'Logical Partitions', it is capable of holding around 100 - or more - partitions.

It might be an idea to shrink SDA5 by about 2 GB to facilitate the creation of a 'Swap Partition'.

If SDA5 is/was the area used for the "wubi' installation then empty it by booting Windows and using 'Remove a Program' in the Control Panel.

---

### Post by oldfred on 2014-10-27
If not using the hibernation or Intel SRT, some users have installed / (root) to the SSD and made Ubuntu very fast. Others have re-enabled the SRT after install of Ubuntu to hard drive.

        Intel Smart Response Technology
[http://mjg59.dreamwidth.org/26022.html](http://mjg59.dreamwidth.org/26022.html)
For GPT systems, this needs to have a type GUID of D3BFE2DE-3DAF-11DF-BA-40-E3A556D89593. 
For MBR systems, you need a partition type of 0x84[2].
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)


 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

 Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)


 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

