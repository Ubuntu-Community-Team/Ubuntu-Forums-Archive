---
title: "Installing 11.04 on SSD reboots to grub command line"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by aTron on 2011-09-15
Hi all, I've been running Ubuntu for a while and install is normally quite painless. However, when I upgraded to a SSD recently I'm having troubles. 

I install the drive as usual and then installed from USB and everything seemed to work fine. The usual re-boot after install and then I ran apt-get update && apt-get upgrade to get the most recent updates. After this I powered down and when I power-up again all I get is the grub command line (grub>). 

I've seen this:
[https://help.ubuntu.com/community/Grub2#A.27.27grub.3E.27.27_Prompt_Booting](https://help.ubuntu.com/community/Grub2#A.27.27grub.3E.27.27_Prompt_Booting)

But I'm not sure if it will help or not. Will I have to do this every time I boot? Is this an indication that something is wrong with the SSD? The install on my other hard disks works just fine with the same version of Ubuntu.

Any help is greatly appreciated.

---

### Post by oldfred on 2011-09-15
Are you able to manually boot then?

Post this from your boot or liveCD:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by aTron on 2011-09-15
Thanks oldfred. The results of the script are below. I now realize as well that I get the additional warning of something like 'unknown file system' and the prompt is 'grub rescue>' rather than 'grub>'.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   114,106,367   114,104,320  83 Linux
/dev/sda2         114,108,414   117,229,567     3,121,154   5 Extended
/dev/sda5         114,108,416   117,229,567     3,121,152  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda5        033b45cf-835c-4689-bb54-694af434f585   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  69 61 6e 2e 6f 72 67 3e  0a 0a 50 61 63 6b 61 67  |ian.org>..Packag|
00000010  65 3a 20 69 6e 64 69 63  61 74 6f 72 2d 61 70 70  |e: indicator-app|
00000020  6c 65 74 2d 61 70 70 6d  65 6e 75 0a 53 74 61 74  |let-appmenu.Stat|
00000030  75 73 3a 20 69 6e 73 74  61 6c 6c 20 6f 6b 20 69  |us: install ok i|
00000040  6e 73 74 61 6c 6c 65 64  0a 50 72 69 6f 72 69 74  |nstalled.Priorit|
00000050  79 3a 20 6f 70 74 69 6f  6e 61 6c 0a 53 65 63 74  |y: optional.Sect|
00000060  69 6f 6e 3a 20 67 6e 6f  6d 65 0a 49 6e 73 74 61  |ion: gnome.Insta|
00000070  6c 6c 65 64 2d 53 69 7a  65 3a 20 31 31 32 0a 4d  |lled-Size: 112.M|
00000080  61 69 6e 74 61 69 6e 65  72 3a 20 55 62 75 6e 74  |aintainer: Ubunt|
00000090  75 20 44 65 73 6b 74 6f  70 20 54 65 61 6d 20 3c  |u Desktop Team <|
000000a0  75 62 75 6e 74 75 2d 64  65 73 6b 74 6f 70 40 6c  |ubuntu-desktop@l|
000000b0  69 73 74 73 2e 75 62 75  6e 74 75 2e 63 6f 6d 3e  |ists.ubuntu.com>|
000000c0  0a 41 72 63 68 69 74 65  63 74 75 72 65 3a 20 69  |.Architecture: i|
000000d0  33 38 36 0a 53 6f 75 72  63 65 3a 20 69 6e 64 69  |386.Source: indi|
000000e0  63 61 74 6f 72 2d 61 70  70 6c 65 74 0a 56 65 72  |cator-applet.Ver|
000000f0  73 69 6f 6e 3a 20 30 2e  34 2e 31 32 2d 30 75 62  |sion: 0.4.12-0ub|
00000100  75 6e 74 75 31 0a 50 72  6f 76 69 64 65 73 3a 20  |untu1.Provides: |
00000110  69 6e 64 69 63 61 74 6f  72 2d 72 65 6e 64 65 72  |indicator-render|
00000120  65 72 0a 44 65 70 65 6e  64 73 3a 20 6c 69 62 61  |er.Depends: liba|
00000130  74 6b 31 2e 30 2d 30 20  28 3e 3d 20 31 2e 31 32  |tk1.0-0 (>= 1.12|
00000140  2e 34 29 2c 20 6c 69 62  63 36 20 28 3e 3d 20 32  |.4), libc6 (>= 2|
00000150  2e 33 2e 36 2d 36 7e 29  2c 20 6c 69 62 67 6c 69  |.3.6-6~), libgli|
00000160  62 32 2e 30 2d 30 20 28  3e 3d 20 32 2e 32 32 2e  |b2.0-0 (>= 2.22.|
00000170  30 29 2c 20 6c 69 62 67  74 6b 32 2e 30 2d 30 20  |0), libgtk2.0-0 |
00000180  28 3e 3d 20 32 2e 31 38  2e 30 29 2c 20 6c 69 62  |(>= 2.18.0), lib|
00000190  69 6e 64 69 63 61 74 6f  72 33 20 28 3e 3d 20 30  |indicator3 (>= 0|
000001a0  2e 33 2e 31 39 29 2c 20  6c 69 62 70 61 6e 65 6c  |.3.19), libpanel|
000001b0  2d 61 70 70 6c 65 74 2d  33 2d 30 2c 20 6c 69 62  |-applet-3-0, lib|
000001c0  78 31 31 2d 36 2c 20 67  6e 6f 6d 65 2d 70 61 6e  |x11-6, gnome-pan|
000001d0  65 6c 0a 52 65 63 6f 6d  6d 65 6e 64 73 3a 20 69  |el.Recommends: i|
000001e0  6e 64 69 63 61 74 6f 72  2d 61 70 70 6d 65 6e 75  |ndicator-appmenu|
000001f0  0a 44 65 73 63 72 69 70  74 69 6f 6e 3a 20 43 6c  |.Description: Cl|
00000200

Unknown BootLoader on sda2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a0 2f 00 00 00  |............/...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by oldfred on 2011-09-15
Script also could not mount sda1, but partition table says it is Linux.

I might try this to see if it works.

#From liveCD so everything is unmounted,swap off if necessary, change sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors:
sudo e2fsck -f -y -v /dev/sda1

---

### Post by aTron on 2011-09-16
There were indeed errors and the second command you suggested fixed these so now it boots to the normal grub prompt and recognizes the ext4 filesystem. Many thanks!!

Below is the new output from the bash script you suggested earlier. I will try toying with some grub commands now to boot into Ubuntu. Is this the right approach? Any suggestions?

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>........C.....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1410840 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   114,106,367   114,104,320  83 Linux
/dev/sda2         114,108,414   117,229,567     3,121,154   5 Extended
/dev/sda5         114,108,416   117,229,567     3,121,152  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2019 MB, 2019557376 bytes
63 heads, 62 sectors/track, 1009 cylinders, total 3944448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     3,941,153     3,941,092   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       761127b5-1006-463b-ba1b-e08c4f4e86f5   ext3       
/dev/sda1        292ab5d3-c172-4036-b7b6-4091c87082b1   ext4       
/dev/sda5        033b45cf-835c-4689-bb54-694af434f585   swap       
/dev/sdb1        E804-F47D                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  36.259239197 = 38.933061632   boot/initrd.img-2.6.38-8-generic               2
  30.166809082 = 32.391364608   boot/vmlinuz-2.6.38-8-generic                  1
  36.259239197 = 38.933061632   initrd.img                                     2
  30.166809082 = 32.391364608   vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  69 61 6e 2e 6f 72 67 3e  0a 0a 50 61 63 6b 61 67  |ian.org>..Packag|
00000010  65 3a 20 69 6e 64 69 63  61 74 6f 72 2d 61 70 70  |e: indicator-app|
00000020  6c 65 74 2d 61 70 70 6d  65 6e 75 0a 53 74 61 74  |let-appmenu.Stat|
00000030  75 73 3a 20 69 6e 73 74  61 6c 6c 20 6f 6b 20 69  |us: install ok i|
00000040  6e 73 74 61 6c 6c 65 64  0a 50 72 69 6f 72 69 74  |nstalled.Priorit|
00000050  79 3a 20 6f 70 74 69 6f  6e 61 6c 0a 53 65 63 74  |y: optional.Sect|
00000060  69 6f 6e 3a 20 67 6e 6f  6d 65 0a 49 6e 73 74 61  |ion: gnome.Insta|
00000070  6c 6c 65 64 2d 53 69 7a  65 3a 20 31 31 32 0a 4d  |lled-Size: 112.M|
00000080  61 69 6e 74 61 69 6e 65  72 3a 20 55 62 75 6e 74  |aintainer: Ubunt|
00000090  75 20 44 65 73 6b 74 6f  70 20 54 65 61 6d 20 3c  |u Desktop Team <|
000000a0  75 62 75 6e 74 75 2d 64  65 73 6b 74 6f 70 40 6c  |ubuntu-desktop@l|
000000b0  69 73 74 73 2e 75 62 75  6e 74 75 2e 63 6f 6d 3e  |ists.ubuntu.com>|
000000c0  0a 41 72 63 68 69 74 65  63 74 75 72 65 3a 20 69  |.Architecture: i|
000000d0  33 38 36 0a 53 6f 75 72  63 65 3a 20 69 6e 64 69  |386.Source: indi|
000000e0  63 61 74 6f 72 2d 61 70  70 6c 65 74 0a 56 65 72  |cator-applet.Ver|
000000f0  73 69 6f 6e 3a 20 30 2e  34 2e 31 32 2d 30 75 62  |sion: 0.4.12-0ub|
00000100  75 6e 74 75 31 0a 50 72  6f 76 69 64 65 73 3a 20  |untu1.Provides: |
00000110  69 6e 64 69 63 61 74 6f  72 2d 72 65 6e 64 65 72  |indicator-render|
00000120  65 72 0a 44 65 70 65 6e  64 73 3a 20 6c 69 62 61  |er.Depends: liba|
00000130  74 6b 31 2e 30 2d 30 20  28 3e 3d 20 31 2e 31 32  |tk1.0-0 (>= 1.12|
00000140  2e 34 29 2c 20 6c 69 62  63 36 20 28 3e 3d 20 32  |.4), libc6 (>= 2|
00000150  2e 33 2e 36 2d 36 7e 29  2c 20 6c 69 62 67 6c 69  |.3.6-6~), libgli|
00000160  62 32 2e 30 2d 30 20 28  3e 3d 20 32 2e 32 32 2e  |b2.0-0 (>= 2.22.|
00000170  30 29 2c 20 6c 69 62 67  74 6b 32 2e 30 2d 30 20  |0), libgtk2.0-0 |
00000180  28 3e 3d 20 32 2e 31 38  2e 30 29 2c 20 6c 69 62  |(>= 2.18.0), lib|
00000190  69 6e 64 69 63 61 74 6f  72 33 20 28 3e 3d 20 30  |indicator3 (>= 0|
000001a0  2e 33 2e 31 39 29 2c 20  6c 69 62 70 61 6e 65 6c  |.3.19), libpanel|
000001b0  2d 61 70 70 6c 65 74 2d  33 2d 30 2c 20 6c 69 62  |-applet-3-0, lib|
000001c0  78 31 31 2d 36 2c 20 67  6e 6f 6d 65 2d 70 61 6e  |x11-6, gnome-pan|
000001d0  65 6c 0a 52 65 63 6f 6d  6d 65 6e 64 73 3a 20 69  |el.Recommends: i|
000001e0  6e 64 69 63 61 74 6f 72  2d 61 70 70 6d 65 6e 75  |ndicator-appmenu|
000001f0  0a 44 65 73 63 72 69 70  74 69 6f 6e 3a 20 43 6c  |.Description: Cl|
00000200

Unknown BootLoader on sda2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a0 2f 00 00 00  |............/...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by oldfred on 2011-09-16
Script does not look any different. Did you posts results.txt not results1.txt or whatever the newest number is? It auto indexes so yo do not overwrite the old copy.

What is the boot issue?If everything else is ok reinstalling grub2's boot loader to the MBR may work.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by aTron on 2011-09-16
I think it's the correct file. The only difference I can see to my untrained eye is that to begin with the filesystem on sda1 was blank and now it recognizes it as ext4. 

I think now the boot issue is that I've never had to deal with GRUB before since Ubuntu installs have always just worked for me so now I need to learn how to boot. When I turn on my computer all I see is the grub command line and I'm not really sure what to do here. I'll try a few things from the link I posted in my first post tonight or tomorrow and see what I can figure out.

---

### Post by oldfred on 2011-09-16
While you have grub in the MBR and it is trying to boot from sda1, the sript is not showing anything in sda1. It normally  would show all the files required to boot. Did sda1 get reformated? It may just be quicker to reinstall to sda1 using manual install to choose sda1 as / (root).

---

### Post by aTron on 2011-09-19
I spent the weekend trying to get this thing to boot and I'm getting the feeling that there is something wrong with the drive I bought. Several distributions all failed to install with the same symptom that the install seemed to work until reboot and then I arrive at grub rescue prompt. I even tried installing a copy of windows7 that gave me an error prompt saying that windows could not install on this hardware. Thanks for all your help.

---

