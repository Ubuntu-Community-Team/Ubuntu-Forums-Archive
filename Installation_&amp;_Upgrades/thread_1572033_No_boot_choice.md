---
title: "No boot choice"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by devildogmech on 2010-09-10
Hello all,
 I installed the netbook remix 10.04 on my Gateway LT2104u. The  installation went fine. I used the installer program from within ubuntu  after starting from my thumb drive. I completed the install, chose to  install besides win7 and after the program completed, I shut down the  PC, pulled the USB drive and restarted. WIN7 started! I never got an  option to choose ubuntu. I went back into the installer program and it  shows the unbuntu partition.
 I went to the BIOS to see if there was a setting I missed, but cant find anything.
 Any ideas?
 TIA
Billy

---

### Post by oldfred on 2010-09-10
Welcome to the forum.

It sounds like grub did not install to the MBR. Was there any error message? IF you do not specify with the advanced button (standard install, I assume the same for netbook) grub installs to sda. Sometimes a USB flash drive will become sda so maybe grub installed to that?

To see where everything is at, from you liveCD flash drive:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by devildogmech on 2010-09-18
As requested. Thanks!

```
            Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    25,173,854    25,173,792  27 Hidden HPFS/NTFS
/dev/sda2    *     25,173,855    25,382,699       208,845   7 HPFS/NTFS
/dev/sda3          25,382,700   284,749,001   259,366,302   7 HPFS/NTFS
/dev/sda4         284,749,822   488,396,799   203,646,978   5 Extended
/dev/sda5         284,749,824   482,447,359   197,697,536  83 Linux
/dev/sda6         482,449,408   488,396,799     5,947,392  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4012 MB, 4012900352 bytes
120 heads, 55 sectors/track, 1187 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     7,837,695     7,837,664   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C8481098480C6BC                       ntfs       PQSERVICE                     
/dev/sda2        58A0812DA0811324                       ntfs       SYSTEM RESERVED               
/dev/sda3        AA54827F54824DCF                       ntfs       Gateway                       
/dev/sda4: PTTYPE="dos" 
/dev/sda5        30fa8127-3597-4afc-b730-4f868a3eed74   ext4                                     
/dev/sda6        f107fe15-9aca-4abf-bb5d-79217c3454b4   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B836-DEC5                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/30fa8127-3597-4afc-b730-4f868a3eed74 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/SYSTEM RESERVED   fuseblk    (rw,nosuid,nodev,allow_other,blksize=512,default_permissions)
/dev/sda3        /media/Gateway           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=30fa8127-3597-4afc-b730-4f868a3eed74 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f107fe15-9aca-4abf-bb5d-79217c3454b4 none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  5e 00 3c 00 4d 00 69 00  63 00 72 00 6f 00 73 00  |^.<.M.i.c.r.o.s.|
00000010  6f 00 66 00 74 00 2d 00  57 00 69 00 6e 00 64 00  |o.f.t.-.W.i.n.d.|
00000020  6f 00 77 00 73 00 2d 00  4b 00 65 00 72 00 6e 00  |o.w.s.-.K.e.r.n.|
00000030  65 00 6c 00 2d 00 57 00  48 00 45 00 41 00 25 00  |e.l.-.W.H.E.A.%.|
00000040  34 00 4f 00 70 00 65 00  72 00 61 00 74 00 69 00  |4.O.p.e.r.a.t.i.|
00000050  6f 00 6e 00 61 00 6c 00  2e 00 65 00 76 00 74 00  |o.n.a.l...e.v.t.|
00000060  78 00 00 00 00 00 00 00  a8 00 00 00 02 00 00 00  |x...............|
00000070  56 5e 00 00 00 00 01 00  ed 19 00 00 00 00 01 00  |V^..............|
00000080  68 34 40 0c 00 00 00 00  6a e1 e0 d4 ae 23 cb 01  |h4@.....j....#..|
00000090  01 00 00 00 00 00 00 00  00 00 00 00 20 00 00 00  |............ ...|
000000a0  66 00 3c 00 4d 00 69 00  63 00 72 00 6f 00 73 00  |f.<.M.i.c.r.o.s.|
000000b0  6f 00 66 00 74 00 2d 00  57 00 69 00 6e 00 64 00  |o.f.t.-.W.i.n.d.|
000000c0  6f 00 77 00 73 00 2d 00  57 00 4c 00 41 00 4e 00  |o.w.s.-.W.L.A.N.|
000000d0  2d 00 41 00 75 00 74 00  6f 00 43 00 6f 00 6e 00  |-.A.u.t.o.C.o.n.|
000000e0  66 00 69 00 67 00 25 00  34 00 4f 00 70 00 65 00  |f.i.g.%.4.O.p.e.|
000000f0  72 00 61 00 74 00 69 00  6f 00 6e 00 61 00 6c 00  |r.a.t.i.o.n.a.l.|
00000100  2e 00 65 00 76 00 74 00  78 00 00 00 00 00 00 00  |..e.v.t.x.......|
00000110  d0 00 00 00 02 00 00 00  51 5e 00 00 00 00 01 00  |........Q^......|
00000120  ed 19 00 00 00 00 01 00  10 35 40 0c 00 00 00 00  |.........5@.....|
00000130  cc 4d f6 d4 ae 23 cb 01  01 00 00 00 00 00 00 00  |.M...#..........|
00000140  00 00 00 00 20 00 00 00  90 00 3c 00 4d 00 69 00  |.... .....<.M.i.|
00000150  63 00 72 00 6f 00 73 00  6f 00 66 00 74 00 2d 00  |c.r.o.s.o.f.t.-.|
00000160  57 00 69 00 6e 00 64 00  6f 00 77 00 73 00 2d 00  |W.i.n.d.o.w.s.-.|
00000170  57 00 69 00 6e 00 64 00  6f 00 77 00 73 00 20 00  |W.i.n.d.o.w.s. .|
00000180  46 00 69 00 72 00 65 00  77 00 61 00 6c 00 6c 00  |F.i.r.e.w.a.l.l.|
00000190  20 00 57 00 69 00 74 00  68 00 20 00 41 00 64 00  | .W.i.t.h. .A.d.|
000001a0  76 00 61 00 6e 00 63 00  65 00 64 00 20 00 53 00  |v.a.n.c.e.d. .S.|
000001b0  65 00 63 00 75 00 72 00  69 00 74 00 79 00 00 fe  |e.c.u.r.i.t.y...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 a0 c8 0b 00 fe  |................|
000001d0  ff ff 05 fe ff ff 91 a2  c8 0b 71 c5 5a 00 00 00  |..........q.Z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by wilee-nilee on 2010-09-18
sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

This is your partition, here is what the last line should read.
Boot files/dirs:   **/boot/grub/grub.cfg** /etc/fstab **/boot/grub/core.img**

Not sure if the script is not reading correctly or there are just missing files, which I highlighted.

There is also no grub bootloader in the mbr. So since you can get into Windows right now, we could assume it is a bad install for what ever reason, or wait for others to have a look at the script. Personally it looks like a bad install the script is missing a bunch of stuff.

---

### Post by devildogmech on 2010-09-19
How do I re-install? I tried to through the installer and it wanted to create a third partition. 

Billy

---

### Post by devildogmech on 2010-09-19
SOLVED! ( I think). I ended up having to run ubuntu from a usb drive, because Windows wouldn't see the partition. I re-formatted the screwed up ubuntu partition, and did a fresh install. Seems to be working, since I got the option to choose Ubuntu or Win7.... Here's to hoping its stable! 

Thanks for the help! 

Billy

---

### Post by wilee-nilee on 2010-09-19
> **devildogmech said:**
> SOLVED! ( I think). I ended up having to run ubuntu from a usb drive, because Windows wouldn't see the partition. I re-formatted the screwed up ubuntu partition, and did a fresh install. Seems to be working, since I got the option to choose Ubuntu or Win7.... Here's to hoping its stable! 

Thanks for the help! 

Billy

Good to hear your all set.

---

