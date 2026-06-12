---
title: "&quot;no operating system found&quot; on reboot post-install"
date: 2018-11-26
forum: Installation &amp; Upgrades
---

### Post by liverpj on 2018-11-26
Hi 

New to theforum and although I’ve been using lubuntu for a few years now I’m a prettybasic user, so please bear with me J

Background:
·        Laptop:Samsung from c.2010
·        Ihave installed a new 120GB SSD and wanted to install a fresh version of Ubuntumate with no other OS
·        Afterinstall when booting it says “no operating system found”. 
·        Liveversions work aok. 
·        Whenchecking the SSD using a live version of both Ubuntu and Mint mate the OSshowed up. 
·        Itried a fresh install using Mint Mate, with the same result, followed by multipleattempts with both Mint and Ubuntu mate

What I havetried:
·        Changingthe boot order
·        Lookingfor something referencing UEFI/EFI (which I don’t really understand). In BIOS(?)there is an option called “Legacy OS Boot” which can be disabled/enabled; “SelectEnabled to attempt Legacy OS Boot only. Select Disabled to attempt EFI Bootfirst, Legacy OS Boot Second”.
·        InstallingMint mate and choosing the “something else”  then trying to partition as per onlineinstructions – there ended up being quite a lot of partitions I didn’trecognise and no UEFI / EFIpartition options. 
·        Wipingthe SSD using; sudo wipe /dev/sda1 [the only other drive that seemed to showwas the flash drive]

My laptopis still wiping… now on its 3[SUP]rd[/SUP] pass (IDK how many it will do)

It was solong ago that I installed lubuntu that I can’t recall the process, but I’m sureit worked without issue. 

Any ideas? Orany decent noob guides which include advice on how to partition post install? Thereseem to be so many average guides now that it’s hard to see the wood for thetrees.  

Cheers.

---

### Post by liverpj on 2018-11-26
A Duplicate post without the conjoined words - mods if it's possible to delete the first post that would be amazing! Not sure what happened when I pasted.


Hi 

New to the forum and although I&#8217;ve been using lubuntu fora few years now I&#8217;m a pretty basic user, so please bear with me &#9786;

Background: 
&#8226; Laptop: Samsung from c.2010
&#8226; I have installed a new 120GB SSD and wanted to installa fresh version of Ubuntu mate with no other OS
&#8226; After install when booting it says &#8220;no operating systemfound&#8221;. 
&#8226; Live versions work aok. 
&#8226; When checking the SSD using a live version of both Ubuntuand Mint mate the OS showed up. 
&#8226; I tried a fresh install using Mint Mate, with the sameresult, followed by multiple attempts with both Mint and Ubuntu mate

What I have tried:
&#8226; Changing the boot order
&#8226; Looking for something referencing UEFI/EFI (which Idon&#8217;t really understand). In BIOS(?) there is an option called &#8220;Legacy OS Boot&#8221;which can be disabled/enabled; &#8220;Select Enabled to attempt Legacy OS Boot only.Select Disabled to attempt EFI Boot first, Legacy OS Boot Second&#8221;.
&#8226; Installing Mint mate and choosing the &#8220;somethingelse&#8221;  then trying to partition as peronline instructions &#8211; there ended up being quite a lot of partitions I didn&#8217;trecognise and no UEFI / EFI partition options. 
&#8226; Wiping the SSD using; ```
sudo wipe /dev/sda1
``` [the onlyother drive that seemed to show was the flash drive]

My laptop is still wiping&#8230; now on its 3rd pass (IDK howmany it will do)

It was so long ago that I installed lubuntu that I can&#8217;trecall the process, but I&#8217;m sure it worked without issue. 

Any ideas? Or any decent noob guides which include adviceon how to partition post install? There seem to be so many average guides nowthat it&#8217;s hard to see the wood for the trees.

---

### Post by yancek on 2018-11-26
Is there an OS installed on another drive of this computer and if so,  what?
Is/was there an EFI partition on another drive?
When you install, do you select the Erase disk and install option or failing that, leave the default in the install.
Not sure what instructions you followed but, there is very little reason to create more than a / (root filesystem) partition and a /home or /data partition.

---

### Post by liverpj on 2018-11-26
Thanks for replying.

As far as I know the only OS was Lubuntu until I removed the HDD and replaced it with a new SSD - at which point there was no OS.

The laptop originally shipped with Vista. 

Idk if there was an EFI partition on the original HDD - is this something I'll be able to check by plugging the HDD into a Win10 laptop with a dock and USB?

I've tried most of the variations of install. But yes I did try the Erase disk and install option, which still gave me "no operating system found" on restart. 

Re the partions; the guide I followed when I first installed Lubuntu ages ago broke down exactly which ones and what size in relation to the memory. Iirc they were just the one you listed.

The reason I'm after an idiots partion guide is it looks like some people online seem to have had (and I guess solve) the no OS error in relation to dodgy partitioning.

Cheers.

---

### Post by oldfred on 2018-11-26
If from 2010, it will be BIOS only, no UEFI.

Apple used early version EFI when it changed to Intel chips. But PC only changed to newer UEFI when Microsoft released Windows 8 in 2012.  A very few Windows 7 systems just before Windows 8 may have UEFI, but that vendor was probably making sure his UEFI worked.

With BIOS, no operating system found would normally mean grub was not installed to MBR of default boot drive in BIOS drive settings.
If you used something else install option and did not install grub to MBR, drive like sda, not partition like sda1, then system has no boot loader in MBR.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Boot-Repair may be able to fix it, just by installing grub to MBR. But usually best to have someone review report to make sure. Occasionally Boot-Repair does not make correct or best choice automatically. If multiple drives only use Boot-Repair's advanced options.

---

### Post by liverpj on 2018-11-26
Cheers.

I don't have the laptop with me at the moment, but that is really helpful. 

Hopefully by tomorrow its stopped wiping and I'll be able to run through those points.

I didnt install grub.

---

### Post by ubfan1 on 2018-11-26
Since your machine offers EFI/Legacy settings, it may have an early EFI version, pre-secure boot (I have a Lenovo like that, which boots fine ether way).  Set the EFI to preferred, and ensure you have an EFI partition (300M, FAT, ESP flag) and your install media should boot and install in  EFI mode.  Without Windows present, the disk partitioning does not even matter, but gpt makes life easier if you want more than four partitions.  Then the reboot should also be in EFI mode.  Didn't see you list an EFI partition, in the earlier post, so we'll see what the boot-repair report says.

---

### Post by liverpj on 2018-11-27
```
Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for 
    (lvmid/AEIOY4-hK6o-DHZm-42DI-USWe-3s8U-c18Weg/r0ScxD-0gEP-kmt8-rIae-aLok-hl
    b8-dHeKhn)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos diskfilter lvm biosdisk
    ---------------------------------------------------------------------------
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda1: unknown filesystem type ''.

sdb1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda1: unknown filesystem type ''.
mount: /mnt/BootInfo/sdb1: /dev/sdb1 already mounted or mount point busy.

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 3841944. According to the info 
                       in the boot sector, sdb2 has 0 sectors.
    Mounting failed:   mount: /mnt/BootInfo/sda1: unknown filesystem type ''.
mount: /mnt/BootInfo/sdb1: /dev/sdb1 already mounted or mount point busy.
mount: /mnt/BootInfo/sdb2: /dev/sdb2 already mounted or mount point busy.

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   234,440,703   234,438,656  8e Linux LVM


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 31.3 GiB, 33554432000 bytes, 65536000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *              0     3,920,639     3,920,640   0 Empty
/dev/sdb2           3,841,944     3,846,615         4,672  ef EFI (FAT-12/16/32)

/dev/sdb1 overlaps with /dev/sdb2

GUID Partition Table detected, but does not seem to be used.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdb1   +  R              0     3,920,583     3,920,584 Data partition (Windows/Linux)
/dev/sdb2   +  R      3,841,944     3,846,615         4,672 Data partition (Windows/Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/sda1                                                          
/dev/sdb1        2018-07-25-03-37-28-00                 iso9660    Ubuntu-MATE 18.04.1 LTS amd64
/dev/sdb2        0D5F-1DB6                              vfat       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Nov 27 08:44 ata-CT120BX500SSD1_1832E1511B77 -> ../../sda
lrwxrwxrwx 1 root root 10 Nov 27 08:44 ata-CT120BX500SSD1_1832E1511B77-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 Nov 27 08:44 usb-Generic_Flash_Disk_EA9926EC-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Nov 27 08:44 usb-Generic_Flash_Disk_EA9926EC-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Nov 27 08:44 usb-Generic_Flash_Disk_EA9926EC-0:0-part2 -> ../../sdb2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /cdrom                   iso9660    (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f3 06 b4 42 eb 15 eb 02  |...t.f.....B....|
00000070  31 c9 5a 51 b4 08 cd 13  5b 0f b6 c6 40 50 83 e1  |1.ZQ....[...@P..|
00000080  3f 51 f7 e1 53 52 50 bb  00 7c b9 04 00 66 a1 b0  |?Q..SRP..|...f..|
00000090  07 e8 44 00 0f 82 80 00  66 40 80 c7 02 e2 f2 66  |..D.....f@.....f|
000000a0  81 3e 40 7c fb c0 78 70  75 09 fa bc ec 7b ea 44  |.>@|..xpu....{.D|
000000b0  7c 00 00 e8 83 00 69 73  6f 6c 69 6e 75 78 2e 62  ||.....isolinux.b|
000000c0  69 6e 20 6d 69 73 73 69  6e 67 20 6f 72 20 63 6f  |in missing or co|
000000d0  72 72 75 70 74 2e 0d 0a  66 60 66 31 d2 66 03 06  |rrupt...f`f1.f..|
000000e0  f8 7b 66 13 16 fc 7b 66  52 66 50 06 53 6a 01 6a  |.{f...{fRfP.Sj.j|
000000f0  10 89 e6 66 f7 36 e8 7b  c0 e4 06 88 e1 88 c5 92  |...f.6.{........|
00000100  f6 36 ee 7b 88 c6 08 e1  41 b8 01 02 8a 16 f2 7b  |.6.{....A......{|
00000110  cd 13 8d 64 10 66 61 c3  e8 1e 00 4f 70 65 72 61  |...d.fa....Opera|
00000120  74 69 6e 67 20 73 79 73  74 65 6d 20 6c 6f 61 64  |ting system load|
00000130  20 65 72 72 6f 72 2e 0d  0a 5e ac b4 0e 8a 3e 62  | error...^....>b|
00000140  04 b3 07 cd 10 3c 0a 75  f1 cd 18 f4 eb fd 00 00  |.....<.u........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  3c 04 00 00 00 00 00 00  88 06 d9 4a 00 00 80 00  |<..........J....|
000001c0  01 00 00 77 e0 fc 00 00  00 00 00 d3 3b 00 00 fe  |...w........;...|
000001d0  ff ff ef fe ff ff 98 9f  3a 00 40 12 00 00 00 00  |........:.@.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


/dev/sdb1: unknown GPT attributes
1000000000000001

/dev/sdb2: unknown GPT attributes
1000000000000001
Unknown BootLoader on sda1

00000000  55 55 55 55 55 55 55 55  55 55 55 55 55 55 55 55  |UUUUUUUUUUUUUUUU|
*
00000200

Unknown BootLoader on sdb1

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f3 06 b4 42 eb 15 eb 02  |...t.f.....B....|
00000070  31 c9 5a 51 b4 08 cd 13  5b 0f b6 c6 40 50 83 e1  |1.ZQ....[...@P..|
00000080  3f 51 f7 e1 53 52 50 bb  00 7c b9 04 00 66 a1 b0  |?Q..SRP..|...f..|
00000090  07 e8 44 00 0f 82 80 00  66 40 80 c7 02 e2 f2 66  |..D.....f@.....f|
000000a0  81 3e 40 7c fb c0 78 70  75 09 fa bc ec 7b ea 44  |.>@|..xpu....{.D|
000000b0  7c 00 00 e8 83 00 69 73  6f 6c 69 6e 75 78 2e 62  ||.....isolinux.b|
000000c0  69 6e 20 6d 69 73 73 69  6e 67 20 6f 72 20 63 6f  |in missing or co|
000000d0  72 72 75 70 74 2e 0d 0a  66 60 66 31 d2 66 03 06  |rrupt...f`f1.f..|
000000e0  f8 7b 66 13 16 fc 7b 66  52 66 50 06 53 6a 01 6a  |.{f...{fRfP.Sj.j|
000000f0  10 89 e6 66 f7 36 e8 7b  c0 e4 06 88 e1 88 c5 92  |...f.6.{........|
00000100  f6 36 ee 7b 88 c6 08 e1  41 b8 01 02 8a 16 f2 7b  |.6.{....A......{|
00000110  cd 13 8d 64 10 66 61 c3  e8 1e 00 4f 70 65 72 61  |...d.fa....Opera|
00000120  74 69 6e 67 20 73 79 73  74 65 6d 20 6c 6f 61 64  |ting system load|
00000130  20 65 72 72 6f 72 2e 0d  0a 5e ac b4 0e 8a 3e 62  | error...^....>b|
00000140  04 b3 07 cd 10 3c 0a 75  f1 cd 18 f4 eb fd 00 00  |.....<.u........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  3c 04 00 00 00 00 00 00  88 06 d9 4a 00 00 80 00  |<..........J....|
000001c0  01 00 00 77 e0 fc 00 00  00 00 00 d3 3b 00 00 fe  |...w........;...|
000001d0  ff ff ef fe ff ff 98 9f  3a 00 40 12 00 00 00 00  |........:.@.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/3904/mountinfo) leaked on lvs invocation. Parent PID 9453: bash
File descriptor 63 (pipe:[61915]) leaked on lvs invocation. Parent PID 9453: bash

ADDITIONAL INFORMATION :
=================== log of boot-repair 20181127_0844 ===================
boot-repair version : 4ppa65
boot-sav version : 4ppa65
boot-sav-extra version : 4ppa65
glade2script version : 3.2.3~ppa4
grub-probe: error: cannot find a GRUB drive for /dev/sdb1.  Check your device.map.
Warning: The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.
boot-repair is executed in live-session (Ubuntu 18.04.1 LTS, bionic, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu-mate.seed boot=casper quiet splash ---
ls: cannot access '/home/usr/.config': No such file or directory
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount /dev/sda1 : Error code 12
mount -r /dev/sda1 /mnt/boot-sav/sda1
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount -r /dev/sda1 : Error code 12

=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/sdb1: UUID="2018-07-25-03-37-28-00" LABEL="Ubuntu-MATE 18.04.1 LTS amd64" TYPE="iso9660" PTUUID="4ad90688" PTTYPE="dos" PARTUUID="4ad90688-01"
/dev/sdb2: SEC_TYPE="msdos" UUID="0D5F-1DB6" TYPE="vfat" PARTUUID="4ad90688-02"
/dev/sda1: PARTUUID="3d2380de-01"

NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount /dev/sda1 : Error code 12
mount -r /dev/sda1 /mnt/boot-sav/sda1
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount -r /dev/sda1 : Error code 12
ls /sys/firmware/efi/vars : new_var,del_var,Timeout-8be4df61-93ca-11d2-aa0d-00e098032b8c,SmmS3NvsData-8983fd2d-113c-4e2b-8f47-0abfeb20a41a,SetupDTS-c2830c26-e273-4000-8fca-2addcd68d634,PsmAcpi-a41435a6-494a-4799-91fc-edf0406083a6,MokListRT-605dab50-e046-4300-abb6-3dd810dd8b23,MemRestoreVariable-608dc793-15de-4a7f-a0c5-6c29beaf5d23,MTC-eb704011-1402-11d3-8e77-00a0c969723b,MSRVariable-af9ffd67-ec10-488a-9dfc-6cbf5ee22c2e,LangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c,Lang-8be4df61-93ca-11d2-aa0d-00e098032b8c,ErrOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,DXELISTs-6b8483ed-a0a6-476f-b92f-dcae75685bd9,ConOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConInDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,AcpiGlobalVariable-af9ffd67-ec10-488a-9dfc-6cbf5ee22c2e,
Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

=================== efibootmgr -v
Timeout: 10 seconds
No BootOrder is set; firmware will attempt recovery

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot maybe enabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sda1    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sda1.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    not-mmc, no-os,    2048 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:120GB:scsi:512:512:msdos:ATA CT120BX500SSD1:;
1:1049kB:120GB:120GB:::boot, lvm;

BYT;
/dev/sdb:33.6GB:scsi:512:512:unknown:Generic Flash Disk:;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
loop0 loop squashfs   1.8G
loop1 loop squashfs  86.9M
loop2 loop squashfs   7.9M
loop3 loop squashfs  71.7M
loop4 loop squashfs  86.7M
sda   disk          111.8G
sda1  part          111.8G
sdb   disk iso9660   31.3G Ubuntu-MATE 18.04.1 LTS amd64
sdb1  part iso9660    1.9G Ubuntu-MATE 18.04.1 LTS amd64
sdb2  part vfat       2.3M Ubuntu-MATE 18.04.1 LTS amd64

KNAME ROTA RO RM STATE   MOUNTPOINT
loop0    1  1  0         /rofs
loop1    1  1  0         /snap/core/4917
loop2    1  1  0         /snap/pulsemixer/23
loop3    1  1  0         /snap/software-boutique/31
loop4    1  1  0         /snap/ubuntu-mate-welcome/169
sda      0  0  0 running
sda1     0  0  0
sdb      1  0  1 running /cdrom
sdb1     1  0  1
sdb2     1  0  1


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1495740k,nr_inodes=373935,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=303388k,mode=755)
/dev/sdb on /cdrom type iso9660 (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=24,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=14247)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=303384k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/var/lib/snapd/snaps/core_4917.snap on /snap/core/4917 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/pulsemixer_23.snap on /snap/pulsemixer/23 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/software-boutique_31.snap on /snap/software-boutique/31 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/ubuntu-mate-welcome_169.snap on /snap/ubuntu-mate-welcome/169 type squashfs (ro,nodev,relatime,x-gdu.hide)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 drm_dp_aux1 drm_dp_aux2 ecryptfs fb0 fd full fuse hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 initctl input kmsg kvm lightnvm log mapper mcelog media0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdb2 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom userio v4l vfio vga_arbiter vhci vhost-net vhost-vsock video0 zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.5G     0  1.5G   0% /dev
tmpfs          tmpfs     297M  1.4M  295M   1% /run
/dev/sdb       iso9660   1.9G  1.9G     0 100% /cdrom
/dev/loop0     squashfs  1.8G  1.8G     0 100% /rofs
/cow           overlay   1.5G  417M  1.1G  29% /
tmpfs          tmpfs     1.5G   32M  1.5G   3% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     1.5G     0  1.5G   0% /sys/fs/cgroup
tmpfs          tmpfs     1.5G  524K  1.5G   1% /tmp
tmpfs          tmpfs     297M   48K  297M   1% /run/user/999
/dev/loop1     squashfs   87M   87M     0 100% /snap/core/4917
/dev/loop2     squashfs  8.0M  8.0M     0 100% /snap/pulsemixer/23
/dev/loop3     squashfs   72M   72M     0 100% /snap/software-boutique/31
/dev/loop4     squashfs   87M   87M     0 100% /snap/ubuntu-mate-welcome/169

=================== fdisk -l:
Disk /dev/loop0: 1.8 GiB, 1917960192 bytes, 3746016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 86.9 MiB, 91099136 bytes, 177928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 7.9 MiB, 8294400 bytes, 16200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 71.7 MiB, 75120640 bytes, 146720 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 86.7 MiB, 90923008 bytes, 177584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x3d2380de

Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1  *     2048 234440703 234438656 111.8G 8e Linux LVM


Disk /dev/sdb: 31.3 GiB, 33554432000 bytes, 65536000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x4ad90688

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdb1  *          0 3920639 3920640  1.9G  0 Empty
/dev/sdb2       3841944 3846615    4672  2.3M ef EFI (FAT-12/16/32)


No OS or WinEFI system

=================== Recommended repair
The default repair of the Boot-Repair utility will not act on the boot.
```

---

### Post by liverpj on 2018-11-27
Boot report above. Sorry just realised you said paste the link... [http://paste.ubuntu.com/p/gwSRZXz5Pt/](http://paste.ubuntu.com/p/gwSRZXz5Pt/)   [http://paste.ubuntu.com/p/gwSRZXz5Pt/plain/](http://paste.ubuntu.com/p/gwSRZXz5Pt/plain/) 

> BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot maybe enabled.

So my BIOS is EFI-compatible it seems. 

My next steps are:
1. Reinstall Ubuntu using the 'something else' option.
2. Check partitioning is correct
3. check grub is installed / install grub
4. go into BIOS and (in my options) > Select Disabled to attempt EFI Boot first, Legacy OS Boot Second

The bit I'm unsure of is;
> Set the EFI to preferred, and ensure you have an EFI partition (300M,  FAT, ESP flag) and your install media should boot and install in  EFI  mode.

Does the install media mean the version of ubuntu downloaded onto the USB? If so is there a way to verify that? Or am I miss-understanding? 

Thanks,

[IMG]https://ibb.co/TBccKSN[/IMG]

[https://ibb.co/TBccKSN](https://ibb.co/TBccKSN)

---

### Post by yancek on 2018-11-27
"Install Media" would mean the DVD or USB with the Live Ubuntu installer.

BIOS options vary a lot between manufacturers.  If you have an EFI capable system, EFI booting may be the priority but if you want to install EFI, you should be able to disable Legacy/CSM in the BIOS.

It would be simpler if you want EFI to create the EFI partition prior to the install.  You can use GParted which is on the Ubuntu install DVD/USB by simply opening a terminal and typing:  sudo gparted
This should show /dev/sda in the main window.  You currently have only one partition taking up the drive so resize/shrink it by highlighting it in the main window then clicking on the Partition tab at the top and click the Resize option.  Shrink to 200-500MB.  When that finishes, again with this partition highlighted in the main window, click the Partition tab and then the Format to option and select FAT32.  When that finishes, again click the Partition tab and this time select the Manage Flags option and check the boxes next to boot and esp.

You should then be able to boot/install UEFI.  I would suggest reviewing the Ubuntu documentation at the site below, particularly the General Principles and Identifying if Computer boots in UEFI mode.  You can skip over the windows dual boot info as it does not apply in your case but there is a good bit of useful information on UEFI with Ubuntu specifically.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by liverpj on 2018-11-27
Thanks. I'll go through those steps and check out the link. 

I have also been reading this: [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 

I've had quite a few failed installs, but two "successful" ones. Both still showed the no OS error. For the last one I created the below partitions based on the Boot Repair msg (also shown). 

[IMG]https://lfgss.microco.sm/api/v1/files/67b0ae17d242fd076c14a2e4d1132aa698a635a1.png[/IMG]

---

### Post by oldfred on 2018-11-27
You normally do not need a separate partition for /boot.

You need an ESP - efi system partition for UEFI boot.
If gpt partitioned, you need a bios_grub partition for BIOS/CSM/Legacy boot.

I normally make first two partitions the ESP & bios_grub. I started using gpt before UEFI so needed that for old system, and then UEFI became standard and I thought drives may get moved to UEFI system, so started adding both. Even after I got my UEFI system, I still added the bios_grub, but do not think I have used it since.

New UEFI systems, do not have the far from start of disk. That was very old BIOS systems, but some BIOS installs had IDE instead of AHCI for drives or were external drives and behaved similarly. If you use a smaller / in the first 100GB of a drive it did not apply to most systems even then. 

If you post long text, please use Code Tags. Easy to add with Forum's advanced editor and # icon.
Also with Boot-Repair, copy & paste link it gives you to pastebin site. Often report is too long to fully copy.

If partitioning in advance be sure to change from default MBR(msdos) to gpt first. The only time to have msdos, is if Windows is to be installed in BIOS boot mode as then Windows requires dos partitioning. Ubuntu can use gpt with either BIOS or UEFI boot systems. UEFI prefers gpt partitioning.

       Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... Or if drive is blank or you want to erase it.
sudo parted /dev/sda mklabel gpt

---

### Post by liverpj on 2018-11-27
> **yancek said:**
> 
It would be simpler if you want EFI to create the EFI partition prior to the install. 

Unfortunately because the OS is installed I can't do the EFI partition prior to install. No matter what I try the drive won't unmount, so I can't delete the partitions. I've tried another install. 

When I create the EFI at the beginning a small 1MB of free space is automatically created in front of it. Could this be the reason? 

[IMG]https://lfgss.microco.sm/api/v1/files/ce0cb1774259092e2bda21d8ba40565ca0b363da.png[/IMG]


When opening gpart it looks like the EFI has the boot and esp flags and is first:
[IMG]https://lfgss.microco.sm/api/v1/files/93227fbffa8c8ebaa06cf92bf34fb66ee52c6ff5.png[/IMG]

Per pt 2. in this link: [https://help.ubuntu.com/community/UEFI#Installing_Ubuntu_for_Single_Boot_with_a_Random_Boot_Mode](https://help.ubuntu.com/community/UEFI#Installing_Ubuntu_for_Single_Boot_with_a_Random_Boot_Mode) I have also tried disabling the BIOS menu items that look like they might correspond. 
> Installing Ubuntu for Single Boot with a Random Boot Mode
...
2. [LEFT][COLOR=#333333][FONT="Ubuntu"]In your firmware, [/FONT][/COLOR][/LEFT][disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9")[LEFT][COLOR=#333333][FONT="Ubuntu"] and [/FONT][/COLOR][/LEFT][Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6")[LEFT][COLOR=#333333][FONT="Ubuntu"] (SRT). [/FONT][/COLOR][/LEFT]

As to whether ubuntu was installed in UEFI mode I tried this:

> [h=1]Identifying if an Ubuntu has been installed in UEFI mode[/h][LEFT][COLOR=#333333][FONT="Ubuntu"][/FONT][/COLOR][COLOR=#333333][FONT=&amp][/FONT][/COLOR][COLOR=#333333][FONT=&amp][/FONT][/COLOR][COLOR=#333333][FONT=&amp]An Ubuntu installed in UEFI mode can be detected the following way: [LEFT][FONT=&amp][/FONT][/LEFT][/FONT][/COLOR][/LEFT]
[LIST]
[*=left]its /etc/fstab file contains an UEFI partition (mount point: /boot/efi)
[/LIST]

...but the only reference to a [LEFT][COLOR=#333333][FONT=Verdana]fstab file I found was in what I guess was the live version as I couldn't access the SSD from Computer due to > Unable to mount location - can't mount file:

[/FONT][/COLOR][/LEFT]

---

### Post by oldfred on 2018-11-27
A bit of free space is normal. It used to be small and gparted did not show it. But newer larger drives & SSD require drives to be aligned. Also partition table is at both start & end of drive (if gpt) which is not shown.

If drive is not gpt, you can convert to gpt.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

How you boot install media, UEFI or BIOS is then how it installs.

---

### Post by liverpj on 2018-11-27
Thanks for the comments and for fixed the long text on the earlier post. 

I've wiped the SSD and added the partitions you and yancek suggested:

Should I go ahead and install now, or restart? 

I've read your link, but tbh it is over my head, and without pretty idiot-proof instructions I can't really work out what actions to take. 

Cheers. 

ps re the other poster's comments on LVM ( [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm) ) how does that interact with this process? Is it something I should have done before I created the two files below?

[IMG]https://lfgss.microco.sm/api/v1/files/1f7984249324d9be5547a6f07ca1a76f6e4ec32a.png[/IMG]
[LEFT][COLOR=#000000][FONT=Ubuntubeta]You need an ESP - efi system partition for UEFI boot.[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]If gpt partitioned, you need a bios_grub partition for BIOS/CSM/Legacy boot.[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntubeta]I normally make first two partitions the ESP & bios_grub. I started using gpt before UEFI so needed that for old system, and then UEFI became standard and I thought drives may get moved to UEFI system, so started adding both. Even after I got my UEFI system, I still added the bios_grub, but do not think I have used it since.[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntubeta]New UEFI systems, do not have the far from start of disk. That was very old BIOS systems, but some BIOS installs had IDE instead of AHCI for drives or were external drives and behaved similarly. If you use a smaller / in the first 100GB of a drive it did not apply to most systems even then. [/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntubeta]If partitioning in advance be sure to change from default MBR(msdos) to gpt first. The only time to have msdos, is if Windows is to be installed in BIOS boot mode as then Windows requires dos partitioning. Ubuntu can use gpt with either BIOS or UEFI boot systems. UEFI prefers gpt partitioning.[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntubeta]       Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... Or if drive is blank or you want to erase it.[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta]sudo parted /dev/sda mklabel gpt[/FONT][/COLOR][/LEFT]

---

### Post by oldfred on 2018-11-27
You can add / (root) of 25GB or so and /home for rest of drive. You now do not need swap partition as installer creates a swap file. But if you have swap partition it will use that.

Is drive gpt?
sudo parted -l
Should be gpt, not msdos or dos.

Then you have to boot live installer in UEFI boot mode and use Something Else install option. You choose (change button) / and specify ext4 & /, and choose /home and ext4.

---

### Post by liverpj on 2018-11-27
> **oldfred said:**
> 
Is drive gpt?

It says; > Partition Table: gpt so, yes?

There is also a warning; 
> The driver description says the physical block size is 2048 bytes, but Linuz says it is 512 bytes

---

### Post by oldfred on 2018-11-27
That error is usually from your flash drive live installer. It is not typically a standard partitioned drive but a hybrid DVD image that can be on flash drive.
You can ignore error on block size.

What brand/model system?
Some just do not want to boot Ubuntu, but only want to boot Windows. But we have multiple work arounds, depending on configuration.

---

### Post by liverpj on 2018-11-27
The laptop is a Samsung x420 previously running lubuntu aok, but originally shipped with Vista (I think). 

The new SSD is a Crucial BX500 120GB 3D NAND SATA 2.5-inch SSD.

---

### Post by liverpj on 2018-11-27
Another crashed install (wondering if I should try and do the simiplest install with no updates, etc.). 

Below is the partitioning prior to install.

On restart: > Operating System not found

This is killing me! The laptop seems to be running on the live version really nicely too ;(

---

### Post by oldfred on 2018-11-27
Many SSD need firmware updates, do not know about Crucial specifically.

Note sure if this is related or just a Samsung SSD?
       Asus/Samsung problem with every NVME SSD and G752! 
[https://ubuntuforums.org/showthread.php?t=2307273&p=13584551#post13584551](https://ubuntuforums.org/showthread.php?t=2307273&p=13584551#post13584551)
[http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04](http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04) 
    
       Phoenix SecureCore Tiano bios setup and secure boot is greyed out. You need to set a Supervisor Password in the Security tab
Samsung w/ Phoenix Tiano SecureCore
[http://askubuntu.com/questions/760102/ubuntu-16-04-error-installing-grub/762267#762267](http://askubuntu.com/questions/760102/ubuntu-16-04-error-installing-grub/762267#762267)
Samsung Ativ Book 9 Plus UEFI Install Troubles - manual copy of grub to /EFI/Boot
[http://ubuntuforums.org/showthread.php?t=2230919](http://ubuntuforums.org/showthread.php?t=2230919) 
    
Boot-Repair now does a copy of shimx64.efi to /EFI/Boot and renames it to bootx64.efi so you can boot hard drive entry in UEFI, not ubuntu entry.

---

### Post by liverpj on 2018-11-27
I tried a new better quality USB flash drive with a fresh install of regular ubuntu what ever the latest version is. 

I've gone for the basic default install. 

One crash. Second try brought up this error in relation to Grub:[ATTACH=CONFIG]281784[/ATTACH]

---

### Post by liverpj on 2018-11-27
Still no joy :(

I tried to get it to install via Legacy / BIOS. Same no OS found. 

I am wondering if I try installing an older version of ubuntu and then updating. 

Could that work? Say if I found and downloaded 14 and (assuming it works) I then update the software once installed?

After that my only thought is to try and cloan my HDD and go back to lubuntu... 

...which is a shame as I really liked ubuntu mate. Not that keen on regular ubuntu with all the big sidebar icons. 

Really at a total loss as to what to do. Here is another screenshot from gpart after the non-EFI install. Unfortunately I couldn't run boot-repair in non-EFI mode so am unable to print a report.
[ATTACH=CONFIG]281785[/ATTACH]

[B]EDIT:
Not 100% but with morning fresh eyes, it looks like it may have *not* installed in Legacy mode. Going to give it another shot trying to install in legacy mode. 

The screenshots below were taken with the Boot to Legacy mode first selected in BIOS. 
[ATTACH=CONFIG]281792[/ATTACH] [/B]
[ATTACH=CONFIG]281793[/ATTACH]

*EDIT 2:*
[I]screenshot post a second attempt at installing in Legacy:
(NB. most basic install used with 'something else', plus a random bit of space for windows...clutching at straws now!)
[ATTACH=CONFIG]281794[/ATTACH][/I]

---

### Post by oldfred on 2018-11-27
If installing in UEFI mode are you also telling it to use the ESP?
I have done both with and without telling it and it finds it, if correctly FAT32 with boot and/or esp flag.
Error seems to say it cannot find the ESP.

---

### Post by ubfan1 on 2018-11-27
Actually, the older EFI systems without secure boot wouldn't need the grub-efi-amd64-signed package, but the unsigned one, grub-efi-amd64.  I wouldn't think it should make a difference,  the signed shim/grub run just fine on my older machine. However, I never installed any grub-efi package, I converted a legacy install to UEFI by simply copying in the files from an efi partition on another secure boot machine (and edited the grub.cfg stub file's UUID to use the legacy root).Take a look at the files on the EFI partition -- mount the FAT filessystem somewhere and see what's in .../EFI/ubuntu --  grubx64.efi and grub.cfg at a minimum.  Type out the (three line)  grub.cfg file and see that the UUID on the search.fs line is the one for the root fs. If it differs, just edit the file to add the right one.

---

### Post by liverpj on 2018-11-28
Thanks for the replies. 

Just to reiterate - I am a very basic user. When running Lubuntu my use was purely Internet and office, so please don't assume too much prior knowledge!

A. >  If installing in UEFI mode are you also telling it to use the ESP? 
1. Idk whether it is installing in EFI or UEFI. I only know whether it is Legacy/Bios or not - which I assumed was EFI. 
2. Sorry, I'm not sure what you mean by "*telling it to use*" (I may need a more basic explanation). After installing in EFI(?) on reboot I have tried both; a) changing the bios to boot in EFI first and b) booting in Legacy first. Both have the same outcome. When I partition the first EFI file per my photos has the 'boot' and 'ESP' flags - is that sufficient to tell it, or do I need to take some other action? 
B. > Error seems to say it cannot find the ESP. 
Is there anything additional I should be doing to make the laptop find the ESP? 


C. >  converted a legacy install to UEFI 
1. When I try and install in Legacy and restart I still get, "no operating system found" - so the same result as installing in EFI. Do I need to download a specific live version of Ubuntu to install in legacy? 
D. >  Take a look at the files on the EFI partition [LEFT][COLOR=#222222][FONT=Verdana]...mount the FAT filessystem somewhere and see what's in .../EFI/ubuntu -- grubx64.efi and grub.cfg at a minimum. [/FONT][/COLOR][/LEFT]
 
1. I have opened what I think is the correct file filepath; cdrom>EFI>BOOT
there are two files; **BOOTx64.EFI** and **grubx64.efi**

E. >  Type out the (three line) grub.cfg file and see that the UUID on the search.fs line is the one for the root fs. If it differs, ** just edit the file to add the right one** . 
1. Sorry, but that goes straight over my head. 
2. What is / where would I find the text for the three line grub.cfg file? I've searched but couldn't find an answer that I understand. 
3. How would I edit the file and what would I edit it to? 

F. I thought it might be useful to post pictures of my bios options to see if there is something that anyone can spot:
[ATTACH=CONFIG]281795[/ATTACH][ATTACH=CONFIG]281796[/ATTACH]
[ATTACH=CONFIG]281797[/ATTACH][ATTACH=CONFIG]281798[/ATTACH]
[ATTACH=CONFIG]281799[/ATTACH]

---

### Post by liverpj on 2018-11-28
Not sure if this is of any help, but on the original HDD in _*boot>grub>x86_64-efi*_ there are a whole load of files, including; *_grub.efi_* and *_core.efi_*

The efi folder in *_boot>efi_* is empty. 

Does that give any clues as to what worked when I had lubuntu on the old HDD? 

I'm about to carryout the bum-flapping task reinstalling my old HDD and hoping the laptop works :s

---

### Post by yancek on 2018-11-28
The images you have posted show an EFI partition (sda1) which means you have installed in EFI mode.
Have you tried installing EFI with Legacy boot disabled?  If so, is the result the same?
The 64bit version downloaded from the Ubuntu site should work to install either UEFI or Legacy.

>  I have opened what I think is the correct file filepath; cdrom>EFI>BOOT]

That's on the installation usb not the hard drive.

The grub.cfg file mentioned in an earlier post would be on sda1.  To access it to see if you have any files there you can use the following commands to first mount then access.  Enter each command consecutively hitting the Enter key after each.

> sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1

Once you have done the above, you can use the following to see if you have EFI files:  ls  /mnt/sda1 (hit the Enter key and it should show an EFI directory)
You can also try accessing it from the nautilus file manager.  If the Grub EFI files are properly installed you would have an ubuntu directory under EFI.  In this directory is where you would find the grub.cfg file mentioned in an earlier post.  If there is nothing there that is why you can't boot EFI.

---

### Post by oldfred on 2018-11-28
Lets see all the details of your install.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the summary report ( not full report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by liverpj on 2018-11-29
Here is the paste bin:

[http://paste.ubuntu.com/p/dpGCFzFkfp/plain/](http://paste.ubuntu.com/p/dpGCFzFkfp/plain/)

[http://paste.ubuntu.com/p/dpGCFzFkfp/](http://paste.ubuntu.com/p/dpGCFzFkfp/) 

Boot repair asked if I had raid, I didn't know and couldnt work out how to check so I said yes and it removed some stuff and installed a mdadm package.

---

### Post by liverpj on 2018-11-29
@yancek 
> That's on the installation usb not the hard drive.

I've managed to mount the old HDD. 

There is a file called [LEFT][COLOR=#000000][FONT=Ubuntubeta]grub.cfg in boot/grub. 

NB. I have not yet tried putting the old HDD back in the laptop to see if still works. [/FONT][/COLOR][/LEFT]


> The images you have posted show an EFI partition (sda1) which means you have installed in EFI mode.
Have you tried installing EFI with Legacy boot disabled?  If so, is the result the same?

- per my previous post I have tried to install various OS. For each one now I have set the laptop to boot in EFI, which results in an EFI install, followed by booting the laptop first in EFI then in Legacy. I have also set the laptop to boot in Legacy, resulting in a non-EFI install, followed by testing the reboot first in Legacy and then afterwards in EFi.

---

### Post by liverpj on 2018-11-29
> Once you have done the above, you can use the following to see if you  have EFI files:  ls  /mnt/sda1 (hit the Enter key and it should show an  EFI directory)
You can also try accessing it from the nautilus file manager.  If the  Grub EFI files are properly installed you would have an ubuntu directory  under EFI.  In this directory is where you would find the grub.cfg file  mentioned in an earlier post.  If there is nothing there that is why  you can't boot EFI.

All that comes up is 'EFI' - see screenshot:
[ATTACH=CONFIG]281820[/ATTACH]

---

### Post by oldfred on 2018-11-29
You chose the advanced LVM (with encryption?) system. That uses volumes not partitions and requires more knowledge of Linux. Often used on servers, but required if you want full drive encryption? It also erases all partitions and only creates a boot partition and a partition for the rest of the drive for the LVM volumes.

Do you want full drive encryption?

---

### Post by ubfan1 on 2018-11-29
Yes, the EFI directory is the only expected entry, but what's in it?  Please post the cut and paste text output of the whole directory tree with
ls -R /mnt/sda1/EFI

---

### Post by liverpj on 2018-11-29
> [LEFT][COLOR=#000000][FONT=Ubuntubeta]Do you want full drive encryption?[/FONT][/COLOR][/LEFT]

Honestly I have zero preference. At this point I just want an OS on my SSD!

---

### Post by liverpj on 2018-11-29
> **ubfan1 said:**
> Yes, the EFI directory is the only expected entry, but what's in it?  Please post the cut and paste text output of the whole directory tree with
ls -R /mnt/sda1/EFI

```
ubuntu-mate@ubuntu-mate:~$ ls /mnt/sda1
EFI
ubuntu-mate@ubuntu-mate:~$ ls -R /mnt/sda1/EFI 
/mnt/sda1/EFI:
BOOT  ubuntu

/mnt/sda1/EFI/BOOT:
BOOTX64.EFI  fbx64.efi

/mnt/sda1/EFI/ubuntu:
BOOTX64.CSV  fw  fwupx64.efi  grub.cfg  grubx64.efi  mmx64.efi  shimx64.efi

/mnt/sda1/EFI/ubuntu/fw:


```

---

### Post by liverpj on 2018-11-29
I've just tried to reinstall mate and after crashing once already it has subsequently come up with a grub failed to install error.

Could that be a clue?

---

### Post by oldfred on 2018-11-29
Often once drive converted to LVM, standard partition tools may have issues.

Gparted should delete the entire partition that the LVM volume is in, and you can delete /boot partition. You can leave the ESP and if wanting to convert to BIOS add the bios_grub partition. Then easy to convert from UEFI or BIOS, just be reinstalling correct version of grub. Easiest with Boot-Repair for newer users.

---

### Post by liverpj on 2018-11-30
To cut down on the variables I am trying a new solution. Installing Windows 10 (and possibly seeing if the og Win7 licence works). This should help me assertain if there is an issue with the SSD. After that I will see if with the new SSD the laptop is useable with Windows. 

If I still have the motivation my next steps will be:

1. Download a fresh copy of Ubuntu MATE 16.04.5 LTS (Xenial) and create an new live disk with a decent USB stick
2. Go to bios and leave for 10mins per Crucial's configuration(?) instructions. 
3. Run live CD
4. in gpart delete all previous partitions.
5. create a FAT32 partition with esp and boot flags of 600MB
6. install using the most basic install with no updates checked
7. Choose something else.
8. Create 2 other partitions  / and home 
9. Install.
 
A. Is there anything else I should be doing? 
B.  Should I be installing grub before installing?

Cheers.

---

### Post by yancek on 2018-11-30
If you install windows 10 on a GPT disk, it will/should create an EFI partition an install its EFI boot files there.  When you install Ubuntu EFI, it will create an ubuntu directory in the EFI partition so you do not need to create another EFI partition.  That will lead to problems.  I would expect the windows install to take up the entire disk so no need to delete your old Ubuntu partitions as there won't be any.  Grub will be installed at the end of the Ubuntu installation.

---

### Post by ubfan1 on 2018-11-30
The contents of your EFI show that you have the grubx64.efi bootloader in its expected place. If the size of the .../EFI/Boot/BOOTX64.efi matches the grubx64.efi, then the fallback/remote boot setup is correct also.  Type out the .../EFI/ubuntu/grub.cfg (should be only 3 lines), and confirm that the UUID and partition match the ones for your root partition.  If they match, then your boot setup seems correct.  If you use the EFI boot menu (some function key at power-up like F12) to give you a choice of boot device or OS, does it have an ubuntu choice?  Does it have a device (sda) choice?  Try booting both.

---

### Post by liverpj on 2018-12-03
Sorry I've been away for a bit.

Win10 install failed.

I tried my old HDD and it works aok.

First thing that comes to mind is that my problem may be to do with the SDD. So the logical test would be to cloan my HDD with Lubuntu (says Ubuntu 17.10) to the new SSD and ascertain if that works. 

Does anyone have a link to a good guide?

Cheers.

ps here are some screen shots of the summary details. Not sure if there is something more useful I should be posting to help folks diagnose the issue(s)?

[ATTACH=CONFIG]281874[/ATTACH]
[ATTACH=CONFIG]281873[/ATTACH]
```
8-Environment Variables-
USER        : 
LANGUAGE        : 
XDG_SEAT        : seat0
XDG_SESSION_TYPE        : x11
SSH_AGENT_PID        : 3632
SHLVL        : 0
HOME        : /home/
DESKTOP_SESSION        : Lubuntu
XDG_SEAT_PATH        : /org/freedesktop/DisplayManager/Seat0
DBUS_SESSION_BUS_ADDRESS        : unix:path=/run/user/1000/bus
MANDATORY_PATH        : /usr/share/gconf/Lubuntu.mandatory.path
LOGNAME        : 
DEFAULTS_PATH        : /usr/share/gconf/Lubuntu.default.path
XDG_SESSION_ID        : c2
PATH        : /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
GDM_LANG        : 
XDG_RUNTIME_DIR        : /run/user/1000
XDG_SESSION_PATH        : /org/freedesktop/DisplayManager/Session0
DISPLAY        : :0.0
LANG        :
XDG_SESSION_DESKTOP        : Lubuntu
XAUTHORITY        : /home/me/.Xauthority
XDG_GREETER_DATA_DIR        : /var/lib/lightdm-data/me
SSH_AUTH_SOCK        : /tmp/ssh-2CY4DK16xU2o/agent.3567
SHELL        : /bin/bash
QT_ACCESSIBILITY        : 1
GDMSESSION        : Lubuntu
XDG_VTNR        : 7
PWD        : /home/me
XDG_DATA_DIRS        : /etc/xdg/lubuntu:/usr/share/gdm:/var/lib/menu-xdg:/usr/share/Lubuntu:/usr/local/share:/usr/share:/var/lib/snapd/desktop:/var/lib/snapd/desktop
XDG_CONFIG_DIRS        : /etc/xdg/lubuntu:/etc/xdg/xdg-Lubuntu:/etc/xdg
XDG_CURRENT_DESKTOP        : LXDE
_LXSESSION_PID        : 3567
XDG_CONFIG_HOME        : /home/me/.config
XDG_MENU_PREFIX        : lxde-
GTK_OVERLAY_SCROLLING        : 0
QT_STYLE_OVERRIDE        : gtk
QT_PLATFORM_PLUGIN        : lxqt
QT_QPA_PLATFORMTHEME        : lxqt
```

---

### Post by liverpj on 2018-12-03
[ATTACH=CONFIG]281876[/ATTACH]
[ATTACH=CONFIG]281877[/ATTACH]

---

### Post by liverpj on 2018-12-07
My original lubuntu OS (which worked on the HDD) was installed in legacy.

I have tried a fresh default install on the SSD and noticed that the partition flagged as boot, also contains an esp flag. I don't fully understand what I've read, but it seems like this might mean it is an EFI install. 

is that right? 

Cheers.

---

### Post by oldfred on 2018-12-07
UEFI uses gpt and has an ESP - efi system partition which is FAT32.
BIOS normally uses MBR with the primary, extended & logical partitions, but with Ubuntu it can (but should not be) installed in UEFI mode to MBR.
Windows requires gpt with UEFI and requires MBR with BIOS boot.

No operating system may be that boot mode of system does not match boot mode of install. How you boot install media UEFI or BIOS (both Windows & Ubuntu) is then how it installs. But system may have default boot in another mode.
There really are three boot modes. UEFI with Secure boot, UEFI, & BIOS/CSM/Legacy. 
And if Secure boot is on, other mode modes may not work at all. 
And most UEFI system have several settings in UEFI to get it to match install. 
You have UEFI Secure Boot, which may be "Windows" or "other". Fine print will say if installing Windows 7 use "other" as Windows 7 does not support Secure Boot, so that really is UEFI Secure boot setting for those systems.
Then you may have separate setting or settings for Legacy/UEFI.
And some systems need work arounds, or other settings in UEFI.

Have you updated UEFI from Samsung for your model system?
New UEFI may be required to correctly support SSD.

Have you run Boot-Repair's fixes and tried booting a hard drive entry?

---

### Post by liverpj on 2018-12-12
Thanks for the reply. I'm a bit snowed under at the moment, so I am picking this up when I can. But rest assured I am reading the responses. 

From the sounds of it Lecacy is the most reliable option for me, especially given that my current HDD running Lubuntu was installed and booting in Legacy. 

> Have you updated UEFI from Samsung for your model system?

I am working on it. But have never updated a BIOS before. I am using this guide [https://www.techadvisor.co.uk/how-to/pc-upgrades/how-update-bios-3428662/](https://www.techadvisor.co.uk/how-to/pc-upgrades/how-update-bios-3428662/) and this is the only update I seem to be able to find on the Samsung website: [https://www.samsung.com/uk/support/model/NP-X420-JA01UK/](https://www.samsung.com/uk/support/model/NP-X420-JA01UK/) 

This is what shows up as my BIOS specs:
> _**-BIOS-**_
  Date		: 09/21/2009
  Vendor		: Phoenix Technologies Ltd. ([www.phoenix.com](www.phoenix.com))
  Version		: 04IA.M005.20090921.KSY
  -Board-
  Name		: X420/X520
  Vendor		: SAMSUNG ELECTRONICS CO., LTD. ([www.samsung.com](www.samsung.com))
  -Product-
  Name		: X420/X520
  Family
  Version		: Not Applicable
  

> New UEFI may be required to correctly support SSD.

OK. 

> Have you run Boot-Repair's fixes and tried booting a hard drive entry?

Yes, I have run Boot-Repair and I think it's fixes. But I will give it another go. 

I don't know what booting a hard drive entry means, or how to do it, so I will do some reading. Just to confirm this would be done by installing the SSD again? 

Thanks.

---

### Post by oldfred on 2018-12-12
I did not think any system that old had UEFI, just the  older BIOS.
UEFI became the standard when Windows 8 was released in 2012 and Microsoft required vendors to only use UEFI on gpt drives. But UEFI has CSM, which was for backwards compatibility.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    
Windows 7 before that was usually BIOS with MBR partitioning.

I did not think the installer would even install in UEFI mode to an old BIOS system?

---

### Post by liverpj on 2018-12-13
I don't think it has UEFI as there is no reference to it in the BIOS. But it does reference EFI and Legacy in the BIOS settings.

---

### Post by liverpj on 2018-12-21
[http://paste.ubuntu.com/p/gkdqCC2kXN/](http://paste.ubuntu.com/p/gkdqCC2kXN/)

---

### Post by liverpj on 2018-12-21
[http://paste.ubuntu.com/p/YDYJMB4Vdt/](http://paste.ubuntu.com/p/YDYJMB4Vdt/)

---

### Post by liverpj on 2018-12-21
[LEFT][COLOR=#222222][FONT=Verdana]It seems to work![/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]OS is ubuntu MATE 16.04[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Installed by:[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]1. selecting Legacy install via my BIOS[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]2. default install - no something else/custom partitions etc. offline, with no updates or anything else - essentially the most vanilla install I could think of. [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]3. running boot repair from live USB after the above delivered the usual "no OS" errror msg.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]4. Going into BIOS and selecting EFI rather than Legacy, plus a couple of other random settings that I stupidly didn't record!!![/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]So in summary, I think it was boot repair that fixed it. This was the first time boot repair has offered me a serise of commands to type into terminal (which I did).[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Now the challenge is checking whether everything is aok, and if the partitioning works for me. [/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Either way this is a massive step forward and relief as it's the first solid 3hrs in a row I've had for weeks, or likely to have for the forseeable future. [/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Thanks for all the help. [/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]I will close this once I have checked it all works. [/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Cheers.[/FONT][/COLOR][/LEFT]

---

### Post by oldfred on 2018-12-21
Did you run Boot-Repair's fixes after posting report?
Report shows grub legacy .97. 
Ubuntu has not used that since about 2009, when it changed to use grub2 for standard BIOS boot.

Grub2 is BIOS/CSM/Legacy boot in new systems.

Grub2 uses grub.cfg for menu.
Grub legacy uses menu.lst.

I do not think Boot-Repair works with grub legacy, other than reinstalling grub2 to replace it.

---

### Post by liverpj on 2018-12-30
> Did you run Boot-Repair's fixes after posting report?

Yes. 

Idk about your other points I'm afraid. Could it be because the OS is ubuntu MATE 16.04? Rather than the new one? 

Everything works OK other than that battery life has got a lot worse.

---

