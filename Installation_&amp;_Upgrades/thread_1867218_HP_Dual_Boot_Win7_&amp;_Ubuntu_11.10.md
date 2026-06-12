---
title: "HP Dual Boot Win7 &amp; Ubuntu 11.10"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by confusedmatt on 2011-10-22
Hi,

I've just bought a G62-450SA, and bricked it trying to dual boot it.

The process I have followed is:

[LIST=1]
[*]Shrunk the main partition
[*]used gpart to create a ext4 partition
[*]removed the HP Tools partition (a mistake I now know)
[*]Created a Swap Partition
[*]Installed 11.10 from the LiveCD
[/LIST]

And now seem to have bricked the laptop.

Having checked the forums I realise that I have made a number of mistakes in this process and am just wondering if anyone can advise how to recover from this massive mistake?

Matt

---

### Post by Hakunka-Matata on 2011-10-22
Hi, Welcome;

Would  you mind expanding a bit on "[B]bricked the laptop"?


[/B]

---

### Post by confusedmatt on 2011-10-23
Hi thanks for your interest,

When I turn it on, after the HP flash screen, there is just a black screen with a cursor which doesn't respond to the keyboard.

I can still get in to the Bios and make changes, but the recovery option just goes to the blank, unresponsive, screen.

Matt

---

### Post by Mark Phelps on 2011-10-24
It's unlikely that the Win7 compressed image that HP put onto the drive for Restore was stored in the HP Tools partition.  It's more likely that it's in a Recovery partition.

Since you resized partitions, that may be confusing the HP restore operation and causing it to fail.

If you can boot using an Ubuntu desktop CD, I would do that.  Open a terminal and run "sudo fdisk -lu" (Lowercase L, not a one). That will list out the partitions on the drive. You'll at least be able to see if the Recovery partition is still there.

You should also open the Win7 OS partition with Nautilus and confirm that the folders and files are still there.

If you have a Restore Cd that came with the PC, you can try booting from it and seeing if it gives you any kind of Repair option.  It probably won't.

If Win7 looks intact from the filesystem perspective, if you have another PC available and are willing to spend some money, you can go to the link below, purchase the appropriate Win7 image, download that and burn it to CD:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Then, boot from that CD and run Startup Repair three times.  With any luck, that will restore access to Win7.

---

### Post by Hakunka-Matata on 2011-10-24
> **confusedmatt said:**
> Hi thanks for your interest,

When I turn it on, after the HP flash screen, there is just a black screen with a cursor which doesn't respond to the keyboard.

I can still get in to the Bios and make changes, but the recovery option just goes to the blank, unresponsive, screen.

Matt

OK, HP flash screen, what is that, the BIOS booting you mean?, 
So you never see a grub menu, or windows startup screen, I don't really know what you're trying to do now.
Are you trying to boot into Windows (xp, 7, vista?)?
Are you trying to boot into Ubuntu?, a wubi install?, or a partition install?

thanks
posting the output of some code might help to understand where you are,  what do you think you need to do?
```
sudo fdisk -l
```

---

### Post by confusedmatt on 2011-10-25
Hi,

Yes, by HP screen I mean the bios options. No, it never gets to the grub menu.

What I'm trying to do is set-up a side by side dual boot with Windows 7 and Ubuntu 11.10.

Following advise given to other people I have run the boot info script, output below:

```

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda2 starts 
                       at sector 409600. But according to the info from 
                       fdisk, sda2 starts at sector 2048. The info in boot 
                       sector on the starting sector of the MFT is wrong. 
                       According to the info in the boot sector, sda2 has 
                       472029183 sectors, but according to the info from 
                       fdisk, it has 407551 sectors.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda3 starts 
                       at sector 940064768. But according to the info from 
                       fdisk, sda3 starts at sector 409600. According to the 
                       info in the boot sector, sda3 has 36495359 sectors, 
                       but according to the info from fdisk, it has 472029183 
                       sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sda4 starts 
                       at sector 976560128. But according to the info from 
                       fdisk, sda4 starts at sector 472438784. According to 
                       the info in the boot sector, sda4 has 210992 sectors.. 
                       But according to the info from the partition table, it 
                       has 504334335 sectors.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  82 Linux swap / Solaris
/dev/sda3             409,600   472,438,783   472,029,184  42 SFS
/dev/sda4         472,438,784   976,773,119   504,334,336  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6871795e-f8e3-47ae-954e-0d0cf978188c   swap       
/dev/sda2        5A6AB7C76AB79DE7                       ntfs       
/dev/sda3        C02827F92827ECDA                       ntfs       RECOVERY
/dev/sda4        3C55-6AEC                              vfat       HP_TOOLS

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

MFT Sector of sda2

00000000  46 49 4c 45 30 00 03 00  08 c4 20 27 00 00 00 00  |FILE0..... '....|
00000010  01 00 01 00 38 00 01 00  b0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  6d 00 1c 91 00 00 00 00  10 00 00 00 60 00 00 00  |m...........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  78 61 a1 b6 1a 72 cb 01  78 61 a1 b6 1a 72 cb 01  |xa...r..xa...r..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  78 61 a1 b6 1a 72 cb 01  |........xa...r..|
000000c0  78 61 a1 b6 1a 72 cb 01  78 61 a1 b6 1a 72 cb 01  |xa...r..xa...r..|
000000d0  78 61 a1 b6 1a 72 cb 01  00 40 00 00 00 00 00 00  |xa...r...@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  3f 86 00 00 00 00 00 00  |........?.......|
00000120  40 00 00 00 00 00 00 00  00 00 64 08 00 00 00 00  |@.........d.....|
00000130  00 00 64 08 00 00 00 00  00 00 64 08 00 00 00 00  |..d.......d.....|
00000140  33 40 86 00 00 00 0c 00  b0 00 00 00 60 00 00 00  |3@..........`...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  05 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 60 00 00 00 00 00 00  08 50 00 00 00 00 00 00  |.`.......P......|
00000180  08 50 00 00 00 00 00 00  31 01 ff ff 0b 11 01 ff  |.P......1.......|
00000190  31 01 03 7c 2c 31 01 1f  56 13 31 01 4c ea 1d 31  |1..|,1..V.1.L..1|
000001a0  01 27 f0 0b 00 5c c9 81  ff ff ff ff 00 00 00 00  |.'...\..........|
000001b0  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 05 00  |....P.....@.....|
000001c0  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  31 01 ff ff 0b 11 01 ff  00 00 01 00 00 e0 6d 00  |1.............m.|
00000200
Unknown BootLoader on sda4

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 ce 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 20 35 3a  |........?.... 5:|
00000020  30 38 03 00 19 03 00 00  00 00 00 00 02 00 00 00  |08..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 ec 6a 55 3c 4e  4f 20 4e 41 4d 45 20 20  |..).jU<NO NAME  |
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
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

```

```

And as per your request the output from sudo fdisk -l:

```

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x568b201c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
/dev/sda2   *        2048      409599      203776   82  Linux swap / Solaris
/dev/sda3          409600   472438783   236014592   42  SFS
/dev/sda4       472438784   976773119   252167168   83  Linux
```

```


If you are able to advise I would be very relieved not to have created an expensive paper weight!

Matt

---

### Post by pritam_par on 2011-10-25
you must have lost ur widows boot loader. Install it through Windows DVD even installing Ubuntu grub will also work

___________________________________________________________________________
[Ubuntu 11.10 dual boot ]("http://opensource-sidh.blogspot.com/2011/10/install-ubuntu-1110-and-windows-dual.html"): [Proxy authorization in Ubuntu]("http://opensource-sidh.blogspot.com/2011/10/settings-for-proxy-authorization-in.html"):

---

### Post by confusedmatt on 2011-10-25
Hi pritam_par,

Can you advise how to install the Ubuntu grub?

Matt

---

### Post by Hakunka-Matata on 2011-10-25
Matt, have a short read on [this]("http://ubuntuforums.org/showthread.php?t=1857886&highlight=SFS+file+system") thread maybe, it is a situation identical to yours.  Windows has created (converted) your drive partitions to "dynamic" type, and now you cannot install ubuntu until the drive is converted back to a type "basic".

Read about it in that link above.

---

### Post by oldfred on 2011-10-26
Not only do you have to dynamic partitions but you converted sda2 to swap. sda2 was your hidden boot/recovery partition for Windows as it has boot flag (active partition in Windows). If you can convert the dynamic partitions back, you may be able to repair your main install with a Windows repairCD (in effect obsoletes the 100MB boot partition). But boot flag then has to be on main partition sda3. You can use gparted or a windows repair CD to move boot flag or active partition.

You can try converting back with miniTool which may or may not work. Did you make the recovery DVDs before installing? Did you make a Windows repair CD  so you have a way to fix Windows?

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Several users have used this, it has a liveCD download to use:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by Mark Phelps on 2011-10-26
> **pritam_par said:**
> Install it through Windows DVD even installing Ubuntu grub will also work

Installing, or in this case, reinstalling, GRUB will have NOTHING to do with repairing any kind of Windows boot problem.

There is a boot CD that might be able to repair the Windows problem, but as oldfred pointed out, the Dynamic Disk problem has to be fixed first.

---

### Post by confusedmatt on 2011-10-27
Hi all,

Thanks again for all of your advise, time and consideration.

As I clearly made such a mess of this thing I have run the recovery disks and started the whole thing again, this time using the wubi, like I guess I should have done in the first place!

And it seems to be working fine now.

Matt (now not quite so confused)

---

