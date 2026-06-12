---
title: "Kernel Panic not syncing VFS"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by ryadav on 2010-12-11
after a fresh install of Ubuntu 10.10 Server, I am getting,

** "Kernel Panic not syncing VFS : Unable to mount root fs on unknown-block(0,0)**"

how can I fix it?

---

### Post by ryadav on 2010-12-11
Here is my boot info, I would really like to get this solved!
Why am I able to boot off the rescue CD but not my HD?


                                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 30.8 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders, total 60074784 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       292,863       290,816  83 Linux
/dev/sda2             294,910    60,073,983    59,779,074   5 Extended
/dev/sda5             294,912     2,293,759     1,998,848  82 Linux swap / Solaris
/dev/sda6           2,295,808    60,073,983    57,778,176  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e1791282-9347-4c24-8bfb-be54309d1159   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ea7405bf-0ca2-47b5-85d9-ed03e228a1b0   swap                                     
/dev/sda6        68081c72-09eb-446b-b536-b00e2e61eedf   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,relatime,errors=remount-ro,barrier=1,data=ordered)
/dev/sda1        /boot                    ext4       (rw,relatime,barrier=1,data=ordered)
/dev/scd0        /media/cdrom             iso9660    (ro,relatime)
/dev/sda1        /boot                    ext4       (rw)


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=68081c72-09eb-446b-b536-b00e2e61eedf /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=e1791282-9347-4c24-8bfb-be54309d1159 /boot           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=ea7405bf-0ca2-47b5-85d9-ed03e228a1b0 none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  5a c8 cf a7 4f 56 c0 0c  23 6d a3 11 ab c9 ec 1b  |Z...OV..#m......|
00000010  7c cf 78 ab e2 2b 0e ea  bb 38 c3 88 d5 c7 3c a3  ||.x..+...8....<.|
00000020  bc bb 8d 22 cf 84 b1 e9  81 25 ef 9a 99 81 60 ab  |...".....%....`.|
00000030  33 a3 e7 62 65 16 b7 6d  86 b2 cd a2 80 e9 ed 89  |3..be..m........|
00000040  70 07 a1 6c 63 5f 63 b1  e5 8b 86 da cc 39 ca 74  |p..lc_c......9.t|
00000050  81 68 61 c6 31 18 ac 9e  9e 0b 9e d6 cc 9b 22 3e  |.ha.1.........">|
00000060  e4 a9 08 89 77 e2 50 a8  70 78 8c e6 7c f6 d8 e4  |....w.P.px..|...|
00000070  22 fc bc dc a9 37 ae 2e  16 6b 37 74 74 9e 08 11  |"....7...k7tt...|
00000080  df 4b 00 b1 28 90 19 63  df ad fc ec b1 f9 a3 97  |.K..(..c........|
00000090  94 9b 93 87 ea ab 46 38  56 7b d7 a5 ad ee 5e 71  |......F8V{....^q|
000000a0  fe c2 6d 10 5d b6 ff 70  1b 44 97 00 f5 08 76 96  |..m.]..p.D....v.|
000000b0  7f 7b 09 1c f1 68 62 87  7b 34 e7 af 78 e7 15 0e  |.{...hb.{4..x...|
000000c0  4d f2 1b 9e cd a1 34 9b  c4 a3 67 10 f5 4a a4 24  |M.....4...g..J.$|
000000d0  1e 9e 1e b8 92 a0 c3 28  1e 6a 4c 1e a1 e7 8f 56  |.......(.jL....V|
000000e0  9a f3 b3 15 16 85 b2 99  d3 57 fc 66 8f 23 27 52  |.........W.f.#'R|
000000f0  9b 71 04 a2 27 7b 72 6e  f0 3d fc 73 2c 47 db a5  |.q..'{rn.=.s,G..|
00000100  d3 26 f4 15 d3 b2 78 f4  b0 a3 cc 2d e7 74 ac b9  |.&....x....-.t..|
00000110  8b 3e 2e 8d a6 fb a7 87  c4 ac df 77 1e d2 6c c7  |.>.........w..l.|
00000120  a1 d9 b0 6f a9 af ce 33  e8 ea 10 d9 55 e9 af e1  |...o...3....U...|
00000130  0b 9f 82 2a f7 e6 17 e1  bd bd c0 ea 1e 1d 9d 6d  |...*...........m|
00000140  2c 1d 1d ac cb e9 f0 fd  b6 ee 52 24 ff 16 b0 03  |,.........R$....|
00000150  7b 09 a7 23 b0 76 96 9f  45 6c 90 94 65 69 26 ab  |{..#.v..El..ei&.|
00000160  a3 c1 c8 12 96 f3 12 b2  68 66 17 81 e8 96 c0 22  |........hf....."|
00000170  fa 66 3b dc 08 89 22 9d  3b fb 4f 23 66 1c 34 83  |.f;...".;.O#f.4.|
00000180  44 6c f1 5c af 57 8a b4  6f 73 36 72 21 b5 07 f3  |Dl.\.W..os6r!...|
00000190  19 84 a6 70 67 f5 26 1e  c6 8f 8a 58 5e 88 4d 05  |...pg.&....X^.M.|
000001a0  6d d6 cf fb 97 27 eb b9  d5 0e f5 3b b6 ac 20 98  |m....'.....;.. .|
000001b0  df ed ef f2 8d f3 ce aa  56 95 0a 6c 76 a8 00 5b  |........V..lv..[|
000001c0  0a 12 82 c6 38 8e 02 00  00 00 00 80 1e 00 00 c6  |....8...........|
000001d0  39 8e 05 fe ff ff 02 80  1e 00 00 a8 71 03 00 00  |9...........q...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by savithari on 2010-12-12
I am in the same situation since 3 weeks.  I have tried Ubuntu, Kubuntu, MythUbuntu but all is same.  Install is fine but after reboot (right after install) the messge I get is what you have typed.  Kernel Panic not syncing VFS uknown block (0,0)

-Narahari

---

### Post by ryadav on 2010-12-12
like you, i have tired xubuntu with the same result, i have tried multiple installs, reinstalled grub. went for ubuntu _server_, still i can't understand why i am seeing this kernel panic

i have tried passing in kernel parameters like: nomodeset, noapic, noacpi

this has to be a very simple error to fix, only if I understood what this kernel panic message meant

i while back before i gave up i even rebuilt the kernel from source

someone has to know how to fix this and correct ubuntu installer

---

