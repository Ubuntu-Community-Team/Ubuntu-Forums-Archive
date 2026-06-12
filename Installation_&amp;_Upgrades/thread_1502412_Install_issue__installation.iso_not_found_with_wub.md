---
title: "Install issue:  installation.iso not found with wubi install"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by dataking on 2010-06-05
Hi all.

I am trying to install kubuntu using wubi and the "install within Windows" feature.

This is on a company asset where the base image cannot be modified, so I can't change the partition table or anything.

I ran the setup (wubi.exe) as administrator, and the install appears to go fine.  I get to the prompt to reboot now, or reboot manually later.  I go ahead and reboot now.

Upon reboot, I get the Windows boot prompt with kubuntu in the menu.  I select kubuntu to stop the timer and pop in the CD.  Then I hit enter.

The kubuntu splash screen comes up and flashes a couple times, and then I get a prompt that the installation ISO cannot be found, and I should run 'chkdsk' in Windows.

Here is the complete message:
Could not find the ISO /ubuntu/install/installation.iso  This could also happen if the file system is not clean because of an operating system crash, an interrupted boot process, an improper shutdown, or unplugging of a removable device without first unmounting or ejecting it.  To fix this, simply reboot into Windows, let it fully start, log in, run 'chkdsk /r', then gracefully shut down and reboot back into Windows.  After this you should be able to reboot again and resume the installation.

Naturally, running chkdsk was one of the first things I tried.  No matter how many times I run chkdsk and reboot and reboot, I still get the message (I've tried several times).

Upon the advice of one of the developers, I ran the [bootinfoscript]("http://bootinfoscript.sourceforge.net") while using the Demo mode of kubuntu.  Here are the results:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub  is installed in the MBR of /dev/sda and looks at sector 414 of the 
    same hard drive for the stage2 file, but no stage2 files can be found at 
    this location.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   312,578,047   312,576,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  c8 09 c7 8c 32 6b f0 ab  ef 1f ea 4b aa 9d bb 54  |....2k.....K...T|
00000010  46 0d 24 5b ad 2f ae ca  0f 8c 2e db 80 3e 9f 3b  |F.$[./.......>.;|
00000020  26 50 75 87 09 ea 54 37  ae 75 c8 50 ed cf e5 ea  |&Pu...T7.u.P....|
00000030  14 ea 06 d4 f0 f3 d4 72  f1 15 42 a0 4b 11 9b d9  |.......r..B.K...|
00000040  c0 80 b4 d8 19 c1 17 ba  ba da 94 54 4c ab c2 05  |...........TL...|
00000050  b2 b5 d3 39 75 15 51 a9  a5 98 12 84 62 35 b0 c8  |...9u.Q.....b5..|
00000060  85 a8 e9 7c 37 c6 96 39  98 22 e5 4e 62 db 26 cb  |...|7..9.".Nb.&.|
00000070  df a7 c8 5c 0a cd 78 70  31 f3 d1 42 f7 94 22 f5  |...\..xp1..B..".|
00000080  39 a0 83 19 57 f4 8f 00  bc 0c df 71 9b b3 c2 d9  |9...W......q....|
00000090  a8 e5 a6 e3 af 1e 8e 6c  74 7e 42 48 d2 97 98 11  |.......lt~BH....|
000000a0  f7 64 08 93 a5 23 1c 34  4a c1 a6 05 d2 81 ef e6  |.d...#.4J.......|
000000b0  d4 e8 87 f2 c2 33 d8 7a  10 1e 06 e7 77 ff 2a 40  |.....3.z....w.*@|
000000c0  19 c8 d0 68 d0 9b b2 0b  0e 3f 18 a3 8e 52 62 28  |...h.....?...Rb(|
000000d0  31 bc d4 3d 06 fa 76 d4  5f c5 2f 07 36 31 b3 ae  |1..=..v._./.61..|
000000e0  6b e2 b2 67 ae 87 9c 2c  c8 85 dd 8a 34 32 36 12  |k..g...,....426.|
000000f0  7a 01 8c 6a 3a 73 24 af  fa 9c ef 30 cb 28 b2 9b  |z..j:s$....0.(..|
00000100  4d c9 a7 31 09 2a b4 fe  0c 7e 00 a4 93 b4 67 26  |M..1.*...~....g&|
00000110  b9 82 c9 80 fa 9d 6a d2  67 d3 4d 43 01 ef d0 68  |......j.g.MC...h|
00000120  cc b9 d1 25 d0 a4 bf c6  f2 05 84 86 bd 75 1d 36  |...%.........u.6|
00000130  1d 1d bf 44 b8 d7 09 5f  3f ee e9 43 01 06 72 f0  |...D..._?..C..r.|
00000140  19 6f d9 37 0c 2f 95 52  63 df af ec 7d 0b b2 d5  |.o.7./.Rc...}...|
00000150  e4 8c 37 b6 28 ab 81 a5  41 c9 62 d6 21 da 3d e5  |..7.(...A.b.!.=.|
00000160  62 df d2 64 a0 84 d0 f3  4f b6 c1 68 e7 19 8a ea  |b..d....O..h....|
00000170  b0 2e 54 d7 86 7f 5d fe  da 63 ca 00 16 c8 3d 6e  |..T...]..c....=n|
00000180  d4 10 d2 87 ee dc db 6a  1a dc d6 28 bf b0 c7 9b  |.......j...(....|
00000190  00 60 9d f2 27 c0 a4 c9  d5 59 55 be 76 d0 c2 db  |.`..'....YU.v...|
000001a0  6a f3 59 8f 20 6f 99 31  69 38 dc 51 12 69 24 46  |j.Y. o.1i8.Q.i$F|
000001b0  56 01 b3 37 34 ef 5a 9a  11 1b 94 1c a2 a7 4a e9  |V..74.Z.......J.|
000001c0  17 0d f8 9b b5 4f 26 7e  12 ef e5 12 b9 83 16 c3  |.....O&~........|
000001d0  1c d2 10 49 8b b7 5e 47  c4 ac 4b 74 e4 c3 37 51  |...I..^G..Kt..7Q|
000001e0  5b 3f c6 10 91 b7 f3 7e  28 6d d5 19 11 58 87 8d  |[?.....~(m...X..|
000001f0  16 73 5b ae bd ba 8a d4  52 68 3a 38 1d e6 e7 e4  |.s[.....Rh:8....|
00000200

```

Troubleshooting steps:

So far I have tried mounting the hard drive and the cdrom to various mount points (/, /cdrom, /isodevice) and tried rerunning the script that seems to give the failure (/scripts/casper-premount/20iso_scan).  All continue to fail.  The CD has the /ubuntu/install directory, but not the installation.iso.

I am currently unable to mount the hard drive because it is not recognized as a valid NTFS file system.  The hard drive is currently whole-disk encrypted, so I'm going to try decrypting the drive and start the process again.  The PGP passphrase prompt comes before the OS boot prompt, so I assumed that the disk would be "available".

I am using the 64-bit kubuntu 10.04 LTS CD for the install.  The base Windows image is Windows 7 (x64).

Thanks for any advice you might be able to offer.

---

### Post by hirulez on 2011-02-22
anyone can help with this as i have the same problem with dataking

---

### Post by JTallis on 2011-03-25
Same issue. :(

---

### Post by Phat_HC on 2011-05-25
I just attempted to install Ubuntu for the first time on my Windows 7 system and have received this same issue.  I'd love to try this flavor of Linux but being fairly new to Linux as a whole I'm stuck on how to role this forward.

Please help

---

### Post by mattydee on 2011-08-27
Same issue here after installing wubi on windows7.
EDIT: I have full hard drive encryption as the OP does (I Used TrueCrypt), but the error message appears after the boot password. One would think that the drive is decrypted after entering the boot password. However, the HD is decrypted on the fly with TC so, even after you enter the boot password, the system needs TC to do decryption. This is probably the issue...

---

### Post by ottosykora on 2011-08-27
I am  not 100% sure what you are trying to do, but in times when I was using wubi, I installed either via net, that means the wubi did in fact download the iso files itself, or otherwise I downloaded the iso from the ubuntu server, placed it next to the wubi installer and this di either pick it automatically or if it was placed in some other folder I had to point the wubi to it. So what CD you put in? 
With the iso file on it or ..?

So just point the wubi to the iso, thats it.

---

### Post by ottosykora on 2011-08-27
@mattydee
>However, the HD is decrypted on the fly with TC so, even after you enter the boot password, the system needs TC to do decryption. This is probably the issue...<

yes definitely. In you case the low level service has to run to be able to decrypt on the fly.

People still think, that installing with wubi will provide them some kind of virtual machine running inside windows. This is not the case. Only the wubi installer itself is a windows program, when linux installed, there is a bootmanager active and this alows you to select windows or linux. Linux is then run istead of windows, windows does not run in that case and so do not run any programs and services from windows.
The major difference to a full linux install is, that all the linux is kept in virtual drives, which are just files on the windows drive ...which is probably encrypted once all is flushed an linux attempts to start.

---

