---
title: "Upgraded Ubuntu, Now Cannot Boot?!  No Such Device: Grub Rescue"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by fastveg on 2010-12-23
Hey all,

I am running Windows Vista and just installed Ubuntu because friends told me it was a good system.

It prompted me to do updates, then prompted me to restart, now my laptop won't boot at all!  And just gives a "grub rescue" error message.

Help?!

---

### Post by fastveg on 2010-12-23
When I installed Ubuntu I did the version that installs 10.4 alongside Windows without using a disc, if that matters any.

---

### Post by fastveg on 2010-12-23
I made a installation disc and tried running that because that's what the other Grub threads seemed to suggest?

This allowed me load Ubuntu using the trial option but doesn't really fix the main booting issue?

What do I do from here?!

---

### Post by fastveg on 2010-12-23
I ran that script thing from another Grub thread.  Here are the results:

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   377,029,484   377,029,422   7 HPFS/NTFS
/dev/sda2         377,029,485   602,308,979   225,279,495   f W95 Ext d (LBA)
/dev/sda5         377,029,548   602,308,979   225,279,432   7 HPFS/NTFS
/dev/sda3         602,312,704   625,135,615    22,822,912   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1030 MB, 1030225920 bytes
4 heads, 3 sectors/track, 167680 cylinders, total 2012160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 243     2,012,159     2,011,917   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       caa473af-2e2c-4e6c-874f-6978dfdee95d   ext4                                     
/dev/sda1        01CBA2ED314315A0                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        E47E96157E95E09A                       ntfs       RECOVERY                      
/dev/sda5        01CBA2ED33BEC400                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3D31-B830                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  a4 f4 68 30 03 a7 c0 f0  88 5a 79 cc 49 86 43 30  |..h0.....Zy.I.C0|
00000010  1b 33 33 63 ac 68 bb e3  c4 03 93 0e a4 0c 50 2e  |.33c.h........P.|
00000020  c1 c4 0b b8 32 71 22 6c  ec 6a b2 d3 83 97 31 8e  |....2q"l.j....1.|
00000030  55 19 54 45 af bd 57 f8  06 fa 28 03 80 4e 50 08  |U.TE..W...(..NP.|
00000040  15 96 85 09 44 41 90 c0  81 85 08 22 42 62 ab c2  |....DA....."Bb..|
00000050  84 41 62 fb 00 00 00 dd  09 00 0d 98 00 d3 cc 00  |.Ab.............|
00000060  00 00 00 24 08 f6 59 a3  88 23 9d a0 52 e2 f7 79  |...$..Y..#..R..y|
00000070  73 66 39 d5 cf 17 81 e6  92 f4 4b cf da 32 9b 65  |sf9.......K..2.e|
00000080  77 d3 07 8a 3d 82 73 f4  4d a7 c8 4d 83 c3 c7 5c  |w...=.s.M..M...\|
00000090  53 20 39 57 13 9b 07 e7  ff 7b c2 a1 ba eb 1b 60  |S 9W.....{.....`|
000000a0  c5 1d 5e 8c 30 5f 52 4f  f0 93 e9 06 de de a4 51  |..^.0_RO.......Q|
000000b0  46 69 d2 9c 63 00 0b 82  b4 95 03 21 9f 4d db 39  |Fi..c......!.M.9|
000000c0  41 a7 dc 34 71 95 63 3a  22 7c c3 f8 54 a2 70 b4  |A..4q.c:"|..T.p.|
000000d0  e2 e7 b4 1d 5d a8 4c 19  65 f0 6b f0 c1 e7 8c 4e  |....].L.e.k....N|
000000e0  f7 3a 37 68 2a 9c e7 ca  43 6e ae 51 8c 2a 16 26  |.:7h*...Cn.Q.*.&|
000000f0  da 63 e5 d0 98 ef bb 5a  0e 4e 77 53 0a c3 e3 c4  |.c.....Z.NwS....|
00000100  14 51 1d ca e5 8c 29 6d  3c ba f4 b4 c2 38 4e ec  |.Q....)m<....8N.|
00000110  8e 9a 37 a1 26 72 7e be  ee f7 dd 12 79 cd 00 c5  |..7.&r~.....y...|
00000120  b2 58 61 41 e5 29 34 3b  5b 64 a3 39 bb 3b 33 07  |.XaA.)4;[d.9.;3.|
00000130  b0 fc fa f1 82 38 c9 a1  22 5a 4b 1e 72 41 6c 7a  |.....8.."ZK.rAlz|
00000140  0f 5e 9f 6a ba 01 86 ab  1c 79 a6 a5 0b 07 a7 84  |.^.j.....y......|
00000150  e7 20 1a 57 df 8f 0e 7c  89 df cd 80 c6 cd 01 0d  |. .W...|........|
00000160  73 62 40 6d 2b 0d 82 75  a8 82 ee 96 2e 50 43 ad  |sb@m+..u.....PC.|
00000170  f8 14 0c 19 61 14 e1 c1  37 19 f3 99 ef 58 20 f5  |....a...7....X .|
00000180  59 d0 ed ba f7 53 33 a2  b0 97 66 94 3f 54 5d e0  |Y....S3...f.?T].|
00000190  71 e0 a7 a1 c2 60 37 32  53 86 4b 0a 71 d4 5a 5e  |q....`72S.K.q.Z^|
000001a0  95 c2 ed 6f e3 58 b3 fd  bf c3 b2 43 4c 1b ee de  |...o.X.....CL...|
000001b0  ef c2 99 4f ee 01 4a a2  1d c9 c3 c2 01 90 00 fe  |...O..J.........|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 c8 7d 6d 0d 00 00  |......?....}m...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by kansasnoob on 2010-12-23
> **fastveg said:**
> I ran that script thing from another Grub thread.  Here are the results:

Since you're running the Ubuntu Live CD just copy-n-paste the following commands:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

Hopefully that will get Windows booting again, then also have a look at this:

[http://ubuntuforums.org/showpost.php?p=10207564&postcount=1](http://ubuntuforums.org/showpost.php?p=10207564&postcount=1)

I have a bit of a worry about drive /dev/sdb which is shown as "Disk /dev/sdb: 1030 MB". I see it has a grub mbr:

> => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in
partition #256 for /boot/grub.

If it's only storage that probably won't matter though.

---

### Post by fastveg on 2010-12-23
Ok, did that.

> ubuntu@ubuntu:~$ sudo lilo -M /dev/sda mbr
Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of  /dev/sda  has been updated.

Restarting without the disk to see what happens...

---

### Post by fastveg on 2010-12-23
Unfortunately, that did not seem to have any impact.  I still booted into the same "No such device" Grub error.

---

### Post by fastveg on 2010-12-23
I reran the script, here are the new results:

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   377,029,484   377,029,422   7 HPFS/NTFS
/dev/sda2         377,029,485   602,308,979   225,279,495   f W95 Ext d (LBA)
/dev/sda5         377,029,548   602,308,979   225,279,432   7 HPFS/NTFS
/dev/sda3         602,312,704   625,135,615    22,822,912   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1030 MB, 1030225920 bytes
4 heads, 3 sectors/track, 167680 cylinders, total 2012160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 243     2,012,159     2,011,917   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       caa473af-2e2c-4e6c-874f-6978dfdee95d   ext4                                     
/dev/sda1        01CBA2ED314315A0                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        E47E96157E95E09A                       ntfs       RECOVERY                      
/dev/sda5        01CBA2ED33BEC400                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3D31-B830                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  a4 f4 68 30 03 a7 c0 f0  88 5a 79 cc 49 86 43 30  |..h0.....Zy.I.C0|
00000010  1b 33 33 63 ac 68 bb e3  c4 03 93 0e a4 0c 50 2e  |.33c.h........P.|
00000020  c1 c4 0b b8 32 71 22 6c  ec 6a b2 d3 83 97 31 8e  |....2q"l.j....1.|
00000030  55 19 54 45 af bd 57 f8  06 fa 28 03 80 4e 50 08  |U.TE..W...(..NP.|
00000040  15 96 85 09 44 41 90 c0  81 85 08 22 42 62 ab c2  |....DA....."Bb..|
00000050  84 41 62 fb 00 00 00 dd  09 00 0d 98 00 d3 cc 00  |.Ab.............|
00000060  00 00 00 24 08 f6 59 a3  88 23 9d a0 52 e2 f7 79  |...$..Y..#..R..y|
00000070  73 66 39 d5 cf 17 81 e6  92 f4 4b cf da 32 9b 65  |sf9.......K..2.e|
00000080  77 d3 07 8a 3d 82 73 f4  4d a7 c8 4d 83 c3 c7 5c  |w...=.s.M..M...\|
00000090  53 20 39 57 13 9b 07 e7  ff 7b c2 a1 ba eb 1b 60  |S 9W.....{.....`|
000000a0  c5 1d 5e 8c 30 5f 52 4f  f0 93 e9 06 de de a4 51  |..^.0_RO.......Q|
000000b0  46 69 d2 9c 63 00 0b 82  b4 95 03 21 9f 4d db 39  |Fi..c......!.M.9|
000000c0  41 a7 dc 34 71 95 63 3a  22 7c c3 f8 54 a2 70 b4  |A..4q.c:"|..T.p.|
000000d0  e2 e7 b4 1d 5d a8 4c 19  65 f0 6b f0 c1 e7 8c 4e  |....].L.e.k....N|
000000e0  f7 3a 37 68 2a 9c e7 ca  43 6e ae 51 8c 2a 16 26  |.:7h*...Cn.Q.*.&|
000000f0  da 63 e5 d0 98 ef bb 5a  0e 4e 77 53 0a c3 e3 c4  |.c.....Z.NwS....|
00000100  14 51 1d ca e5 8c 29 6d  3c ba f4 b4 c2 38 4e ec  |.Q....)m<....8N.|
00000110  8e 9a 37 a1 26 72 7e be  ee f7 dd 12 79 cd 00 c5  |..7.&r~.....y...|
00000120  b2 58 61 41 e5 29 34 3b  5b 64 a3 39 bb 3b 33 07  |.XaA.)4;[d.9.;3.|
00000130  b0 fc fa f1 82 38 c9 a1  22 5a 4b 1e 72 41 6c 7a  |.....8.."ZK.rAlz|
00000140  0f 5e 9f 6a ba 01 86 ab  1c 79 a6 a5 0b 07 a7 84  |.^.j.....y......|
00000150  e7 20 1a 57 df 8f 0e 7c  89 df cd 80 c6 cd 01 0d  |. .W...|........|
00000160  73 62 40 6d 2b 0d 82 75  a8 82 ee 96 2e 50 43 ad  |sb@m+..u.....PC.|
00000170  f8 14 0c 19 61 14 e1 c1  37 19 f3 99 ef 58 20 f5  |....a...7....X .|
00000180  59 d0 ed ba f7 53 33 a2  b0 97 66 94 3f 54 5d e0  |Y....S3...f.?T].|
00000190  71 e0 a7 a1 c2 60 37 32  53 86 4b 0a 71 d4 5a 5e  |q....`72S.K.q.Z^|
000001a0  95 c2 ed 6f e3 58 b3 fd  bf c3 b2 43 4c 1b ee de  |...o.X.....CL...|
000001b0  ef c2 99 4f ee 01 4a a2  1d c9 c3 c2 01 90 00 fe  |...O..J.........|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 c8 7d 6d 0d 00 00  |......?....}m...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by fastveg on 2010-12-23
I believe the error might be on SDA2?  In the drive/partition info, it appears to be a duplicate of a valid partition, SDA5.

SDA3 looks like my main partition, the original C: drive, where Vista is installed.  Then I have another smaller partition U: where I tried to install Ubuntu.

--

Edit:  I don't know why it says XP on there, this laptop came with Vista pre-installed.

---

### Post by kansasnoob on 2010-12-23
What is that /dev/sdb? It shows up as 1030 MB. Is that a flash drive? A memory card?

If so remove it and then try to boot.

---

### Post by fastveg on 2010-12-23
Yeah, it's a memory card.  Has always stayed in without any issues, but removing it and rebooting now.

---

### Post by fastveg on 2010-12-23
Hey man, that seemed to fix it.  It gave me the old option to boot between either ubuntu or windows -- I chose ubuntu and it came right up.

Only difference was after I chose ubuntu, it had four options?  Like two ubuntu options and then two more that said (recovery). I think before there were only two options, not four.

I'm going to test out windows now, back in a minute.

---

### Post by fastveg on 2010-12-23
Yep, everything seems to work now.  Thanks for the help Kansas.

Is there anything else I need to do?  Do you think I should even keep this WUBI install or should I just wipe my U: drive and install fresh from the disk?

I only did WUBI because I thought it would be quicker / easier but now I am not so sure..

---

### Post by fastveg on 2010-12-23
And now I'm seeing that it's not possible to get flash player for chrome for the 64-bit 10.04 ubuntu.  Is that a WUBI thing as well?

[http://www.google.com/support/forum/p/Chrome/thread?tid=5cbb37c115bd9a75&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=5cbb37c115bd9a75&hl=en)

---

### Post by theasprint on 2010-12-23
Hi,

For now it may seem Wubi is quite troublesome.
Recommend that for future installations, Try Ubuntu first, then if everything is compatible, install it side-by-side with Windows and not Wubi.

This may actually be more stable. Because Ubuntu is in its "free" form. Unlike Wubi

---

### Post by fastveg on 2010-12-23
Thanks for the advice theasprint.

Would you forsee any issues with me wiping away this WUBI installation (deleting everything on the U: partition) and reinstalling ubuntu from disc?

Considering the boot issues I was having would that break anything?

---

### Post by theasprint on 2010-12-24
Hi,

You want to wipe the Wubi installation?
I think for a nice, clean wipe, just uninstall Ubuntu from Windows.

If you want to stick with Wubi, then apply the Permanent Fix in the Wubi Megathread here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Here's a thing: Anything that would go wrong later, we'll solve it. But if nothing goes wrong, the nothing will go wrong. An Ubuntu that breaks, breaks.

However, I would really recommend you to remove Wubi (uninstall properly) and Install Ubuntu at another partition. (if you still want to use Ubuntu) There should be less risks and problems when Ubuntu is "free" unlike its Wubi form.

Here is a link on how to dual-boot Windows and Ubuntu properly (recommend you follow)
[http://ubuntuforums.org/showthread.php?t=1649050](http://ubuntuforums.org/showthread.php?t=1649050)

Good Luck :D

---

### Post by kansasnoob on 2010-12-24
> **fastveg said:**
> Thanks for the advice theasprint.

Would you forsee any issues with me wiping away this WUBI installation (deleting everything on the U: partition) and reinstalling ubuntu from disc?

Considering the boot issues I was having would that break anything?

The Ubuntu 10.10 Live Installer (aka: ubiquity) has some issues/bugs. Look at posts #1 and #15 here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

So, if you're going to do a real install I'd recommend using the "Specify partitions manually (advanced)” option. It's not as scary as it sounds. If you want to do that I'd be glad to give you some partitioning recommendations if you'd post a screenshot of Gparted using the Live CD. Gparted is in System > Administration, the screenshot tool is in Accessories, and you can use the paperclip thingy at the top of the reply box to attach it. Also tell me how much space you'd like to give Ubuntu and how much RAM you have (if unsure the command **free** will show you).

I know nothing about 64 bit nor Chrome browser, sorry. I believe though that you can use the 32 bit (aka: i386) version of Ubuntu on 64 bit hardware.

Regarding the Wubi install be super sure to read all of this and ask questions there if you don't understand any part of it:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Certain package updates seem to continually break Wubi boots!!!!!!!!!!!

I need more coffee.

---

