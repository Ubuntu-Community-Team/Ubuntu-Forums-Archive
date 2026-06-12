---
title: "Partioning and installing at lenovo s10-3s - won't boot without the USB stick!"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by garfieldpbj on 2011-05-06
Hi

I have got a Lenovo s10-3s onto which I want to install ubuntu 11.04, and still keep the original system.

The netbook has one hard drive with the following partitioning as standard:

200 mb primary (prob. win 7 recovery)
180 gb primary (win 7)
25 gb primary (storage)
15 gb primary (recovery, lenovo)

all are ntfs..

(the size of the windows+storage partition, might actually be something different, because I changed the sizes, and do not remember the original values..)

I want to keep the win7 and the two recovery partitions..

Because I only have a 512 MB USB stick I use the minimal installation, but I do not think this should be the problem..

Because maximum 4 primary partitions are allowed I made the following:

200 mb primary (prob. win 7 recovery)
50 gb primary (win 7, resized)
15 gb primary (recovery, lenovo)
50 gb logical (ubuntu, ext4)
4 gb logical (swap)
130 gb logical (storage, ntfs)

After that I installed ubuntu, with no errors. 

However I am not able to boot it directly - the strange thing is however, if I plug in the USB stick, and boots from that, I get the correct boot menu and can choose between ubuntu, memtest, win7 and win7 rec, and boot all of them..

However I do not want to boot from the usb stick every time..

How do I fix it?

I have tried to "rebuild" the grub2 menu with no luck.. (for example following [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708))

I hope someone can guide me... I am very frustrated! 

/Peter

Ps. Have anyone found the "real solution" to the wireless problem in 11.04?

---

### Post by lechien73 on 2011-05-06
It sounds like Grub has got installed to the MBR of your USB stick, rather than the hard disk.

To confirm this, please download and run the Boot Info Script ([http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)). Follow the instructions at the link to run it, and then please create a new response here, click the **#** button on the toolbar, and then paste the contents of RESULTS.txt file between the [CODE] tags.

If that's what's happened, then it should be relatively straightforward to install Grub to the MBR of your hard drive.

---

### Post by garfieldpbj on 2011-05-06
For me it look like I installed the boot loader at both the stick and the hard drive (actually, the ubuntu installer installed it at the stick..)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for a6d.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for cbdc2.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda4 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30943599 sectors.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 Gb, 250059350016 byte
255 hoveder, 63 sektorer/spor, 30401 cylindre, i alt 488397168 sektorer
Enheder = sektorer af 1 * 512 = 512 byte
Sektorstørrelse (logisk/fysisk): 512 byte / 512 byte

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       411,647       409,600   7 HPFS/NTFS
/dev/sda2             411,648    98,067,897    97,656,250   7 HPFS/NTFS
/dev/sda3          98,068,478   457,453,567   359,385,090   5 Extended
/dev/sda5    *    359,796,736   457,453,567    97,656,832  83 Linux
/dev/sda6         351,983,616   359,796,735     7,813,120  82 Linux swap / Solaris
/dev/sda7          98,068,480   351,981,567   253,913,088  83 Linux
/dev/sda4         457,453,568   488,397,167    30,943,600  12 Compaq diagnostics


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 512 Mb, 512753664 byte
16 hoveder, 62 sektorer/spor, 1009 cylindre, i alt 1001472 sektorer
Enheder = sektorer af 1 * 512 = 512 byte
Sektorstørrelse (logisk/fysisk): 512 byte / 512 byte

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             62     1,000,927     1,000,866   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3AAC369BAC36519D                       ntfs                                     
/dev/sda2        1AF43516F434F61B                       ntfs       Windows                       
/dev/sda3: PTTYPE="dos" 
/dev/sda4        B2A23BBFA23B86BF                       ntfs       LENOVO_PART                   
/dev/sda5        27b226d3-dd2e-4936-9f96-09dcd07a0588   ext4                                     
/dev/sda6        906c262d-eeac-481b-b1c1-ed75fd931e2c   swap                                     
/dev/sda7        10fc86c2-6333-4d0c-9405-4c6e38618819   ext4       Lager                         
/dev/sda: PTTYPE="dos" 
/dev/sdc1        8908-85ED                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /media/Lager             ext4       (rw,commit=0)
/dev/sdc1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 27b226d3-dd2e-4936-9f96-09dcd07a0588
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 27b226d3-dd2e-4936-9f96-09dcd07a0588
set locale_dir=($root)/boot/grub/locale
set lang=da_DK
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, med Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 27b226d3-dd2e-4936-9f96-09dcd07a0588
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=27b226d3-dd2e-4936-9f96-09dcd07a0588 ro   splash quiet vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, med Linux 2.6.38-8-generic (genoprettelsestilstand)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 27b226d3-dd2e-4936-9f96-09dcd07a0588
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=27b226d3-dd2e-4936-9f96-09dcd07a0588 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 27b226d3-dd2e-4936-9f96-09dcd07a0588
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 27b226d3-dd2e-4936-9f96-09dcd07a0588
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 3AAC369BAC36519D
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root B2A23BBFA23B86BF
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc5       /               ext4    errors=remount-ro 0       1
# /media/Lager was on /dev/sdc7 during installation
UUID=10fc86c2-6333-4d0c-9405-4c6e38618819 /media/Lager    ext4    defaults        0       2
# swap was on /dev/sdc6 during installation
UUID=906c262d-eeac-481b-b1c1-ed75fd931e2c none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 188.6GB: boot/grub/core.img
 214.8GB: boot/grub/grub.cfg
 186.1GB: boot/initrd.img-2.6.38-8-generic
 184.4GB: boot/vmlinuz-2.6.38-8-generic
 186.1GB: initrd.img
 184.4GB: vmlinuz

=================== sdc1: Location of files loaded by Grub: ===================


    ??GB: initrd.gz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 10 10 00  |.X.SYSLINUX.....|
00000010  02 00 02 00 00 f8 00 01  3e 00 10 00 00 00 00 00  |........>.......|
00000020  a2 45 0f 00 00 00 29 ed  85 08 89 20 20 20 20 20  |.E....)....     |
00000030  20 20 20 20 20 20 46 41  54 31 36 20 20 20 0e 1f  |      FAT16   ..|
00000040  be 5b 7c ac 22 c0 74 0b  56 b4 0e bb 07 00 cd 10  |.[|.".t.V.......|
00000050  5e eb f0 32 e4 cd 16 cd  19 eb fa fc 31 c9 8e d1  |^..2........1...|
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
00000110  c6 06 45 7d 00 66 b8 30  02 00 00 66 ba 00 00 00  |..E}.f.0...f....|
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


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by garfieldpbj on 2011-05-06
As can be seen from the result file, I did actually not format the sda7 (my storage, to be seen in both win and ubuntu) to ntfs yet..

...again I do not think this is the source of the error..

---

### Post by lechien73 on 2011-05-06
Well, you definitely have Natty's version of grub installed in the MBR of /dev/sda, because the current version of boot info script doesn't parse it properly yet.

For clarity, would you mind getting the development version and trying that instead?

```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh; hb=HEAD'
```

---

### Post by garfieldpbj on 2011-05-06
Here's the dev. output:```
                Boot Info Script 0.56    from 8 February 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/media/sda5/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    -----
    search.fs_uuid 27b226d3-dd2e-4936-9f96-09dcd07a0588 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda4 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30943599 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........:...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 560 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the directory. 
                       According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 Gb, 250059350016 byte
255 hoveder, 63 sektorer/spor, 30401 cylindre, i alt 488397168 sektorer
Enheder = sektorer af 1 * 512 = 512 byte
Sektorstørrelse (logisk/fysisk): 512 byte / 512 byte

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       411,647       409,600   7 NTFS / exFAT / HPFS
/dev/sda2             411,648    98,067,897    97,656,250   7 NTFS / exFAT / HPFS
/dev/sda3          98,068,478   457,453,567   359,385,090   5 Extended
/dev/sda5    *    359,796,736   457,453,567    97,656,832  83 Linux
/dev/sda6         351,983,616   359,796,735     7,813,120  82 Linux swap / Solaris
/dev/sda7          98,068,480   351,981,567   253,913,088  83 Linux
/dev/sda4         457,453,568   488,397,167    30,943,600  12 Compaq diagnostics


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 512 Mb, 512753664 byte
16 hoveder, 62 sektorer/spor, 1009 cylindre, i alt 1001472 sektorer
Enheder = sektorer af 1 * 512 = 512 byte
Sektorstørrelse (logisk/fysisk): 512 byte / 512 byte

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             62     1,000,927     1,000,866   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3AAC369BAC36519D                       ntfs       
/dev/sda2        1AF43516F434F61B                       ntfs       Windows
/dev/sda4        B2A23BBFA23B86BF                       ntfs       LENOVO_PART
/dev/sda5        27b226d3-dd2e-4936-9f96-09dcd07a0588   ext4       
/dev/sda6        906c262d-eeac-481b-b1c1-ed75fd931e2c   swap       
/dev/sda7        10fc86c2-6333-4d0c-9405-4c6e38618819   ext4       Lager
/dev/sdc1        8908-85ED                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /media/Windows           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /media/Lager             ext4       (rw,commit=0)
/dev/sdc1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 27b226d3-dd2e-4936-9f96-09dcd07a0588
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 27b226d3-dd2e-4936-9f96-09dcd07a0588
set locale_dir=($root)/boot/grub/locale
set lang=da_DK
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, med Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 27b226d3-dd2e-4936-9f96-09dcd07a0588
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=27b226d3-dd2e-4936-9f96-09dcd07a0588 ro   splash quiet vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, med Linux 2.6.38-8-generic (genoprettelsestilstand)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 27b226d3-dd2e-4936-9f96-09dcd07a0588
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=27b226d3-dd2e-4936-9f96-09dcd07a0588 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 27b226d3-dd2e-4936-9f96-09dcd07a0588
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 27b226d3-dd2e-4936-9f96-09dcd07a0588
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 3AAC369BAC36519D
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root B2A23BBFA23B86BF
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc5       /               ext4    errors=remount-ro 0       1
# /media/Lager was on /dev/sdc7 during installation
UUID=10fc86c2-6333-4d0c-9405-4c6e38618819 /media/Lager    ext4    defaults        0       2
# swap was on /dev/sdc6 during installation
UUID=906c262d-eeac-481b-b1c1-ed75fd931e2c none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 175.690044403 = 188.645748736  boot/grub/core.img                             1
 200.108753204 = 214.865137664  boot/grub/grub.cfg                             1
 173.326385498 = 186.107789312  boot/initrd.img-2.6.38-8-generic               2
 171.779602051 = 184.446943232  boot/vmlinuz-2.6.38-8-generic                  1
 173.326385498 = 186.107789312  initrd.img                                     2
 171.779602051 = 184.446943232  vmlinuz                                        1

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             initrd.gz                                      2

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             vesamenu.c32                                   1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 vesamenu.c32                       :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```

---

### Post by lechien73 on 2011-05-06
The only thing I can see from your RESULTS.txt output is that, according to the /etc/fstab file on /dev/sda5:

```
/dev/sdc5       /               ext4    errors=remount-ro 0       1
```

Which would indicate it's trying to mount /dev/sdc5 as your root folder, rather than /dev/sda5.

---

### Post by garfieldpbj on 2011-05-06
> **lechien73 said:**
> 
Which would indicate it's trying to mount /dev/sdc5 as your root folder, rather than /dev/sda5.

Have you got any idea how to fix this?

---

### Post by lechien73 on 2011-05-06
Since when you boot with the USB drive, it is correctly mounting /dev/sda5 as root. I would try:

```
sudo nano /etc/fstab
```

Find the line that reads:

```
/dev/sdc5       /               ext4    errors=remount-ro 0       1
```

And change it so that it reads:

```
UUID=27b226d3-dd2e-4936-9f96-09dcd07a0588   /               ext4    errors=remount-ro 0       1
```

Press CTRL-X to close nano and press Y to save the changes. Then try rebooting.

---

### Post by garfieldpbj on 2011-05-06
> **lechien73 said:**
> Since when you boot with the USB drive, it is correctly mounting /dev/sda5 as root. I would try:

```
sudo nano /etc/fstab
```

Find the line that reads:

```
/dev/sdc5       /               ext4    errors=remount-ro 0       1
```

And change it so that it reads:

```
UUID=27b226d3-dd2e-4936-9f96-09dcd07a0588   /               ext4    errors=remount-ro 0       1
```

Press CTRL-X to close nano and press Y to save the changes. Then try rebooting.

I'll try that later, and tell you the result - I have to cook some food now :-) 

Thank you for all your help untill now..

---

### Post by lechien73 on 2011-05-06
You're welcome...I'm just about to do the same thing :)

---

### Post by garfieldpbj on 2011-05-06
> **lechien73 said:**
> Since when you boot with the USB drive, it is correctly mounting /dev/sda5 as root. I would try:

```
sudo nano /etc/fstab
```

Find the line that reads:

```
/dev/sdc5       /               ext4    errors=remount-ro 0       1
```

And change it so that it reads:

```
UUID=27b226d3-dd2e-4936-9f96-09dcd07a0588   /               ext4    errors=remount-ro 0       1
```

Press CTRL-X to close nano and press Y to save the changes. Then try rebooting.

I have the same error when booting without the USB stick. (Error: file not found; grub rescue>)

Any suggestions what else to try?

---

### Post by garfieldpbj on 2011-05-07
I found a (simple!) solution, to write the MBR at the local disc:

```
sudo grub-install --root-directory=/ /dev/sda
```

Thank you for the other suggestions.

For the wireless problem  I found a forum post:
[http://ubuntuforums.org/showthread.php?t=1744402](http://ubuntuforums.org/showthread.php?t=1744402)

/Peter

---

