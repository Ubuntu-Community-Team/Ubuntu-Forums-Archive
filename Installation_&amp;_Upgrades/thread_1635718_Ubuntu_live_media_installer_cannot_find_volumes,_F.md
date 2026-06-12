---
title: "Ubuntu live media installer cannot find volumes, Fedora live does"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by kjetilbmoe on 2010-12-02
Ubuntu community,

I have a computer running Red hat (some 2007 old version), and would like to install a fresh 64bit Ubuntu 10.10 in addition to this. The live ubuntu usb installer launches perfectly - but now it cannot find a single harddrive (there are 2, separate ones). This troubles me. I would like to change the partitions a bit upon installing.

The system boots to Red hat just fine when not using the Ubuntu usb, and is able to find all the disks. Running a live Fedora USB discovers the drives, but is not able to "read" or mount them properly - I get "daemon is inhibited".

The drives seems to be formatted as ext3.

How do I proceed to install Ubuntu?

---

### Post by oldfred on 2010-12-02
It may be how drives are formated or ?

To see what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

I would probably download the newest gparted liveCD and see if that lets me create the partitions.

---

### Post by kjetilbmoe on 2010-12-02
Here you go. I couldn't see any obvious errors though...

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.93 is installed in the MBR of /dev/sda and looks at sector 47755 on 
    boot drive #1 for the stage2 file. A stage2 file is at this location on 
    /dev/sda. Stage2 looks on partition #1 for /grub/grub.conf.
 => Grub  is installed in the MBR of /dev/sdb and looks at sector 91201 on 
    boot drive #1 for the stage2 file, but no stage2 files can be found at 
    this location.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Red Hat Enterprise Linux WS 
                       release 3 (Taroon Update 5) Kernel on an
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 73.4 GB, 73407865856 bytes
255 heads, 63 sectors/track, 8924 cylinders, total 143374738 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       208,844       208,782  83 Linux
/dev/sda2             208,845   126,977,759   126,768,915  83 Linux
/dev/sda3         126,977,760   143,364,059    16,386,300  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 146.8 GB, 146815737856 bytes
255 heads, 63 sectors/track, 17849 cylinders, total 286749488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   286,744,184   286,744,122  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4007 MB, 4007657472 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     7,823,654     7,823,592   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop2                                              squashfs                                 
/dev/loop3       48d0835e-93a9-42e3-a057-441099473325   ext4       Fedora-13-i686-L              
/dev/loop4                                              DM_snapshot_cow                               
/dev/mapper/live-osimg-min 48d0835e-93a9-42e3-a057-441099473325   ext4       Fedora-13-i686-L              
/dev/mapper/live-rw 48d0835e-93a9-42e3-a057-441099473325   ext4       Fedora-13-i686-L              
/dev/sda1        9a73135e-3e10-417d-abe5-0f93d695d2a5   ext3       /boot                         
/dev/sda2        d9c22739-9cd3-43d0-85ec-785b1a5f7407   ext3       /                             
/dev/sda3                                               swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        601295e7-d585-47ef-899b-51d3c2c55926   ext3       /disk1                        
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        8870-099A                              vfat       T1                            
/dev/sdc: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
live-osimg-min
live-rw

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/live-rw /                        ext4       (rw,noatime)
/dev/sdc1        /media/T1                vfat       (rw,nosuid,nodev,uhelper=udisks,uid=500,gid=500,shortname=mixed,dmask=0077,utf8=1,flush)


============================= sda1/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/sda2
#          initrd /initrd-version.img
#boot=/dev/sda
default=0
timeout=10
splashimage=(hd0,0)/grub/splash.xpm.gz
title Red Hat Enterprise Linux WS (2.4.21-32.ELsmp)
	root (hd0,0)
	kernel /vmlinuz-2.4.21-32.ELsmp ro root=LABEL=/ hda=ide-scsi
	initrd /initrd-2.4.21-32.ELsmp.img
title Red Hat Enterprise Linux WS-up (2.4.21-32.EL)
	root (hd0,0)
	kernel /vmlinuz-2.4.21-32.EL ro root=LABEL=/ hda=ide-scsi
	initrd /initrd-2.4.21-32.EL.img

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/grub.conf
    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd-2.4.21-32.EL.img
    .0GB: initrd-2.4.21-32.ELsmp.img
    .0GB: vmlinuz-2.4.21-32.EL
    .0GB: vmlinuz-2.4.21-32.ELsmp

=============================== sda2/etc/fstab: ===============================

LABEL=/                 /                       ext3    defaults        1 1
LABEL=/boot             /boot                   ext3    defaults        1 2
none                    /dev/pts                devpts  gid=5,mode=620  0 0
LABEL=/disk1            /disk1                  ext3    defaults        1 2
none                    /proc                   proc    defaults        0 0
none                    /dev/shm                tmpfs   defaults        0 0
/dev/sda3               swap                    swap    defaults        0 0
/dev/cdrom              /mnt/cdrom              udf,iso9660 noauto,owner,kudzu,ro 0 0
/dev/fd0                /mnt/floppy             auto    noauto,owner,kudzu 0 0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  1f d7 8d 5d 02 4e 06 bf  c4 67 40 76 60 df f8 be  |...].N...g@v`...|
00000010  1e 5a 3a 81 26 ba fe be  27 51 cf 91 9e d6 f5 3e  |.Z:.&...'Q.....>|
00000020  55 47 08 85 26 2a 05 bf  27 6a 2f 7b 27 6c 01 bf  |UG..&*..'j/{'l..|
00000030  fc 6f 9a a7 2e 13 f9 3e  5c c6 6f 49 de 13 fd 3e  |.o.....>\.oI...>|
00000040  cb 4e 05 f9 31 13 fb 3e  0b e8 65 5a 74 a2 04 bf  |.N..1..>..eZt...|
00000050  ea 11 c6 ee 0b da 08 3f  be 9a 26 46 5c e8 d0 be  |.......?..&F\...|
00000060  63 e3 a8 e1 b5 41 06 bf  4f b5 1a 40 cf 19 0b 3f  |c....A..O..@...?|
00000070  0f 55 26 fe e5 6a f0 3e  f3 e5 07 a2 7a 75 46 3f  |.U&..j.>....zuF?|
00000080  28 d5 5a fe 75 60 4c bf  d8 5c c5 53 37 22 54 bf  |(.Z.u`L..\.S7"T.|
00000090  2b 7f d7 d9 c8 2e 06 bf  41 43 4e 79 00 c1 23 bf  |+.......ACNy..#.|
000000a0  b9 e1 2b 19 79 69 3f bf  eb 68 1e 12 56 fd e9 3e  |..+.yi?..h..V..>|
000000b0  0f 34 d9 a0 49 ea 03 bf  9c 14 82 2f 76 db 22 bf  |.4..I....../v.".|
000000c0  d0 16 4a 2d df bb 16 3f  c9 77 1c 29 ed 75 23 bf  |..J-...?.w.).u#.|
000000d0  82 55 5e 25 54 35 3c bf  e8 a8 fe 93 86 11 32 bf  |.U^%T5<.......2.|
000000e0  28 53 d6 95 4f 93 0d 3f  ad d9 6e 7e db 39 fe be  |(S..O..?..n~.9..|
000000f0  06 6a 39 3d 21 a2 15 bf  7e 3e 24 f4 a7 73 e0 be  |.j9=!...~>$..s..|
00000100  9b 9c 65 75 3f 4b f7 be  b8 b5 e7 a5 61 3e 33 bf  |..eu?K......a>3.|
00000110  0e b0 65 9e 2a f4 50 bf  6f 2e 7c 62 38 22 5d bf  |..e.*.P.o.|b8"].|
00000120  d4 21 6d be 96 85 4c 3f  28 1e f1 ba 33 e5 59 bf  |.!m...L?(...3.Y.|
00000130  c1 5a fa 25 53 64 62 bf  7c 92 43 01 9b 1f 32 3f  |.Z.%Sdb.|.C...2?|
00000140  3a c7 eb 23 01 08 43 bf  19 27 af 74 4c 63 52 bf  |:..#..C..'.tLcR.|
00000150  d2 cf e7 88 a3 9a 20 bf  b4 a9 97 b7 eb dc 0b 3f  |...... ........?|
00000160  82 99 0e e7 98 cd 1e 3f  24 2b af 32 0e be 1a bf  |.......?$+.2....|
00000170  2f 61 0a fa fd 20 0d bf  74 a0 cd 84 95 9b 0f bf  |/a... ..t.......|
00000180  e3 a0 43 10 82 e9 21 bf  c6 72 5c 7c 68 8e 11 bf  |..C...!..r\|h...|
00000190  f1 af c2 60 ae fe 3a bf  41 e6 57 7e fb eb 10 3f  |...`..:.A.W~...?|
000001a0  05 54 1f 47 01 1b 20 bf  df 87 6a 12 1d fa 38 bf  |.T.G.. ...j...8.|
000001b0  e3 91 a6 03 1c 10 fe 3e  a4 4c 85 80 a6 eb fc 3e  |.......>.L.....>|
000001c0  41 de ae c6 38 ad 0e 3f  b9 72 86 b1 16 77 12 bf  |A...8..?.r...w..|
000001d0  f5 6d bd 18 37 4d 31 bf  cb be 8a 84 fa a6 57 bf  |.m..7M1.......W.|
000001e0  db fd 46 99 fd 76 09 3f  75 d3 2f 08 4c b7 0b bf  |..F..v.?u./.L...|
000001f0  c5 2b e7 81 cf 0b 15 bf  8f 8d 79 53 ff af df 3e  |.+........yS...>|
00000200


=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file or automatically
```

---

### Post by oldfred on 2010-12-02
If you run gparted from the Ubuntu liveCD can you see partitions. You may have to swapoff on the swap partition as that often is auto mounted.

---

### Post by kjetilbmoe on 2010-12-03
I managed to create a partition with Fedora live usb - though it *still *does not show up in Ubuntu installer. Neither in the alternate installer.

The problem may be related to SCSI disks, and as I search for issues on this, it seems to have been a problem for quite a number of people lately. Though I cannot find any specific solution to this.

---

### Post by sikander3786 on 2010-12-03
If there is an option in the Bios, switching HDD mode to ahci or compatible might help.

---

