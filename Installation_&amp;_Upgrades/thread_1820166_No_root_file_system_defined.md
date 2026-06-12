---
title: "No root file system defined"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by Fusilli Jerry on 2011-08-07
Hi folks,

After having problems upgrading a previously working but old Ubuntu installation as [described in this post]("http://ubuntuforums.org/showthread.php?t=1819836"), I decided the easiest thing to do was probably just uninstall Ubuntu and do a fresh install of the latest version.

Here's what I did:

[LIST=1]
[*]Uninstall Ubuntu from the Add / Remove programs in Windows XP.
[*]Remove the C:\wubildr.mbr = "Ubuntu" line from the boot.ini.
[*]Reboot Windows XP and confirm the old Ubuntu files are gone and Windows has reclaimed the file space.
[*]Download and install the latest wubi.exe.
[*]Install Ubuntu using wubi to the same disk as last time, though this time I allocated 10 GB instead of 30 GB.
[*]The install seemed to go well and I was prompted to reboot to finish installing.
[*]Selected Ubuntu at the beginning of the boot and Ubuntu seemed to be completing the install.
[*]That's when I received the following error:
[/LIST]

> Verifying the installation configuration
No root file system defined
Please correct this from the partitioning menuI'm not sure if it will be helpful but I'm including the last few dozen lines from the wubi-11.04-rev211.log I found in the Windows Temp folder.

```
08-07 09:43 DEBUG  TaskList: ## Finished extract_kernel
08-07 09:43 DEBUG  TaskList: ## Running choose_disk_sizes...
08-07 09:43 DEBUG  WindowsBackend: total size=10000
  root=9744
  swap=256
  home=0
  usr=0
08-07 09:43 DEBUG  TaskList: ## Finished choose_disk_sizes
08-07 09:43 DEBUG  TaskList: ## Running create_preseed...
08-07 09:43 DEBUG  TaskList: ## Finished create_preseed
08-07 09:43 DEBUG  TaskList: ## Running modify_bootloader...
08-07 09:43 DEBUG  TaskList: New task modify_bootini
08-07 09:43 DEBUG  TaskList: ### Running modify_bootini...
08-07 09:43 DEBUG  WindowsBackend: modify_bootini C:
08-07 09:43 DEBUG  TaskList: ### Finished modify_bootini
08-07 09:43 DEBUG  TaskList: New task modify_bootini
08-07 09:43 DEBUG  TaskList: ### Running modify_bootini...
08-07 09:43 DEBUG  WindowsBackend: modify_bootini D:
08-07 09:43 DEBUG  WindowsBackend: Could not find boot.ini D:\boot.ini
08-07 09:43 DEBUG  TaskList: ### Finished modify_bootini
08-07 09:43 DEBUG  TaskList: New task modify_bootini
08-07 09:43 DEBUG  TaskList: ### Running modify_bootini...
08-07 09:43 DEBUG  WindowsBackend: modify_bootini G:
08-07 09:43 DEBUG  WindowsBackend: Could not find boot.ini G:\boot.ini
08-07 09:43 DEBUG  TaskList: ### Finished modify_bootini
08-07 09:43 DEBUG  TaskList: New task modify_bootini
08-07 09:43 DEBUG  TaskList: ### Running modify_bootini...
08-07 09:43 DEBUG  WindowsBackend: modify_bootini H:
08-07 09:43 DEBUG  WindowsBackend: Could not find boot.ini H:\boot.ini
08-07 09:43 DEBUG  TaskList: ### Finished modify_bootini
08-07 09:43 DEBUG  TaskList: ## Finished modify_bootloader
08-07 09:43 DEBUG  TaskList: ## Running modify_grub_configuration...
08-07 09:43 DEBUG  TaskList: ## Finished modify_grub_configuration
08-07 09:43 DEBUG  TaskList: ## Running create_virtual_disks...
08-07 09:43 DEBUG  Virtualdisk:  Creating virtual disk D:\ubuntu\disks\root.disk of 9744MB
08-07 09:43 DEBUG  Virtualdisk:  Creating virtual disk D:\ubuntu\disks\swap.disk of 256MB
08-07 09:43 DEBUG  TaskList: ## Finished create_virtual_disks
08-07 09:43 DEBUG  TaskList: ## Running uncompress_files...
08-07 09:43 DEBUG  WindowsBackend: compact D:\ubuntu\install\boot /U /A /F
08-07 09:43 DEBUG  WindowsBackend: compact D:\ubuntu\install\boot\*.* /U /A /F
08-07 09:43 DEBUG  TaskList: ## Finished uncompress_files
08-07 09:43 DEBUG  TaskList: ## Running eject_cd...
08-07 09:43 DEBUG  TaskList: ## Finished eject_cd
08-07 09:43 DEBUG  TaskList: # Finished tasklist
08-07 09:43 INFO   root: Almost finished installing
08-07 09:43 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\JUSTIN~1\LOCALS~1\Temp\pyl98.tmp\translations, languages=['en_US', 'en']
08-07 09:43 INFO   root: Finished installation
08-07 09:43 INFO   root: Rebooting
08-07 09:43 DEBUG  TaskList: # Running tasklist...
08-07 09:43 DEBUG  TaskList: ## Running reboot...
08-07 09:43 DEBUG  TaskList: ## Finished reboot
08-07 09:43 DEBUG  TaskList: # Finished tasklist
08-07 09:43 DEBUG  root: application.quit
08-07 09:43 DEBUG  WindowsFrontend: frontend.quit
08-07 09:43 DEBUG  WindowsFrontend: frontend.on_quit
08-07 09:43 DEBUG  root: application.on_quit
08-07 09:43 INFO   root: sys.exit
```

Any advice on how to proceed is greatly appreciated.

---

### Post by Fusilli Jerry on 2011-08-07
I've seen people recommend running the boot_info_script.sh so I burned Ubuntu 11.04 onto a CD-ROM and booted into the OS using the "Try Ubuntu" mode.  I ran boot_info_script.sh and posted the results below.

Any advice on how to proceed is much appreciated.  I'm at a loss on what to do now.  Many thanks.

[HTML]                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Plop is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.
 => Plop is installed in the MBR of /dev/mapper/isw_dehdccaejc_ARRAY.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

isw_dehdccaejc_ARRAY1: _________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

isw_dehdccaejc_ARRAY2: _________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr /wubildr.mbr

isw_dehdccaejc_ARRAY3: _________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

isw_dehdccaejc_ARRAY3/Wubi: ____________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_dehdccaejc_ARRAY4: _________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2    *        112,455   224,652,959   224,540,505   7 NTFS / exFAT / HPFS
/dev/sda3         224,669,025   302,744,924    78,075,900   7 NTFS / exFAT / HPFS
/dev/sda4         302,744,925   312,480,314     9,735,390  db CP/M / CTOS / ...


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63   488,392,064   488,392,002   7 NTFS / exFAT / HPFS


Drive: isw_dehdccaejc_ARRAY _____________________________________________________________________

Disk /dev/mapper/isw_dehdccaejc_ARRAY: 160.0 GB, 159996968960 bytes
255 heads, 63 sectors/track, 19451 cylinders, total 312494080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_dehdccaejc_ARRAY1                 63       112,454       112,392  de Dell Utility
/dev/mapper/isw_dehdccaejc_ARRAY2   *        112,455   224,652,959   224,540,505   7 NTFS / exFAT / HPFS
/dev/mapper/isw_dehdccaejc_ARRAY3        224,669,025   302,744,924    78,075,900   7 NTFS / exFAT / HPFS
/dev/mapper/isw_dehdccaejc_ARRAY4        302,744,925   312,480,314     9,735,390  db CP/M / CTOS / ...


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_dehdccaejc_ARRAY1 07D6-0110                              vfat       DellUtility
/dev/mapper/isw_dehdccaejc_ARRAY2 A4AC851FAC84ECDC                       ntfs       
/dev/mapper/isw_dehdccaejc_ARRAY3 9680D99B80D981E3                       ntfs       Backup
/dev/mapper/isw_dehdccaejc_ARRAY4                                        vfat       DellRestore
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 
/dev/sdc1        D27431CF7431B6D7                       ntfs       Iomega HDD
/dev/sdd1        BA71000C70FFCD5F                       ntfs       SignatureMini

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_dehdccaejc_ARRAY
isw_dehdccaejc_ARRAY1
isw_dehdccaejc_ARRAY2
isw_dehdccaejc_ARRAY3
isw_dehdccaejc_ARRAY4

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


======================= isw_dehdccaejc_ARRAY2/boot.ini: ========================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda3


Unknown BootLoader on sda4


Unknown BootLoader on isw_dehdccaejc_ARRAY1

00000000  eb 4a 90 44 65 6c 6c 20  38 2e 30 00 02 04 01 00  |.J.Dell 8.0.....|
00000010  02 00 02 00 00 f8 6e 00  3f 00 ff 00 3f 00 00 00  |......n.?...?...|
00000020  08 b7 01 00 80 00 29 10  01 d6 07 44 65 6c 6c 55  |......)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 00 00  |tilityFAT16   ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 30 33 c0 8e d0  |...........03...|
00000050  bc 00 07 fc b9 80 00 8e  d8 be 00 7c b8 00 20 8e  |...........|.. .|
00000060  c0 33 ff f3 66 a5 ea 6b  00 00 20 8e d8 b8 01 02  |.3..f..k.. .....|
00000070  b9 01 00 b6 00 8a 16 24  00 bb 00 02 cd 13 0f 82  |.......$........|
00000080  e0 00 80 3e c2 03 06 74  0e c6 06 c2 03 06 b8 01  |...>...t........|
00000090  03 cd 13 0f 82 cb 00 66  0f b7 06 16 00 66 d1 e0  |.......f.....f..|
000000a0  66 40 66 03 06 1c 00 66  a3 3e 00 8b 2e 11 00 89  |f@f....f.>......|
000000b0  2e 44 00 c1 ed 04 e8 cb  00 4d 75 fa b9 0b 00 be  |.D.......Mu.....|
000000c0  ea 01 8b fd f3 a6 74 0f  83 c5 20 ff 0e 44 00 75  |......t... ..D.u|
000000d0  eb be e0 01 e9 8e 00 26  8b 46 1a a3 46 00 66 a1  |.......&.F..F.f.|
000000e0  1c 00 66 40 66 a3 3e 00  c7 06 48 00 00 00 8b 2e  |..f@f.>...H.....|
000000f0  16 00 e8 8f 00 4d 75 fa  c7 06 4a 00 70 00 c7 06  |.....Mu...J.p...|
00000100  48 00 00 00 66 0f b7 06  46 00 66 83 e8 02 66 0f  |H...f...F.f...f.|
00000110  b6 0e 0d 00 66 f7 e1 66  0f b7 0e 16 00 66 d1 e1  |....f..f.....f..|
00000120  66 41 66 03 0e 1c 00 66  03 c1 66 0f b7 0e 11 00  |fAf....f..f.....|
00000130  66 c1 e9 04 66 03 c1 66  a3 3e 00 0f b6 2e 0d 00  |f...f..f.>......|
00000140  e8 41 00 4d 75 fa 8b 36  46 00 b8 00 30 d1 e6 73  |.A.Mu..6F...0..s|
00000150  03 05 00 10 8e c0 26 ad  3d f8 ff 73 0d a3 46 00  |......&.=..s..F.|
00000160  eb a2 be d5 01 e8 0d 00  eb fe 8a 16 24 00 33 ed  |............$.3.|
00000170  ea 00 00 70 00 ac 3c 00  74 09 b4 0e bb 07 00 cd  |...p..<.t.......|
00000180  10 eb f2 c3 66 a1 3e 00  66 33 d2 66 0f b7 0e 18  |....f.>.f3.f....|
00000190  00 66 f7 f1 fe c2 88 16  25 00 32 d2 66 0f b7 0e  |.f......%.2.f...|
000001a0  1a 00 66 f7 f1 8a f2 8b  c8 b8 01 02 c0 e5 06 0a  |..f.............|
000001b0  2e 25 00 86 e9 8a 16 24  00 c4 1e 48 00 cd 13 72  |.%.....$...H...r|
000001c0  a1 66 ff 06 3e 00 81 06  48 00 00 02 75 06 81 06  |.f..>...H...u...|
000001d0  4a 00 00 10 c3 44 69 73  6b 20 65 72 72 6f 72 00  |J....Disk error.|
000001e0  4e 6f 20 6c 6f 61 64 65  72 00 44 45 4c 4c 42 49  |No loader.DELLBI|
000001f0  4f 20 42 49 4e 00 00 00  00 00 00 00 00 00 55 aa  |O BIN.........U.|
00000200

Unknown BootLoader on isw_dehdccaejc_ARRAY3/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
[/HTML]

---

### Post by Fusilli Jerry on 2011-08-08
bump.   anyone have any suggestions on this?  are the results of the boot_info_script.sh helpful in identifying the source of the problem? many thanks!

---

