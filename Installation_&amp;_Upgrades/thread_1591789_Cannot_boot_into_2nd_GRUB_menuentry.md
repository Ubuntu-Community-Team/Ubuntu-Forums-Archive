---
title: "Cannot boot into 2nd GRUB menuentry"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by JohnMac on 2010-10-09
I tried to use Startup-Manager to rearrange my GRUB menuentries and now my new Meerkat install is not booting. I initially tried update-grub and then I reinstalled GRUB but now obviously that menuentry is gone because I no longer get an option.

My system:

Desktop PC with AMD5200 64 bit CPU
2 Gb ram
160 Gb Samsung HDD
Partition SDA1 - Ubuntu 10.04 32bit
Partition SDA8 - Ubuntu 10.10 rc

Can anyone help, my Boot info:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   166,637,785   166,635,738  83 Linux
/dev/sda2         166,639,614   312,580,095   145,940,482   5 Extended
/dev/sda5         300,886,016   312,580,095    11,694,080  82 Linux swap / Solaris
/dev/sda6         166,639,616   169,097,215     2,457,600  83 Linux
/dev/sda7         295,321,600   300,881,919     5,560,320  82 Linux swap / Solaris
/dev/sda8         169,099,264   295,305,215   126,205,952  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 130 MB, 130940928 bytes
16 heads, 32 sectors/track, 499 cylinders, total 255744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32       255,486       255,455   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 30.0 GB, 30005821440 bytes
255 heads, 62 sectors/track, 3706 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63       160,649       160,587   0 Empty
/dev/sdc2             160,650    58,605,118    58,444,469   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        69710a30-d716-4bb4-b1f8-b77a943e4f05   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        77b21f6c-b0e0-4c99-8d75-0dbbc375e231   swap                                     
/dev/sda6        c5717e00-fde4-499d-baf1-69c5708bfbb4   ext4                                     
/dev/sda7        bc7ac98f-7983-47c4-b0bd-b44606a6b527   swap                                     
/dev/sda8        cba4e5c1-a923-434d-acb6-5bbade7b5faf   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5447-4D31                              vfat       REMOVABLE                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc         A88B-3652                              vfat       iPod                          
/dev/sdc2        E5AB-6A34                              vfat       IPOD                          
error: /dev/sdc1: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc2        /media/IPOD              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb1        /media/REMOVABLE         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 69710a30-d716-4bb4-b1f8-b77a943e4f05
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 69710a30-d716-4bb4-b1f8-b77a943e4f05
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 69710a30-d716-4bb4-b1f8-b77a943e4f05
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=69710a30-d716-4bb4-b1f8-b77a943e4f05 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 69710a30-d716-4bb4-b1f8-b77a943e4f05
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=69710a30-d716-4bb4-b1f8-b77a943e4f05 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 69710a30-d716-4bb4-b1f8-b77a943e4f05
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=69710a30-d716-4bb4-b1f8-b77a943e4f05 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 69710a30-d716-4bb4-b1f8-b77a943e4f05
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=69710a30-d716-4bb4-b1f8-b77a943e4f05 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 69710a30-d716-4bb4-b1f8-b77a943e4f05
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=69710a30-d716-4bb4-b1f8-b77a943e4f05 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 69710a30-d716-4bb4-b1f8-b77a943e4f05
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=69710a30-d716-4bb4-b1f8-b77a943e4f05 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 69710a30-d716-4bb4-b1f8-b77a943e4f05
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=69710a30-d716-4bb4-b1f8-b77a943e4f05 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 69710a30-d716-4bb4-b1f8-b77a943e4f05
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=69710a30-d716-4bb4-b1f8-b77a943e4f05 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 69710a30-d716-4bb4-b1f8-b77a943e4f05
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=69710a30-d716-4bb4-b1f8-b77a943e4f05 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 69710a30-d716-4bb4-b1f8-b77a943e4f05
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=69710a30-d716-4bb4-b1f8-b77a943e4f05 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 69710a30-d716-4bb4-b1f8-b77a943e4f05
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 69710a30-d716-4bb4-b1f8-b77a943e4f05
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=77b21f6c-b0e0-4c99-8d75-0dbbc375e231 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  47.3GB: boot/grub/core.img
  47.7GB: boot/grub/grub.cfg
  47.4GB: boot/initrd.img-2.6.32-21-generic
  47.6GB: boot/initrd.img-2.6.32-22-generic
  47.6GB: boot/initrd.img-2.6.32-23-generic
   9.3GB: boot/initrd.img-2.6.32-24-generic
  13.6GB: boot/initrd.img-2.6.32-25-generic
  47.3GB: boot/vmlinuz-2.6.32-21-generic
  47.5GB: boot/vmlinuz-2.6.32-22-generic
  47.5GB: boot/vmlinuz-2.6.32-23-generic
  47.8GB: boot/vmlinuz-2.6.32-24-generic
  47.9GB: boot/vmlinuz-2.6.32-25-generic
  13.6GB: initrd.img
   9.3GB: initrd.img.old
  47.9GB: vmlinuz
  47.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 20 00 02  |.X.MSDOS5.0.. ..|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  3f 3e 7e 03 00 00 00 00  00 00 00 00 00 00 00 00  |?>~.............|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  01 00 29 52 36 8b a8 69  50 6f 64 00 4d 45 20 20  |..)R6..iPod.ME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 08  |{......|.N..V@..|
00000070  cd 13 73 05 b9 ff ff 8a  f1 66 0f b6 c6 40 66 0f  |..s......f...@f.|
00000080  b6 d1 80 e2 3f f7 e2 86  cd c0 ed 06 41 66 0f b7  |....?.......Af..|
00000090  c9 66 f7 e1 66 89 46 f8  83 7e 16 00 75 38 83 7e  |.f..f.F..~..u8.~|
000000a0  2a 00 77 32 66 8b 46 1c  66 83 c0 0c bb 00 80 b9  |*.w2f.F.f.......|
000000b0  01 00 e8 2b 00 e9 48 03  a0 fa 7d b4 7d 8b f0 ac  |...+..H...}.}...|
000000c0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000d0  ee a0 fb 7d eb e5 a0 f9  7d eb e0 98 cd 16 cd 19  |...}....}.......|
000000e0  66 60 66 3b 46 f8 0f 82  4a 00 66 6a 00 66 50 06  |f`f;F...J.fj.fP.|
000000f0  53 66 68 10 00 01 00 80  7e 02 00 0f 85 20 00 b4  |Sfh.....~.... ..|
00000100  41 bb aa 55 8a 56 40 cd  13 0f 82 1c 00 81 fb 55  |A..U.V@........U|
00000110  aa 0f 85 14 00 f6 c1 01  0f 84 0d 00 fe 46 02 b4  |.............F..|
00000120  42 8a 56 40 8b f4 cd 13  b0 f9 66 58 66 58 66 58  |B.V@......fXfXfX|
00000130  66 58 eb 2a 66 33 d2 66  0f b7 4e 18 66 f7 f1 fe  |fX.*f3.f..N.f...|
00000140  c2 8a ca 66 8b d0 66 c1  ea 10 f7 76 1a 86 d6 8a  |...f..f....v....|
00000150  56 40 8a e8 c0 e4 06 0a  cc b8 01 02 cd 13 66 61  |V@............fa|
00000160  0f 82 54 ff 81 c3 00 02  66 40 49 0f 85 71 ff c3  |..T.....f@I..q..|
00000170  4e 54 4c 44 52 20 20 20  20 20 20 00 00 00 00 00  |NTLDR      .....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 41 70  |..............Ap|
000001b0  70 6c 65 20 69 50 6f 64  20 20 20 20 20 20 00 01  |ple iPod      ..|
000001c0  01 00 00 fe 3f 09 3f 00  00 00 4b 73 02 00 00 00  |....?.?...Ks....|
000001d0  01 0a 0b fe fe ff 8a 73  02 00 b5 ca 7b 03 00 00  |.......s....{...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda2

00000000  6e 65 48 6f 6c 64 65 72  20 3d 20 67 2e 65 64 74  |neHolder = g.edt|
00000010  5f 6f 75 74 73 69 64 65  6c 69 6e 65 2e 76 61 6c  |_outsideline.val|
00000020  75 65 3b 0d 0a 20 20 20  20 20 20 20 20 54 61 70  |ue;..        Tap|
00000030  69 4f 62 6a 2e 73 65 74  5f 44 69 61 6c 4f 75 74  |iObj.set_DialOut|
00000040  28 67 2e 65 64 74 5f 6f  75 74 73 69 64 65 6c 69  |(g.edt_outsideli|
00000050  6e 65 2e 76 61 6c 75 65  29 3b 0d 0a 0d 0a 20 20  |ne.value);....  |
00000060  20 20 20 20 20 20 69 66  20 28 67 2e 65 64 74 5f  |      if (g.edt_|
00000070  6f 75 74 73 69 64 65 6c  69 6e 65 2e 76 61 6c 75  |outsideline.valu|
00000080  65 20 21 3d 20 22 22 29  0d 0a 20 20 20 20 20 20  |e != "")..      |
00000090  20 20 7b 0d 0a 20 20 20  20 20 20 20 20 20 20 20  |  {..           |
000000a0  20 67 2e 6c 62 6c 5f 6f  75 74 73 69 64 65 6c 69  | g.lbl_outsideli|
000000b0  6e 65 2e 69 6e 6e 65 72  48 54 4d 4c 20 3d 20 4c  |ne.innerHTML = L|
000000c0  5f 6f 75 74 73 69 64 65  6c 69 6e 65 5f 54 65 78  |_outsideline_Tex|
000000d0  74 3b 0d 0a 20 20 20 20  20 20 20 20 20 20 20 20  |t;..            |
000000e0  67 2e 6c 62 6c 5f 6f 75  74 73 69 64 65 6c 69 6e  |g.lbl_outsidelin|
000000f0  65 2e 63 6c 61 73 73 4e  61 6d 65 20 3d 20 22 74  |e.className = "t|
00000100  65 78 74 2d 70 72 69 6d  61 72 79 22 3b 0d 0a 20  |ext-primary";.. |
00000110  20 20 20 20 20 20 20 7d  0d 0a 20 20 20 20 20 20  |       }..      |
00000120  20 20 65 6c 73 65 0d 0a  20 20 20 20 20 20 20 20  |  else..        |
00000130  7b 0d 0a 20 20 20 20 20  20 20 20 20 20 20 20 67  |{..            g|
00000140  54 6f 6f 42 75 73 79 48  61 76 65 45 72 72 6f 72  |TooBusyHaveError|
00000150  32 20 3d 20 74 72 75 65  3b 0d 0a 20 20 20 20 20  |2 = true;..     |
00000160  20 20 20 20 20 20 20 67  2e 6c 62 6c 5f 6f 75 74  |       g.lbl_out|
00000170  73 69 64 65 6c 69 6e 65  2e 69 6e 6e 65 72 48 54  |sideline.innerHT|
00000180  4d 4c 20 3d 20 4c 5f 6f  75 74 73 69 64 65 6c 69  |ML = L_outsideli|
00000190  6e 65 30 31 5f 54 65 78  74 3b 0d 0a 20 20 20 20  |ne01_Text;..    |
000001a0  20 20 20 20 20 20 20 20  67 2e 6c 62 6c 5f 6f 75  |        g.lbl_ou|
000001b0  74 73 69 64 65 6c 69 6e  65 2e 63 6c 61 73 00 fe  |tsideline.clas..|
000001c0  ff ff 82 fe ff ff 02 70  00 08 00 70 b2 00 00 fe  |.......p...p....|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 80 25 00 00 00  |............%...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1


Unknown BootLoader  on sdc2

00000000  eb 3c 90 2a 55 4f 4b 4a  49 48 43 00 02 20 20 00  |.<.*UOKJIHC..  .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 8a 73 02 00  |........?....s..|
00000020  b4 ca 7b 03 ba 37 00 00  00 00 00 00 02 00 00 00  |..{..7..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 01 29 34 6a ab e5 49  50 4f 44 20 20 20 20 20  |..)4j..IPOD     |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 5b 7c ac  |  FAT32   ...[|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 7b  7b 7e 7e 7c 20 53 20 54  |.......{{~~| S T|
00000080  20 4f 20 50 20 7c 20 54  68 69 73 20 69 73 20 41  | O P | This is A|
00000090  70 70 6c 65 20 69 50 6f  64 20 6e 6f 74 20 61 20  |pple iPod not a |
000000a0  62 6f 6f 74 61 62 6c 65  20 64 69 73 6b 2e 50 6c  |bootable disk.Pl|
000000b0  65 61 73 65 20 74 72 79  20 61 67 61 69 6e 20 2e  |ease try again .|
000000c0  2e 2e 20 00 00 00 00 00  00 00 00 00 00 00 00 00  |.. .............|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

/home/john/Downloads/boot_info_script055.sh: line 892:  2991 Killed                  mount -r -t "$type" $part "$mountname" 2>> $Mount_Error
hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc1: No such file or directory

```

---

### Post by mikewhatever on 2010-10-09
Try running the **sudo update-grub** command. It should find all OSs and add a boot entry for each to the menu.

---

### Post by drs305 on 2010-10-09
Pending.

Posted to the wrong thread, but what *mikewhatever* suggests may find it. As you can see, the boot info script does not even see anything in sda8.

You might inspect the partition with either gparted or System, Administration, Disk Utility to see if there is anything on the partition. You can also attempt to mount the partition and inspect the contents if update-grub doesn't add an entry. The boot info script does a good job of finding OSs so I'm concerned that Maverick isn't on sda8.

Content added.

---

### Post by BingHeZhouKe on 2010-10-09
your ubuntu 10.10 isn't recognized,maybe its boot file is over,
there is so many kernels in your ubuntu 10.04,why not get rid of them ?

---

### Post by JohnMac on 2010-10-10
I tried deleting unwanted kernals. When I opened the partition with Gparted it shows some of the partition used (3Gig). I wasn't able to mount sda8 and look inside. When I rightclicked on sda8 it said that it was not mounted but when I asked gparted to "check" on sda6 it said there was an error the partition was mounted or being used by another program.:confused:

Any clues?

---

### Post by drs305 on 2010-10-10
Depending on how much time you spent in installing & customizing Maverick your best course may be to just delete sda8 and try again. There is definitely something wrong with the disk reporting.

You could try opening Disk Utility (System, Administration, Disk Utility) to see what it reports regarding sda8. 

I would also recommend running an fsck check:
```

sudo e2fsck -C0 -p -f -v /dev/sda8
*# If it finds errors:*
sudo e2fsck -f -y -v /dev/sda8

```

And if you really need sda8 as is, there are apps such as [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status") that might help with the partition table if nothing about helps.

As far as all the kernels, I'd recommend Ubuntu Tweak. It's a great GUI app that can remove unneeded kernels. I made up this guide on removing kernels last week which details how to use it:
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by efflandt on 2010-10-10
Something changed in grub2 in 10.10 which identifies partitions slightly differently than grub2 in 10.04.  Not sure if anything is different in the mbr part of grub or just in /boot/grub.

This is an example of a menuentry in 10.10 (1st partition of external usb drive).  Note the (hd1,msdos1) instead of hd(1,1):

```
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set f227491a-860a-4500-8bbc-1dc48e9ccd38
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f227491a-860a-4500-8bbc-1dc48e9ccd38 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
```That is not relevant to your problem (unless your custom grub.cfg in 10.10 did that incorrectly).  The current problem is whether you can even mount sda8 from 10.04 (bootinfo_script could not).  That problem could explain why update-grub in 10.04 cannot find 10.10.  Boot Info Script 0.55 dated February 15th, 2010 should be able to find it (although I am using ext3):

```
sdf1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
```

---

### Post by JohnMac on 2010-10-11
Thanks for your help all.
I am in my old Lucid livecd and I have been able to mount and check out my sda8 and all seems well. I used fsck to check the partitions and all seems well. 

I did use Tweak to remove most of my old kernals. I could just delete the partition I suppose, it is only a development install. 

I'll reboot and try again.

---

### Post by JohnMac on 2010-10-11
It worked, I'm in Meerkat after a update-grub. Maybe my Meerkat livecd has a bug.:)

---

### Post by 32ftpersecond on 2010-10-12
update-grub seems to be the key with my systems as well, thanks.

---

