---
title: "mostly clean install grub issues"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by kaligus on 2011-06-14
I have until last night been running Kubuntu 10.04 64 without issue of any major variety.

I deleted /bin /var /etc /usr /lib?? etc. leaving only /root and /home intact (/home is another drive) and installed Kubuntu 11.04 from the alternative distro CD.

I can not get past grub which always drops me at the "grub rescue" prompt. I tried manually setting root and prefix with still no ability to continue booting.

When I "ls (hd#,1)/" with # = 0 .. 5 from the grub prompt my / drive does not show up and /compile shows up twice as hd1,1 and hd2,1.

I then tied boot-repair on the Kubuntu secured remix CD (where I am running currently), same result.

Lastly I tried installing from the secured remix CD with again the same "grub rescue" prompt being all I get on boot.

 I can mount all drives and access at will from a live CD of several varieties but can not seem to get the boot process to locate my / drive or most importantly "/boot/grub"

---

### Post by Quackers on 2011-06-14
Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by garvinrick4 on 2011-06-14
Hello Quackers first time I have noticed the boot_script is a .zip file I have been spending
my time studying network cards and their drivers as of late. Glad I read the post before
sending out wrong info to download and execute the script. Have a nice day Quackers.
Here is nice wireless script if you do not have already:
[http://sourceforge.net/projects/wirelessscript/files/](http://sourceforge.net/projects/wirelessscript/files/)

---

### Post by kaligus on 2011-06-14
thanks for the reply!

/dev/sdc1 is / and is the only drive selected to boot from in BIOS and the only drive with boot flag set.

/dev/sda1 has an MBR because one of the things I tried last night was just saying yes to "install grub on first drive" followed by telling BIOS to boot that drive.  ALL OTHER MBR are from past lives and have not given any grief to this point and /dev/sdc1 has been / since it came home for version 9.10

/dev/sda1 is on the motherboard IDE/PATA /dev/sdd1 and /dev/sde1 are on an addon IDE/PATA card, everything else is SATA on motherboard

not sure what else may be helpful to know.

(edited after I noticed lzma complaints... still trying to solve new complaints but more info is now present)

```
 
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 50ac4bca-a3d2-445a-a6cd-3a06483565c4 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdd and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sde.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdf and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdc1 
                       and looks at sector 625231016 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdf1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   156,296,384   156,296,322  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   613,088,594   613,088,532  83 Linux
/dev/sdb2         613,088,656   625,137,344    12,048,689   5 Extended
/dev/sdb5         613,088,658   625,137,344    12,048,687  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   976,771,071   976,769,024  83 Linux


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders, total 20005650 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63    20,000,924    20,000,862  83 Linux


Drive: sde _____________________________________________________________________

Disk /dev/sde: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders, total 20005650 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1                  63    20,000,924    20,000,862  83 Linux


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  63   488,392,064   488,392,002  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1fdcbeb3-9ff4-4bdd-8f13-b0add00e3e40   ext3       home
/dev/sdb1        ef9f2c74-2ae2-48bf-95ad-62a2faf8f89f   ext3       junk
/dev/sdb5        6cb1821d-b889-4466-a402-ce02cb2cb3c5   swap       
/dev/sdc1        50ac4bca-a3d2-445a-a6cd-3a06483565c4   ext4       root
/dev/sdd1        9f16182b-3ce2-4d2f-84f3-f672da9c9c6e   ext4       downloads
/dev/sde1        4b0ea33d-dacd-4cd9-a3a1-b83a6b549355   ext4       compile
/dev/sdf1        32ea28c2-f048-4b0a-976a-3021b1fbd55f   ext3       storage

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /mnt/temp                ext4       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root 50ac4bca-a3d2-445a-a6cd-3a06483565c4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root 50ac4bca-a3d2-445a-a6cd-3a06483565c4
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 0,71,115; then
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 50ac4bca-a3d2-445a-a6cd-3a06483565c4
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=50ac4bca-a3d2-445a-a6cd-3a06483565c4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 50ac4bca-a3d2-445a-a6cd-3a06483565c4
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=50ac4bca-a3d2-445a-a6cd-3a06483565c4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 50ac4bca-a3d2-445a-a6cd-3a06483565c4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 50ac4bca-a3d2-445a-a6cd-3a06483565c4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=50ac4bca-a3d2-445a-a6cd-3a06483565c4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=1fdcbeb3-9ff4-4bdd-8f13-b0add00e3e40 /home           ext3    defaults        0       2
# /compile was on /dev/sde1 during installation
UUID=4b0ea33d-dacd-4cd9-a3a1-b83a6b549355 /compile        ext4    defaults        0       2
# /downloads was on /dev/sdd1 during installation
UUID=9f16182b-3ce2-4d2f-84f3-f672da9c9c6e /downloads      ext4    defaults        0       2
# /junk was on /dev/sdb1 during installation
UUID=ef9f2c74-2ae2-48bf-95ad-62a2faf8f89f /junk           ext3    defaults        0       2
# /storage was on /dev/sdf1 during installation
UUID=32ea28c2-f048-4b0a-976a-3021b1fbd55f /storage        ext3    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=6cb1821d-b889-4466-a402-ce02cb2cb3c5 none            swap    sw              0       0

##WAB

##unuused
## /dev/fd0    /media/floppy0      auto    rw,user,noauto,exec,utf8    0       0

## overridden for what ever reason
/dev/scd0       /media/cdrom0       udf,iso9660    user,noauto,exec,utf8    0       0
/dev/scd1       /media/cdrom1       udf,iso9660    user,noauto,exec,utf8    0       0

## partitioned USB devices
/dev/sdg1    /media/usb00_sdg    vfat    user,auto,uid=1000,gid=1000    0    0
/dev/sdh1    /media/usb01_sdh    vfat    user,auto,uid=1000,gid=1000    0    0
/dev/sdi1    /media/usb02_sdi    vfat    user,auto,uid=1000,gid=1000    0    0
/dev/sdj1    /media/usb03_sdj    vfat    user,auto,uid=1000,gid=1000    0    0
/dev/sdk1    /media/usb04_sdk    vfat    user,auto,uid=1000,gid=1000    0    0
/dev/sdl1    /media/usb05_sdl    vfat    user,auto,uid=1000,gid=1000    0    0
/dev/sdm1    /media/usb06_sdm    vfat    user,auto,uid=1000,gid=1000    0    0
/dev/sdn1    /media/usb07_sdn    vfat    user,auto,uid=1000,gid=1000    0    0
/dev/sdo1    /media/usb08_sdo    vfat    user,auto,uid=1000,gid=1000    0    0

##unpartitioned USB devices
/dev/sdk    /media/usb09_sdk    vfat    user,auto,uid=1000,gid=1000    0    0
/dev/sdl    /media/usb10_sdl    vfat    user,auto,uid=1000,gid=1000    0    0

## network mounts
//192.168.1.53/www               /media/www        cifs  auto,user,username=will,password=SINKY,uid=1000,gid=1000  0  0
//192.168.1.42/littlewill-home   /media/littlewill cifs  auto,user,username=will,password=SINKY,uid=1000,gid=1000  0  0

##/WAB

--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 298.132682800 = 320.117530624  boot/grub/core.img                             1
 298.155292511 = 320.141807616  boot/grub/grub.cfg                             1
 298.922851562 = 320.965967872  boot/initrd.img-2.6.38-8-generic               2
 294.263004303 = 315.962494976  boot/vmlinuz-2.6.38-8-generic                  1
 298.922851562 = 320.965967872  initrd.img                                     2
 294.263004303 = 315.962494976  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  7c fe 32 6f 3f e8 da f7  40 27 73 82 78 3a e6 32  ||.2o?...@'s.x:.2|
00000010  e7 00 e7 73 6f 92 b1 e0  d3 21 a5 af f6 cc cd 75  |...so....!.....u|
00000020  f4 d3 1c 93 60 ee db 37  01 9d a7 42 54 58 9c 19  |....`..7...BTX..|
00000030  0b 01 23 17 d7 74 31 ce  35 f2 94 07 c5 f4 78 45  |..#..t1.5.....xE|
00000040  7f 20 cb 3d 8f a4 ce f0  66 2e 5f d8 68 9d 6c 2c  |. .=....f._.h.l,|
00000050  7b 03 8d 1f 33 b8 c0 0e  11 da 3f ee 5f d1 47 9a  |{...3.....?._.G.|
00000060  f1 dd fb d2 28 a3 75 a6  3b 00 7c f1 1b f0 5d f1  |....(.u.;.|...].|
00000070  42 b4 4d 6c 12 76 0d bf  7d 80 0f 72 5f 27 a7 d4  |B.Ml.v..}..r_'..|
00000080  4e bc 98 dd a6 af 1b 2d  51 c1 5e f5 26 d6 ce d7  |N......-Q.^.&...|
00000090  1a a9 d7 e0 9a 8a 0e 34  bb 6a 6c 2c 0d 76 f1 f3  |.......4.jl,.v..|
000000a0  5d 01 0a bb 46 75 80 f6  0d 09 fa 33 05 b0 9c 36  |]...Fu.....3...6|
000000b0  9d 49 8b b9 fd 60 f0 04  8f f5 e9 ba 6a 8a c7 5e  |.I...`......j..^|
000000c0  bc 77 fc 4b 3f a7 38 4a  b9 ea 52 c5 e7 9f 5c 57  |.w.K?.8J..R...\W|
000000d0  cf 6e 51 ba 6d c8 e7 5c  4a c0 27 3a 17 be f0 42  |.nQ.m..\J.':...B|
000000e0  f4 5e 56 0b 7d 27 cd 3f  e4 34 43 1d 2e 96 f4 e1  |.^V.}'.?.4C.....|
000000f0  7c ad 65 7d bb 9a cb ff  6e 4e b8 1d 5d 78 75 6d  ||.e}....nN..]xum|
00000100  66 12 f7 7a 3d 31 53 e5  79 22 22 22 72 1d 31 64  |f..z=1S.y"""r.1d|
00000110  bc e4 8f 06 f5 cc da 46  aa bb f5 18 91 18 1d 35  |.......F.......5|
00000120  b5 b7 f9 c8 d3 b1 f3 79  18 4c bb ed be 0e 4a 59  |.......y.L....JY|
00000130  60 44 c5 36 64 bb 4f 53  04 ba 38 5c 61 bb 56 17  |`D.6d.OS..8\a.V.|
00000140  56 42 eb ac 4a 67 c0 00  6d a6 54 9e da 0e de c0  |VB..Jg..m.T.....|
00000150  da db 10 64 19 19 4b 1b  3d 9b 9f 61 02 95 a2 ef  |...d..K.=..a....|
00000160  6a 75 9c cb 12 1f 0c 1a  34 f0 0c 25 8c 57 33 66  |ju......4..%.W3f|
00000170  f6 f0 ab 8c 30 48 b3 82  31 c7 dd 2e 86 da 7b a7  |....0H..1.....{.|
00000180  dc 27 a6 8f d7 77 ed 96  2e b0 f6 d6 b4 0e 0b ff  |.'...w..........|
00000190  94 5d c7 ec c4 06 1e 0b  50 1a 28 1f 54 10 6c b0  |.]......P.(.T.l.|
000001a0  32 ba 7b d2 63 de 32 3b  0b 0b 26 94 cf 3e 9a 80  |2.{.c.2;..&..>..|
000001b0  27 6d a3 82 fe 31 ea 5b  cb e9 ee bf bc a4 00 fe  |'m...1.[........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 2f d9 b7 00 00 00  |........../.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdg sdh sdi sdj 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error



```

---

### Post by kaligus on 2011-06-14
I am going to assume that the problem is here:

>  => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of      the same hard drive for core.img. core.img is at this location and looks      for (,msdos1)/boot/grub on this drive.

However after that I am at a loss how to make the core.img look for (root)/boot/grub

I also can not explain how it goes from working to looking on (,msdos1)/boot/grub

---

### Post by Quackers on 2011-06-14
Yes garvinrick4 the new boot script is slightly different now :-)
Thanks for the wireless script :-)
You have a nice day too!

kaligus,
which hard drive is set to boot first in your bios?

---

### Post by kaligus on 2011-06-15
Currently /dev/sdc1 but /dev/sda1 gave the same results last night.

I have not tried /dev/sda1 today after using boot-repair and was actually just going to do so since it appears to have correct information.

Thanks again Quackers.

---

### Post by oldfred on 2011-06-15
I do not see anything wrong. I assume you have tried booting from both sda & sdc, both grub2 boot loaders look correctly configured.

Have you tried manually booting from rescue prompt? Note that the drive number 2 is if you are booting from sda. If booting from sdc it may be hd0 as grub2 always sees the boot drive as hd0.

set prefix=(hd2,1)/boot/grub
set root=(hd2,1)
insmod (hd2,1)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sdc1 ro
initrd /initrd.img
boot


Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

### Post by kaligus on 2011-06-15
> **oldfred said:**
> I do not see anything wrong. I assume you have tried booting from both sda & sdc, both grub2 boot loaders look correctly configured.

Have you tried manually booting from rescue prompt? Note that the drive number 2 is if you are booting from sda. If booting from sdc it may be hd0 as grub2 always sees the boot drive as hd0.

set prefix=(hd2,1)/boot/grub
set root=(hd2,1)
insmod (hd2,1)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sdc1 ro
initrd /initrd.img
boot




at the grub rescue prompt typing 
> 
ls (hd{0-5},1)/

NEVER shows my / drive thus I can not load any modules including boot.

I just tried setting /dev/sda1 as boot in BIOS again and it still (as last night) drops me at a grub rescue prompt where I do not have a / drive.  I strongly suspect that my BIOS may be ignoring the IDE drive as soon as I plug in SATA drives for booting.  If I put one of the other SATA drives below the IDE drive I get an expected "no OS found" type error which tells me I can not boot from the onboard IDE port if I have SATA drives installed (feels like a bug to me).

BOTH hd1,1 and hd2,1 are identical and the contents shown by ls of either are what should be (hd1,1)

The second entry in the boot script results

> 
sdc1: __________________________________________________________________________      File system:       ext4     Boot sector type:  Grub2 (v1.99)     Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdc1                         and looks at sector 625231016 of the same hard drive                         for core.img, but core.img can not be found at this                         location.     Operating System:  Ubuntu 11.04     Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
Does not seem to be correct even though the first entry seems correct (though I still think (,msdos1) looks funny, my experience with grub2 is limited to it working correctly and my not messing about with it until last night)

---

### Post by oldfred on 2011-06-15
You do not boot from a partition like your sdc1 (normally), so the grub2 boot loader installed there does not matter. It is not used for anything. Only a grub2 boot loader in the MBR should be configured to boot and both of yours (sda & sdc's MBRs) look ok.

We have seen issues before with mixed IDE & SATA drives. Often related to a BIOS not set correctly or just not a well designed BIOS. Have you updated BIOS to most current version? What settings do you have for drives. Often settings like IDE & large are required, but names vary somewhat by brand for those settings.

---

### Post by kaligus on 2011-06-15
> **oldfred said:**
> You do not boot from a partition like your sdc1 (normally), so the grub2 boot loader installed there does not matter. It is not used for anything. Only a grub2 boot loader in the MBR should be configured to boot and both of yours (sda & sdc's MBRs) look ok.

We have seen issues before with mixed IDE & SATA drives. Often related to a BIOS not set correctly or just not a well designed BIOS. Have you updated BIOS to most current version? What settings do you have for drives. Often settings like IDE & large are required, but names vary somewhat by brand for those settings.

The BIOS is the latest as far as I know, I am making sure that has not changed.

I will also check my BIOS settings... we had a very near lighting strike last night which does not seem to have affected anything but I suppose it could have mangled CMOS just enough... Hair stood up and the physical force of the bang was reverberating for quite some time.

Was there a major change between 10.04 and 11.04 which would cause mixed IDE/SATA issues because yesterday morning it booted quite well into 10.04 from the / (sdc1) drive and no drives moved etc.

---

### Post by oldfred on 2011-06-15
There were a lot of changes to grub2 with version 1.99, but I do not know of any changes on IDE or SATA identification. It has been an issue for quite a while. Some BIOS would not consistently load the same drive as sda, so grub did not know which was which. Part of the reason for using UUIDs not device names.

Grub 1.99 Submenus - drs305
[http://ubuntuforums.org/showthread.php?t=1739336](http://ubuntuforums.org/showthread.php?t=1739336)

---

### Post by kaligus on 2011-06-16
Well I give up for now :)  There is a new BIOS update which is turning out more challenging than Kubuntu to install properly (what you mean the world does not run Windows?).  I made a live cd which preselects "boot from first hard drive" which seems to work just fine.  I will fiddle more after I get everything installed etc.  Thank you all for your ideas!

---

### Post by oldfred on 2011-06-16
If you can boot into your system, you can reinstall grub to the MBR from there. If Ubuntu is in sdc, I would install there not sdb as shown in example below. Then change BIOS to boot sdc.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by kaligus on 2011-06-22
The solution to my problem is to disallow booting from my second DVD drive.

Anytime I set a boot priority for the drive grub "ls (hd1,1)/" becomes identical to "ls (hd2,1)/" regardless of where in the chain the offending drive sits or what drive is set to boot in BIOS.

If I remove the offending drive from the boot chain I can boot from any drive on any port (2 onboard PATA, 6 onboard SATA, 2 above-board PATA).  The offending drive is a PATA drive originally pulled from an external USB box.

the drive:
```

              *-cdrom
                   description: DVD writer
                   product: MD-16XDVD9A4
                   vendor: MAD DOG

```and just in case it is the add on PATA/RAID card is causing the confusion:
```

           *-storage
                description: RAID bus controller
                product: PCI0680 Ultra ATA-133 Host Controller
                vendor: Silicon Image, Inc.

```
no raid set up or enabled, and I have long ago lost the manual so it is possible that disabling boot from the PATA/RAID card would also solve the problem.

---

