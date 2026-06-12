---
title: "GRUB: no partition found"
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by Darii on 2010-07-11
I've been happily using my new Dell SXPS 1645 for the past 6 months and dual-booting Ubuntu and Windows 7 Professional, (both 64-bit) and have had very few issues until now.

Currently, when I boot up my computer and it gets past the BIOS loading I get:

error: no such partition.
grub rescue> _

No matter what commands I type into the Grub rescue prompt, (I've tried to do root and roonoverify) it comes up with "Unknown Command"

Booting up with an older Ubuntu 9.10 and running the partition utility reads that all of my disk space is unallocated, and it crashes the window if I ever try to read the filesystem.  Although, in fairness, I don't think that Ubuntu read my partitions ight even when my computer was in full working order.

When I boot from my imaging utility disk (Acronis True Image Home 2010), it reads out that my Ubuntu and swap partitions are unallocated, the Win7 loader is on C:/ and that Win7 and all my files/programs are on D:/ (they're supposed to be on C:/)

The strangest thing about this is that this isn't the first time it happened; it happened yesterday when I first booted up, but I figured that since I hadn't really done anything on my computer since I last imaged it besides play games for a week (and even then, the saves for those are in the Steam cloud) so I just restored my computer from an older image.  I booted back up immediately thereafter and had no problems; I just let my computer do all the updates it wanted to do (Firefox, iTunes, Steam games, virus definitions, security patches for Windows, etc.) rebooted it again, and started playing games/browsing the internet.  Windows downloaded one more update during this time; I thought nothing of it.  When I shut it down for the night and rebooted it this morning, I was at the exact same place I was the day before, with the same diagnosis (as far as I could tell).

I don't really care if I can recover any of those changes I made (as I can just reimage and download all the updates again), but I do need to find this source of this mysterious problem so it doesn't happen again, possibly when I have something important saved on my computer (ex during the school year).

So far all I can figure that could have caused the exact same problem to occur after restoring a (for all practical purposes) week-old image would be because of one/some of those Window updates messing something up in the bootloader, or some weird hardware error.  (Admittedly, I've been leery of my 128GB Sasmsung(?) SSD even before I started having problems because I've almost run out of space on it, and have been looking for an excuse to upgrade).

This is my first time running a dual-boot system; any and all help would be appreciated.

---

### Post by scottuss on 2010-07-11
It's entirely possible that the hard disk is starting to fail, I'd recommend running a disk testing utility in the process of elimination.

---

### Post by oldfred on 2010-07-11
Some HP & Dell software hides settings in the MBR.

Writes to MBR-----------------------------------
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

### Post by Darii on 2010-07-11
olfred- I did a clean install of Win7 when I got my computer, so I should no longer have the Dell DataSafe or any of the other problematic programs listed on my computer.

Regardless, I don't think the problem is entirely with the MBR, if at all.

I tried to restore the MBR from the working image (not the entire image, just the MBR) but that did nothing.  

I burned a copy of the Super GRUB CD mentioned in one of those links, and have been poking around in it for a while now.  I managed to get it to boot into Windows fine, but it can't seem to create or repair GRUB, nor can it find the partition for it when I tell it to give me information about my partitions.  I get an error reading "Error 6:Mismatched or corrupt version of stage1/stage2" in the show me my partitions mode, when I tell it to try to repair GRUB Error 15: File not found Booting 'not lucky', and when booted into Windows I get an extra partition E:/ which wasn't there before. 

 When I boot into E:/ with SGC I get some weird diagnostics testing I've never seen before, and Partition Wizard under Windows and SGC seem to point to this as the stange ~39MB Windows FAT partition that was sitting at the front of my drive.  If I were to repartition could I delete that partition and get another primary partition back, or odes it do something I can't see?

As it stands, I am leaning towards using this as an opportunity to repartition and just reinstall Ubuntu later, but I would like to have at least a faint idea was to what caused this.  Does Windows in general (and not just Windows Vista and/or select utilities) have a reputation for eating the MBR and/or partitions?

---

### Post by presence1960 on 2010-07-11
Currently we have no hard info about the actual condition of your partitions, MBR, etc. So everything is speculation at best.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by Darii on 2010-07-11
So, here's the output:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x72078d5f

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262   6 FAT16
/dev/sda2    *         81,920       286,719       204,800   7 HPFS/NTFS
/dev/sda3             289,170   192,458,699   192,169,530   7 HPFS/NTFS
/dev/sda4         192,442,635   250,067,789    57,625,155   f W95 Ext d (LBA)
Invalid MBR Signature found
/dev/sda5     ?   244,277,235   289,361,416    45,084,182  66 Unknown
/dev/sda6     ?   243,228,557   306,138,935    62,910,379  b4 SpeedStor

/dev/sda3 overlaps with /dev/sda4
/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda4
/dev/sda5 overlaps with /dev/sda6
/dev/sda6 ends after the last sector of /dev/sda
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda4

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        9C983A48983A2166                       ntfs       System Reserved               
/dev/sda3        01CA88CF53504DE0                       ntfs       Windows                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  93 08 c0 fb 09 09 8f fb  84 09 f5 fb ca 09 3c fc  |..............<.|
00000010  99 09 e4 fb 4f 09 dd fb  e8 08 1b fc 64 08 a7 fc  |....O.......d...|
00000020  e3 07 9d fd 91 06 e1 fd  b4 04 d9 fd d5 02 ea fd  |................|
00000030  31 01 24 fe dc ff 80 fe  e7 fe 60 ff 17 fe bd 00  |1.$.......`.....|
00000040  fb fc a6 01 d4 fb 6f 02  c7 fa 3a 03 aa f9 b9 03  |......o...:.....|
00000050  92 f8 50 04 9b f7 cc 04  5a f6 43 04 35 f5 6b 03  |..P.....Z.C.5.k.|
00000060  62 f4 51 02 ad f3 cd 00  19 f3 b3 ff 94 f2 20 ff  |b.Q........... .|
00000070  07 f2 ca fd af f1 26 fc  b2 f1 3f fb e8 f1 a6 fa  |......&...?.....|
00000080  84 f2 16 fa a4 f3 ab f9  21 f5 64 f9 a8 f6 45 f9  |........!.d...E.|
00000090  76 f8 af f9 2d fa ad fa  74 fb 7b fb 9c fc cf fb  |v...-...t.{.....|
000000a0  bb fd 94 fb 8d fe a8 fa  96 ff 04 fa f2 00 2b fa  |..............+.|
000000b0  1f 02 98 fa 2d 03 19 fb  42 04 ee fb 19 05 9f fc  |....-...B.......|
000000c0  aa 05 30 fd 2d 06 da fd  38 06 d9 fd e6 05 07 fd  |..0.-...8.......|
000000d0  61 05 bc fb c0 04 a2 fa  f3 03 f7 f9 2c 03 eb f9  |a...........,...|
000000e0  2f 02 a8 f9 11 01 c3 f8  e1 ff 02 f8 76 fe b0 f7  |/...........v...|
000000f0  7a fd ee f7 45 fd 0b f8  5e fd ed f7 76 fd a0 f7  |z...E...^...v...|
00000100  f5 fd c8 f7 e5 fe c5 f8  c6 ff 26 fa 41 00 29 fb  |..........&.A.).|
00000110  8f 00 b2 fb b8 00 7e fb  17 01 0c fb 0a 02 a9 fb  |......~.........|
00000120  13 03 f1 fc 1d 04 4b fe  44 05 86 ff 3b 06 1c 00  |......K.D...;...|
00000130  f4 06 10 00 f9 07 3f 00  f3 08 b2 00 9e 09 8c 00  |......?.........|
00000140  09 0a dc ff 8b 0a 71 ff  f9 0a 02 ff 89 0b 19 ff  |......q.........|
00000150  28 0c 28 ff 98 0c ee fd  10 0d 13 fc 63 0d dc fa  |(.(.........c...|
00000160  a0 0d 48 fa f9 0d 89 f9  8c 0e 15 f8 00 0f 77 f6  |..H...........w.|
00000170  0a 0f 43 f5 ff 0e c5 f4  05 0f f8 f4 83 0e 5d f5  |..C...........].|
00000180  77 0d 7b f5 42 0c 2b f5  a8 0a 57 f4 2a 09 b3 f3  |w.{.B.+...W.*...|
00000190  f6 07 b3 f3 fc 06 b1 f3  32 06 ba f3 48 05 6d f3  |........2...H.m.|
000001a0  66 04 77 f2 04 04 77 f1  43 04 49 f1 6c 04 f8 f0  |f.w...w.C.I.l...|
000001b0  30 04 ef ef d3 03 c4 ee  59 03 fb ed 07 03 b8 ed  |0.......Y.......|
000001c0  25 03 66 ee 5a 03 e8 ee  16 03 16 ee af 02 60 ed  |%.f.Z.........`.|
000001d0  97 02 b4 ed 82 02 82 ee  06 03 ab ef bf 03 97 f0  |................|
000001e0  21 04 17 f1 01 04 8d f1  05 04 f1 f2 6d 04 3e f5  |!...........m.>.|
000001f0  12 05 af f7 17 05 8c f9  54 04 f3 fa 36 03 44 fc  |........T...6.D.|
00000200

Unknown BootLoader  on sda5


Unknown BootLoader  on sda6



=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo0/sda3: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory

```

---

### Post by presence1960 on 2010-07-11
You still have the dell utility partition @ sda1. You have an extended partition sda4 which contains sda5 & sda6 which are unmountable. These are most likely your ubuntu / partition and swap partition.

Your partition table is somewhat fouled up with partitions overlapping each other. I would format the entire hard disk (using gparted Live)and set up at least three partitions. At least one NTFS as a primary partition for windows and the rest an extended partition for ubuntu, swap and maybe a data storage partition. Set them up as logical inside the extended partition. The ubuntu partition I would set up as ext 4 and swap as linux-swap.

If you set up the partitions before hand it will save you the trouble of shrinking windows to install ubuntu.

Install windows from the windows DVD first onto sda1. When install is complete reboot and make sure windows runs properly. When you are ready then install ubuntu onto the logical partition inside the extended partition.

P.S. I didn't suggest running fsck on the sda5 & sda6 partitions because your partition table is out of wack anyway. Your best bet in my opinion is to start anew and get rid of that dell utility partition while fixing the overlapping partitions by starting over.

---

### Post by presence1960 on 2010-07-11
```
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x72078d5f

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262   6 FAT16
/dev/sda2    *         81,920       286,719       204,800   7 HPFS/NTFS
/dev/sda3             289,170   192,458,699   192,169,530   7 HPFS/NTFS
/dev/sda4         192,442,635   250,067,789    57,625,155   f W95 Ext d (LBA)
[COLOR="Red"]Invalid MBR Signature found
/dev/sda5     ?   244,277,235   289,361,416    45,084,182  66 Unknown
/dev/sda6     ?   243,228,557   306,138,935    62,910,379  b4 SpeedStor

/dev/sda3 overlaps with /dev/sda4
/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda4
/dev/sda5 overlaps with /dev/sda6
/dev/sda6 ends after the last sector of /dev/sda
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda4[/COLOR]

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        9C983A48983A2166                       ntfs       System Reserved               
/dev/sda3        01CA88CF53504DE0                       ntfs       Windows  
```                     

See how your partition table is fouled up? I would format the entire disk and start over.

---

### Post by Darii on 2010-07-12
Bleargh.  So that's what that lil FAT16 partition has been all along?  I had no idea what it was, and I could've sworn I formatted it when I first installed Win 7....  I guess it didn't work.

I've been looking for an excuse to reformat, and I guess I'm being forced to take this opportunity.

Thanks for all your help with this so far and giving me advice on how to go about repartitioning my drive-- I'll mark this topic as solved.

---

