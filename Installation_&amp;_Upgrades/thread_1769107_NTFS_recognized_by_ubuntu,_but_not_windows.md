---
title: "NTFS recognized by ubuntu, but not windows"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by notzippy on 2011-05-27
I had a series of bad things happen during this (botched) Ubunto 11 install but the worse was my primary windows 7 installation partition got disrupted.. I used testdisk to restore the partition back to the point were I could mount it in Ubunto live and transfer a few files off of it - but now when I attempt to boot Windows 7, it fails immediately. If I use the install disk I can check that the partition is healthy but has "RAW" data (diskpart report). I have read a few different things saying various paid apps can "fix" the issue but from reading the docs (on those repair apps) is that all the do is transfer the files off of the "broken" partition so you can restore it elsewhere. 

Is there an actual fix for this ? I assume windows 7 is being more demanding about the state of the partition... 
(Oh and to rub salt in the wound when I use the windows installation disc if I choose "repair " I get a message that I cannot cause the installation disc does not match the "installed" version of windows)

thoughts ?

thx
Nz

---

### Post by oldfred on 2011-05-27
Welcome to the forums. 

Raw in windows means the partition does not have a NTFS boot sector set up yet. Normally when you format to NTFS it sets it up and when you install windows it adds info on booting XP with ntldr or Vista/7 with bootmgr. That info is missing. And that may be why it says it is the wrong version.

You just need to run fixboot from windows repair CD. Post #9 has links for a repair CD if you do not have one & #7 has instructions copied from several windows sites.

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

---

### Post by notzippy on 2011-05-27
Hi 

Thanks for the fast response, I had one issue following those directions - I am getting 

The version of System Recovery Options is not compatible with the version of Windows you are trying to repair.

When I try to repair the disk using the DVD I used to install the software. However I was able to bring up a command prompt (shift F10) and run the following commands

BootRec.exe /fixmbr
chkdsk C: /r /f 
BootRec.exe /FixBoot  
BootRec.exe /ScanOs

But when I ran this command
BootRec.exe /RebuildBcd

I got 
The requested system device cannot be found

Researched this it appears that this reads information from the \boot\bcd folder. Looking at my drive I have 2 of these folders (c:\boot, c:\Boot) but neither have the bcd file, but the do have a BCD.rcbak file - could this file be imported ?

Thoughts ?

thx
Nz

---

### Post by notzippy on 2011-05-27
Slight update to this, I do have a file located in c:\boot\BSD , but I am thinking this may be the real issue - I found this article on vista from Easybcd is it applicable to windows 7 ?

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by oldfred on 2011-05-27
You must also have installed grub to the windows partition. I should have asked for this first to see everything.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

If you had grub in the boot sector then windows may have seen it as RAW since it was missing the windows info.

You cannot have /boot & /Boot. Windows is not case sensitive so you have something impossible in windows, two folders with the same name. You want to delete the one with grub. The other should have the BCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

I think one user just copied bootmgr and the BCD to the correct places to allow booting and then repaired the BCD as it was for the repair not the install. But the repair disk should create a new one if it can see the correct folders.

---

### Post by notzippy on 2011-05-28
The RESULTS.txt, looks like your correct with your analysis about grub - i suspected this but had no proof...
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Testdisk is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdg.
 => Windows is installed in the MBR of /dev/sdh.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 262178.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdg1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 1143744 of /dev/sdg1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /ldlinux.sys

sdh1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sda2         262,178 3,068,168,333 3,067,906,156 Data partition (Windows/Linux)
/dev/sda3   3,068,170,240 3,907,028,991   838,858,752 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 640.1 GB, 640133946880 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250261615 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   799,698,943   799,696,896   7 NTFS / exFAT / HPFS


Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 8017 MB, 8017412096 bytes
16 heads, 32 sectors/track, 30584 cylinders, total 15659008 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1    *          8,064    15,659,007    15,650,944   b W95 FAT32


Drive: sdh _____________________________________________________________________

Disk /dev/sdh: 1000.2 GB, 1000204885504 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdh1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        01CB6A628FB3DDE0                       ntfs       Media
/dev/sda3        886C49086C48F28C                       ntfs       New Volume
/dev/sdb1        006642C16642B766                       ntfs       
/dev/sdg1        46A3-EC85                              vfat       PENDRIVE
/dev/sdh1        CE62431C62430923                       ntfs       SimpleDrive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/006642C16642B766  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdg1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdh1        /media/SimpleDrive       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdg1/boot/grub/grub.cfg: ===========================

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
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdg1/syslinux.cfg: ==============================

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
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry7 
menu label Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash -- 
 
label ubnentry8 
menu label Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash -- 
 
--------------------------------------------------------------------------------

=================== sdg1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdg1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdg1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

./boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

Renamed /boot - still having same problem with windows not being able to boot.

Nz

---

### Post by oldfred on 2011-05-28
Since you have a gpt disk and an MBR disk, you should be booting from the MBR disk. I know windows only will work with gpt if you use UEFI and only the win7 64 bit.

So replace testdisk in the MBR of sdb with a windows boot loader and then set BIOS to boot sdb.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing testdisk with Synaptic.
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by notzippy on 2011-05-30
Hi

Followed your advice and still had no luck getting windows to boot - as a last ditch effort i tried to recreate the bcd using bcdedit /create (and many more steps see link listed in previous post) This did work - and I got the windows splash startup (finally) but... the machine simply rebooted after a few seconds of loading and none of the safe modes worked for loading it either... Soooooo I backed up the partition (using partimage) and formatted it.

Tried to install windows - windows would not install to that drive. So I cleaned it , still would not install. Cursing the M$ overlords I disconnected my other drive. Finally windows accepted my plea and installed. 

I then installed ubunto with no issues.

Thanks for your help - another nail in the M$ coffin..
Nz

---

