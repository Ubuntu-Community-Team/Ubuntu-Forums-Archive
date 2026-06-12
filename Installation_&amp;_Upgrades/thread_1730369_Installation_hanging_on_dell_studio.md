---
title: "Installation hanging on dell studio"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by installationfailed on 2011-04-16
Hello

I'm currently trying to install ubuntu but the installation process hangs on the second page of the installation
(right after select language)
[IMG]http://i.imgur.com/GWRCC.png[/IMG]

I am booting from a usb. NO other OS is installed and I'm currently in "try it now" mode
What am I doing wrong??

Regards

---

### Post by Hedgehog1 on 2011-04-16
Does you computer have at least 512 megs of RAM?  This is a minimum requirement to load (1 gig is preferred for acceptable operation).  If you have enough RAM, then please do this so we can see about your hard disk configuration:


Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by installationfailed on 2011-04-16
thanks for the reply Hedgehog!
edit: i have more then 512mb ram

```

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

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

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325    30,800,324    30,720,000   7 HPFS/NTFS
/dev/sda3          30,800,325   976,771,119   945,970,795   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4007 MB, 4007264256 bytes
74 heads, 10 sectors/track, 10576 cylinders, total 7826688 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,826,687     7,818,624   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        9CFE33DBFE33AC80                       ntfs                                     
/dev/sda3        EED42F69D42F336F                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E23D-4652                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/EED42F69D42F336F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb1/boot/grub/grub.cfg: ===========================


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

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 20 1a 11  |.X.SYSLINUX.. ..|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......|
00000020  80 4d 77 00 73 07 00 00  00 00 00 00 02 00 00 00  |.Mw.s...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 52 46 3d e2 4e  4f 20 4e 41 4d 45 20 20  |..)RF=.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 20  20 00 00 66 ba 00 00 00  |..E}.f.  ..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by Hedgehog1 on 2011-04-16
> **installationfailed said:**
> I am booting from a usb. **_NO other OS is installed_** and I'm currently in "try it now" mode
What am I doing wrong??

installationfailed,

Thanks for posting the script results.

Your 1st post says that 'NO other OS is installed', but I see an OS **is** already installed on your hard drive:

```
/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325    30,800,324    30,720,000   7 HPFS/NTFS
/dev/sda3          30,800,325   976,771,119   945,970,795   7 HPFS/NTFS
```

The partition layout appears to be the Vista/Windows 7 layout.

So I have two questions for you:

1) Is your plan to overwrite the disk with Ubuntu (and wipe out Windows)? Or are you planning to dual-boot Windows & Ubuntu?

2) Just to be clear - when you press to orange 'forward' button shown on the screen shot, nothing happens, right?

***The Hedge***

:KS

p.s. If you did not download the ISO using a Bit Torrent client, these is always the possibility of the ISO being damaged.  Please feel free to re-download it using a Bit Torrent client and create a fresh LiveCD (burned at this slowest speed) or a fresh LiveUSB preferably on a different USB that is not the same brand (some brands of USB will not load 'gparted' or 'parted' during a 10.10 install; the installed is getting near to at the call to 'parted' to figure out what install options to offer.

---

### Post by installationfailed on 2011-04-16
> **Hedgehog1 said:**
> installationfailed,

Thanks for posting the script results.

Your 1st post says that 'NO other OS is installed', but I see an OS **is** already installed on your hard drive:

```
/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325    30,800,324    30,720,000   7 HPFS/NTFS
/dev/sda3          30,800,325   976,771,119   945,970,795   7 HPFS/NTFS
```The partition layout appears to be the Vista/Windows 7 layout.

So I have two questions for you:

1) Is your plan to overwrite the disk with Ubuntu (and wipe out Windows)? Or are you planning to dual-boot Windows & Ubuntu?

2) Just to be clear - when you press to orange 'forward' button shown on the screen shot, nothing happens, right?

***The Hedge***

:KS

p.s. If you did not download the ISO using a Bit Torrent client, these is always the possibility of the ISO being damaged.  Please feel free to re-download it using a Bit Torrent client and create a fresh LiveCD (burned at this slowest speed) or a fresh LiveUSB preferably on a different USB that is not the same brand (some brands of USB will not load 'gparted' or 'parted' during a 10.10 install; the installed is getting near to at the call to 'parted' to figure out what install options to offer.


1:  plan to have the 1 OS
2: Yes when I click the orange forward it hangs

I will re download the iso using a torrent and update you.

---

