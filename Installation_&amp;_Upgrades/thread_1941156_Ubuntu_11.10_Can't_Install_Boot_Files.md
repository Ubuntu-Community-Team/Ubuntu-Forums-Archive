---
title: "Ubuntu 11.10 Can't Install Boot Files"
date: 2012-03-15
forum: Installation &amp; Upgrades
---

### Post by AliMoradi on 2012-03-15
I'm trying to install Ubuntu 11.10 64-bit alongside windows, and the entire installation process went fine, however, it was unable to install the boot files. I get the following error:

[CENTER]**Fatal Error: Sorry, an error occurred and it was not possible to install the bootloader at the specified location.**
[/CENTER]

I know this is a common issue and have read on a few other threads about it, but unfortunately none of the other solutions seems to work for me. I'm hoping you guys have some suggestions for me. I'm attaching my boot info on this thread in case it's of any help. I appreciate any help you guys can give!

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No known boot loader is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

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

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1     ? 1,936,269,394 3,772,285,809 1,836,016,416   7 NTFS / exFAT / HPFS
/dev/sda2     ? 1,917,848,077 2,462,285,169   544,437,093  73 Unknown
/dev/sda3     ? 1,818,575,915 2,362,751,050   544,175,136  2b SyllableSecure
/dev/sda4     ? 2,844,524,554 2,844,579,527        54,974  61 SpeedStor

/dev/sda1 ends after the last sector of /dev/sda
/dev/sda1 overlaps with /dev/sda2
/dev/sda1 overlaps with /dev/sda3
/dev/sda1 overlaps with /dev/sda4
/dev/sda2 ends after the last sector of /dev/sda
/dev/sda2 overlaps with /dev/sda3
/dev/sda3 ends after the last sector of /dev/sda
/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848 1,270,138,151 1,269,931,304   7 NTFS / exFAT / HPFS
/dev/sdb3       1,270,138,878 1,953,523,711   683,384,834   5 Extended
/dev/sdb5       1,270,138,880 1,919,975,423   649,836,544  83 Linux
/dev/sdb6       1,919,977,472 1,953,523,711    33,546,240  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        1C1408F31408D226                       ntfs       System Reserved
/dev/sdb2        3CDA0AFFDA0AB564                       ntfs       
/dev/sdb5        ce8e6453-c3ff-4bc7-83b7-dbce2c0a30b1   ext4       
/dev/sdb6        6d52adcd-614e-44c8-8f87-f60f23ba9b86   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=ce8e6453-c3ff-4bc7-83b7-dbce2c0a30b1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=6d52adcd-614e-44c8-8f87-f60f23ba9b86 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sda

00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  a8 6d 70 74 00 00 00 00  |.........mpt....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  3e 99 ce 2a ba ce 2a d4  |........>..*..*.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 07 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BO.TMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

Unknown BootLoader on sda1


Unknown BootLoader on sda2

00000000  14 03 78 56 4b 0a 52 d1  70 8b 6e d3 64 56 38 b1  |..xVK.R.p.n.dV8.|
00000010  73 b7 d3 d0 e4 b6 a1 1a  17 44 6b be 46 eb c3 8c  |s........Dk.F...|
00000020  a4 84 0b 1b 49 70 5e dc  03 88 4f 6d 5b 1a 06 51  |....Ip^...Om[..Q|
00000030  02 30 5e 19 81 c9 10 02  01 b0 6a d4 6e a4 77 68  |.0^.......j.n.wh|
00000040  e6 17 72 34 5d 96 bc 62  2a dd 37 f3 da 9b ee ae  |..r4]..b*.7.....|
00000050  33 4e e3 31 c7 25 27 38  d9 37 6a 7f ec b4 ad 44  |3N.1.%'8.7j....D|
00000060  48 08 23 76 6a a6 62 4f  e7 19 71 ae 2e 0f d3 bd  |H.#vj.bO..q.....|
00000070  a9 5e 87 4e 69 de 7c 62  44 10 57 d6 05 b8 61 ca  |.^.Ni.|bD.W...a.|
00000080  21 40 20 49 29 88 27 41  19 47 7d dd d2 6a 38 1f  |!@ I).'A.G}..j8.|
00000090  3d 4b 64 24 e9 4c 85 fa  70 8e 64 3d 21 f2 7b e3  |=Kd$.L..p.d=!.{.|
000000a0  cd ee 5c b4 a5 bc ed ec  6d 68 97 50 b8 c4 d6 b2  |..\.....mh.P....|
000000b0  1c 0c 1b ee 49 4e 87 41  a0 a2 71 8a 7f d5 7e e6  |....IN.A..q...~.|
000000c0  ba 43 dc f3 74 59 fc 6c  05 27 d7 b9 9a ab 7a 9a  |.C..tY.l.'....z.|
000000d0  cc 1a c3 ef 2e 9d 3a 22  74 ba 06 0e 88 f5 10 e2  |......:"t.......|
000000e0  a9 da d5 cd b1 2b 0b f6  69 3b 68 ed 2b 02 68 b5  |.....+..i;h.+.h.|
000000f0  6d a0 5d 57 a6 b4 98 dd  f3 5a d0 bc 62 0b 21 45  |m.]W.....Z..b.!E|
00000100  f3 29 68 02 44 2f 87 01  29 b3 da 7e db 25 e8 d9  |.)h.D/..)..~.%..|
00000110  cc 56 57 75 fa e9 26 47  ba 12 56 89 6a 26 1b 75  |.VWu..&G..V.j&.u|
00000120  8e 9c ad 37 3e a2 77 5e  cc 02 a6 69 bd e3 8d 8d  |...7>.w^...i....|
00000130  43 5c a1 cf e8 51 f8 25  18 8a 6d 8a a9 1c 96 77  |C\...Q.%..m....w|
00000140  91 7d 05 b3 f3 0c e1 f0  56 b6 1f 48 cd 21 8b 6d  |.}......V..H.!.m|
00000150  14 74 72 64 f1 15 0b df  1b cd 42 26 ba 31 04 1b  |.trd......B&.1..|
00000160  bb 38 e1 8e 2e 3d f7 fd  a0 81 27 2a a6 af 38 15  |.8...=....'*..8.|
00000170  c6 c0 3d 4c c0 c5 30 48  43 dc 7f 2f 9a 95 f7 e2  |..=L..0HC../....|
00000180  54 d0 7a b3 9b f0 4e 99  4f d8 97 2e 2f 80 49 05  |T.z...N.O.../.I.|
00000190  b1 b5 a0 0c 11 49 99 f8  4a 91 80 cc 26 94 d2 e6  |.....I..J...&...|
000001a0  ed df 68 05 17 a8 4b 3f  02 02 98 ef 6a 8b e0 d5  |..h...K?....j...|
000001b0  2d e4 34 52 9b 9f b1 8a  6e db 5c 13 a0 e8 e9 78  |-.4R....n.\....x|
000001c0  72 bb f5 cb e2 be 9a 75  f5 19 50 bb 25 91 32 55  |r......u..P.%.2U|
000001d0  2a 43 9d 3e 50 90 94 00  33 07 47 55 93 10 65 9a  |*C.>P...3.GU..e.|
000001e0  13 44 b9 9c e2 d0 e0 65  05 d1 55 46 d9 15 73 4c  |.D.....e..UF..sL|
000001f0  8b ff d7 56 45 fa 79 a6  28 df 11 d4 7c cd 74 5e  |...VE.y.(...|.t^|
00000200

Unknown BootLoader on sda3

00000000  01 13 0c fe 65 0a b6 04  4c 33 cd 05 a9 64 f6 a7  |....e...L3...d..|
00000010  bc 7c 84 6f 3e d6 95 48  40 16 28 76 1d f7 18 a1  |.|.o>..H@.(v....|
00000020  f0 af 2c 10 34 f7 8f 54  02 8b 90 61 18 d8 e2 45  |..,.4..T...a...E|
00000030  04 25 dd 8a b8 7f 93 0d  1d 55 bf 8a ba 24 41 6c  |.%.......U...$Al|
00000040  69 fc ea 70 95 a5 9e 48  ba 81 a8 e8 24 b9 5f 05  |i..p...H....$._.|
00000050  df 7c d3 c1 f8 ba 31 c2  61 ac c3 9a b0 70 a7 b9  |.|....1.a....p..|
00000060  19 1a d6 20 a4 f4 dc ef  25 b1 e0 2c 5b 52 cf 62  |... ....%..,[R.b|
00000070  40 c2 44 a5 57 c3 e9 c8  f7 13 6f ae 71 54 02 5f  |@.D.W.....o.qT._|
00000080  ad c3 7b 9a c0 3d ea 51  a6 06 2b db 45 67 83 22  |..{..=.Q..+.Eg."|
00000090  e3 86 e7 61 62 f6 e2 84  5e 1e 52 6e 4b f8 98 82  |...ab...^.RnK...|
000000a0  3f b0 21 c7 0b 3c 5a 6f  4c d0 a3 96 f6 5d ae fc  |?.!..<ZoL....]..|
000000b0  29 dc a4 79 6f ac 47 1e  46 60 1f 56 f9 4a 14 f4  |)..yo.G.F`.V.J..|
000000c0  b4 48 1c 25 8b 8b 23 e4  3c ef 6a 8a 6a 0e b4 f2  |.H.%..#.<.j.j...|
000000d0  a0 87 a4 fc 10 2e d3 50  4a 94 43 47 20 ed 87 d7  |.......PJ.CG ...|
000000e0  23 86 50 60 27 8a bb 2e  85 87 34 5c d3 95 77 6a  |#.P`'.....4\..wj|
000000f0  bb f8 22 f8 a5 c6 dd e6  33 36 b8 e4 4c 57 7b 34  |..".....36..LW{4|
00000100  63 a9 29 09 03 5e 13 43  ad d9 0b 38 b2 e1 e8 c3  |c.)..^.C...8....|
00000110  a1 94 4a b1 69 4c 53 25  8d 9c 9f 12 43 2a 30 bb  |..J.iLS%....C*0.|
00000120  de 2f 40 8d 77 89 d7 55  88 67 51 3b 0c ce 2f 92  |./@.w..U.gQ;../.|
00000130  19 e2 37 f4 79 09 09 9b  d5 30 73 91 30 0b 23 c1  |..7.y....0s.0.#.|
00000140  fc ba 61 c9 89 07 f0 e3  ef 61 f3 9b f0 52 d8 20  |..a......a...R. |
00000150  8a b8 c7 f7 be 78 9e b9  4c 9f e9 ae c8 dc 11 14  |.....x..L.......|
00000160  08 1a 20 99 ad fb 23 0b  0f fe 7c 65 62 31 da 24  |.. ...#...|eb1.$|
00000170  ae c0 9c f6 5d 70 06 27  6f a3 10 88 d4 4c 29 9a  |....]p.'o....L).|
00000180  b3 03 09 a4 91 4a 70 74  83 a3 f2 3d cc 51 6c 9d  |.....Jpt...=.Ql.|
00000190  e8 d7 f1 04 4c d6 65 05  26 97 94 48 8c 20 d3 20  |....L.e.&..H. . |
000001a0  d4 92 f2 09 71 75 49 be  f9 52 1b 4e 0f 24 55 7b  |....quI..R.N.$U{|
000001b0  a4 4a fe 29 41 b7 90 9a  15 db 42 ba ad c6 94 28  |.J.)A.....B....(|
000001c0  23 83 f5 28 d1 e4 c0 c0  dc 95 3a e7 6d a8 35 ca  |#..(......:.m.5.|
000001d0  13 40 81 0f bc 41 1e 09  9e ae 0d f2 b5 9b 4f d2  |.@...A........O.|
000001e0  b8 8b 04 da 7f 1f b7 78  1d cc 97 ab 62 33 05 95  |.......x....b3..|
000001f0  8a 04 9b 30 3e ba 0c 4e  40 c1 02 c4 48 20 a9 1e  |...0>..N@...H ..|
00000200

Unknown BootLoader on sda4



========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by AliMoradi on 2012-03-15
Just some more information about my computer:

I have two hard drives, C and D. 

Hard Drive C has four partitions; 100 MB NTFS for system reserves, 605.55 GB NTFS for Windows 7, 309.87 GB for Ubuntu, and 16 GB that I have no idea what its purpose is.

Hard Drive D has only one partition where I keep all my data files.

I'm not exactly sure which of these partitions Ubuntu is trying to install the bootloader on, but I can only imagine that it's installing it in the same partition that Ubuntu was installed on.

I made the Ubuntu partition and installed Ubuntu using the 'alongside' method, but I know in some other threads it was mentioned that this isn't the best way to do it. Should I try to delete that partition and re-install Ubuntu manually?

---

### Post by darkod on 2012-03-15
The disk reported as /dev/sda is your data disk. The disk reported as /dev/sdb is your Win7/Ubuntu disk.

First of all, have you noticed the errors in the results saying that the partitions on /dev/sda don't look right? It seems thee is overlapping and outside of the disk, which is impossible.

As for grub2, it didn't install from what ever reason. You can try to enter your root partition with chroot and install it. Boot with the cd in live mode, and in terminal you will need to do:
```
sudo mount /dev/sdb5 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Now you can run command as within the installation:
```
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/sdb
```

Exit the chroot and unmount all:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Restart and see if it helped.

---

### Post by AliMoradi on 2012-03-15
This worked perfectly. Thank you for your help!

---

