---
title: "Ubuntu 10.10 Server upgraded to 11.04 (grub problem)"
date: 2011-08-17
forum: Installation &amp; Upgrades
---

### Post by PippoPippo on 2011-08-17
Hi,

I have upgraded from 10.10 to 11.04 server. Upon reboot I got stuck at the grub prompt. Initially I was able to boot using

linux /vmlinuz-2.6.38-10-generic-pae root=UUID=####
initrd /initrd.img-2.6.38-10-generic-pae
boot

where #### is the UUID of the (homeserver-root) partition (the disk uses LVM).

After trying various stuff to repair grub, including trying to "Rescue system" from the install CD to no avail, I can no longer boot, not even from the grub prompt. 

I attach the results from running boot_info_script.sh. 
TIA
Giulio

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (homeserver-root)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 624723168 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda3: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.......Y..V...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 4410330 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

sdc: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    39,519,899    39,519,837  8e Linux LVM
/dev/sda2         624,642,048   625,141,759       499,712   5 Extended
/dev/sda5         624,644,096   625,141,759       497,664  83 Linux
/dev/sda3          39,520,256   624,642,047   585,121,792  8e Linux LVM


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4037 MB, 4037017600 bytes
2 heads, 63 sectors/track, 62577 cylinders, total 7884800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             64     7,884,799     7,884,736   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/ramzswap0                                          swap       
/dev/sda1        1FNlcx-xFiQ-SxLg-xy1s-mM7h-XOt4-N0mH0D LVM2_member 
/dev/sda3        mXzqZz-W5rS-d6pa-JaPw-qWnC-eb1r-AHq9sc LVM2_member 
/dev/sda5        460155a7-bf8b-4668-b543-2a3e22f0b3ad   ext2       
/dev/sdb1        8C93-2951                              vfat       
/dev/sdc         D816-061E                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc         /media/D816-061E         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


============================= sda5/grub/grub.cfg: ==============================

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
}

insmod lvm
insmod part_msdos
insmod part_msdos
insmod ext2
set root='(homeserver-root)'
search --no-floppy --fs-uuid --set=root e518d485-fc0f-49af-a7a0-19f0cfddbbc9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 460155a7-bf8b-4668-b543-2a3e22f0b3ad
set locale_dir=($root)/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 460155a7-bf8b-4668-b543-2a3e22f0b3ad
	linux	/vmlinuz-2.6.38-10-generic-pae root=/dev/mapper/homeserver-root ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-10-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 460155a7-bf8b-4668-b543-2a3e22f0b3ad
	echo	'Loading Linux 2.6.38-10-generic-pae ...'
	linux	/vmlinuz-2.6.38-10-generic-pae root=/dev/mapper/homeserver-root ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-10-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 460155a7-bf8b-4668-b543-2a3e22f0b3ad
	linux	/vmlinuz-2.6.35-28-generic-pae root=/dev/mapper/homeserver-root ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 460155a7-bf8b-4668-b543-2a3e22f0b3ad
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/vmlinuz-2.6.35-28-generic-pae root=/dev/mapper/homeserver-root ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-28-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 460155a7-bf8b-4668-b543-2a3e22f0b3ad
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 460155a7-bf8b-4668-b543-2a3e22f0b3ad
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 298.063583374 = 320.043335680  grub/core.img                                  2
 298.063298225 = 320.043029504  grub/grub.cfg                                  1
 298.035417557 = 320.013092864  initrd.img-2.6.35-28-generic-pae              49
 297.912487030 = 319.881097216  initrd.img-2.6.38-10-generic-pae              59
 298.022096634 = 319.998789632  vmlinuz-2.6.35-28-generic-pae                 20
 297.864701271 = 319.829787648  vmlinuz-2.6.38-10-generic-pae                 21

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 f6 03  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 50 78 00 05 1e 00 00  00 00 00 00 02 00 00 00  |.Px.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 1e 06 16 d8 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa b8 b0 07 8e c0  |  FAT32   ......|
00000060  8e d8 b8 00 10 8e d0 bc  fe ff a0 fb 02 2c 01 72  |.............,.r|
00000070  1e 74 0f 3b 1e 00 01 74  09 a1 1c 01 0b 06 1e 01  |.t.;...t........|
00000080  75 0d 0a d2 75 05 80 26  fa 02 84 88 16 fc 02 fb  |u...u..&........|
00000090  bd cc 02 e8 1b 01 be f0  02 66 8b 1c 66 03 1e 1c  |.........f..f...|
000000a0  01 66 89 1c d0 0e fa 02  73 38 b4 41 bb aa 55 8a  |.f......s8.A..U.|
000000b0  16 fc 02 f6 c2 80 74 2a  cd 13 72 26 d1 e9 73 22  |......t*..r&..s"|
000000c0  81 fb 55 aa 75 1c b9 03  00 b4 42 8a 16 fc 02 be  |..U.u.....B.....|
000000d0  e8 02 8b 5c 10 89 5c 02  cd 13 72 04 0a e4 74 32  |...\..\...r...t2|
000000e0  e2 e7 d0 0e fa 02 73 13  b4 08 8a 16 fc 02 c4 3e  |......s........>|
000000f0  f4 02 cd 13 72 05 83 e1  3f 75 19 d0 0e fa 02 73  |....r...?u.....s|
00000100  0f 8a 36 1a 01 fe ce 8b  0e 18 01 83 e1 3f 75 04  |..6..........?u.|
00000110  eb 6d eb 75 88 36 f4 02  89 0e f6 02 8a d9 8a fe  |.m.u.6..........|
00000120  a1 f0 02 8b 16 f2 02 e8  6a 00 8a 16 fc 02 fe c3  |........j.......|
00000130  32 ff 8b f3 c4 1e ec 02  8b 2e f8 02 3b ee 79 02  |2...........;.y.|
00000140  8b f5 bf 03 00 0b db 75  09 b4 00 cd 13 4f 74 2f  |.......u.....Ot/|
00000150  72 f7 8b c6 b4 02 cd 13  72 ef 2b ee 74 2b c1 e6  |r.......r.+.t+..|
00000160  09 03 de 80 e1 c0 fe c1  8b 36 f6 02 fe c6 3a 36  |.........6....:6|
00000170  f4 02 76 c8 32 f6 fe c5  75 c2 80 c1 40 eb bd bd  |..v.2...u...@...|
00000180  df 02 e8 2c 00 cd 18 eb  fe bd d7 02 e8 22 00 ea  |...,........."..|
00000190  00 01 00 10 53 f7 f1 fe  c2 8a ca 8a df 32 ff 43  |....S........2.C|
000001a0  33 d2 f7 f3 8a f2 8a e8  c0 e4 06 5b 2a d9 0a cc  |3..........[*...|
000001b0  c3 60 1e 07 b4 0f cd 10  b4 03 cd 10 b8 01 13 b3  |.`..............|
000001c0  07 33 c9 26 8a 4e 00 45  cd 10 61 c3 0a 0d 0a 0a  |.3.&.N.E..a.....|
000001d0  4c 6f 61 64 69 6e 67 07  20 53 79 6d 6f 62 69 08  |Loading. Symobi.|
000001e0  20 45 52 52 4f 52 0d 0a  10 00 00 00 00 00 10 10  | ERROR..........|
000001f0  08 40 00 00 00 00 00 00  49 00 87 02 80 6e 55 aa  |.@......I....nU.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


```

---

### Post by YesWeCan on 2011-08-17
Hi there.
What do you get when you boot? The grub-rescue> prompt?

It appears that you have an LVM root volume and also a separate boot partition sda5.

One issue is that the Grub boot program in the MBR area is looking for /boot/grub in the root volume instead of in sda5. So that won't work.

The bootinfoscript output is not complete because the LVM volumes are not active by default when you boot a live CD. So would you install LVM and activate the volumes and re-run bootinfoscript?
[COLOR=Navy]sudo apt-get install lvm2
sudo vgchange -ay[/COLOR]

You should see a list of the LVM volumes, one of which should be homeserver-root.

While the script output is being considered, you might want to reinstall Grub so it looks for sda5 instead of homeserver-root:
[COLOR=Navy]sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]

And reboot and see what it does now.

---

### Post by PippoPippo on 2011-08-19
Hi, thank you for your help.

At the time of my first message the prompt was grub> not grub-rescue>

> sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
That did not work. When I rebooted I was presented with an initramfs> prompt and did not know what to do.

I repeated the procedure following the instructions here 
[http://stephentanner.com/index.php/2011/05/restoring-grub-for-an-encrypted-lvm/](http://stephentanner.com/index.php/2011/05/restoring-grub-for-an-encrypted-lvm/)  apart from the encryption bit which does not apply.

Namely instead of 

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

I entered

mkdir /media/linux
mount /dev/homeserver/root /media/linux
mount -o bind /proc /media/linux/proc
mount -o bind /dev /media/linux/dev
mount -o bind /sys /media/linux/sys
chroot /media/linux /bin/bash
mount /dev/sda5 /boot
grub-install /dev/sda

The problem with this, is that upon reboot it is as if ubuntu sets the wrong frequency for my monitor and I get a garbled screen instead of the grub menu. Then the screen switches itself off.

I attach the result of the boot_info script after activating the logical volume. Is it correct that /dev/sda1 rather than /dev/sda5 is marked as the boot partition?

TIA
Giulio

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 624723168 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.......Y..V...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 4410330 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

homeserver-root': ______________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

homeserver-swap_1': ____________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    39,519,899    39,519,837  8e Linux LVM
/dev/sda2         624,642,048   625,141,759       499,712   5 Extended
/dev/sda5         624,644,096   625,141,759       497,664  83 Linux
/dev/sda3          39,520,256   624,642,047   585,121,792  8e Linux LVM


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4037 MB, 4037017600 bytes
2 heads, 63 sectors/track, 62577 cylinders, total 7884800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             64     7,884,799     7,884,736   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/homeserver-root e518d485-fc0f-49af-a7a0-19f0cfddbbc9   ext3       
/dev/mapper/homeserver-swap_1 ea269adf-3899-4173-b68c-8551bf20276f   swap       
/dev/ramzswap0                                          swap       
/dev/sda1        1FNlcx-xFiQ-SxLg-xy1s-mM7h-XOt4-N0mH0D LVM2_member 
/dev/sda3        mXzqZz-W5rS-d6pa-JaPw-qWnC-eb1r-AHq9sc LVM2_member 
/dev/sda5        460155a7-bf8b-4668-b543-2a3e22f0b3ad   ext2       
/dev/sdb1        8C93-2951                              vfat       
/dev/sdc         D816-061E                              vfat       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
homeserver-root
homeserver-swap_1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc         /media/D816-061E         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


============================= sda5/grub/grub.cfg: ==============================

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
}

insmod lvm
insmod part_msdos
insmod part_msdos
insmod ext2
set root='(homeserver-root)'
search --no-floppy --fs-uuid --set=root e518d485-fc0f-49af-a7a0-19f0cfddbbc9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 460155a7-bf8b-4668-b543-2a3e22f0b3ad
set locale_dir=($root)/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 460155a7-bf8b-4668-b543-2a3e22f0b3ad
    linux    /vmlinuz-2.6.38-10-generic-pae root=/dev/mapper/homeserver-root ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-10-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 460155a7-bf8b-4668-b543-2a3e22f0b3ad
    echo    'Loading Linux 2.6.38-10-generic-pae ...'
    linux    /vmlinuz-2.6.38-10-generic-pae root=/dev/mapper/homeserver-root ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-10-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 460155a7-bf8b-4668-b543-2a3e22f0b3ad
    linux    /vmlinuz-2.6.35-28-generic-pae root=/dev/mapper/homeserver-root ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 460155a7-bf8b-4668-b543-2a3e22f0b3ad
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /vmlinuz-2.6.35-28-generic-pae root=/dev/mapper/homeserver-root ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-28-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 460155a7-bf8b-4668-b543-2a3e22f0b3ad
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 460155a7-bf8b-4668-b543-2a3e22f0b3ad
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 297.890734673 = 319.857740800  boot/grub/core.img                             2
 298.057332039 = 320.036623360  grub/core.img                                  2
 298.063298225 = 320.043029504  grub/grub.cfg                                  1
 298.035417557 = 320.013092864  initrd.img-2.6.35-28-generic-pae              49
 297.912487030 = 319.881097216  initrd.img-2.6.38-10-generic-pae              59
 298.022096634 = 319.998789632  vmlinuz-2.6.35-28-generic-pae                 20
 297.864701271 = 319.829787648  vmlinuz-2.6.38-10-generic-pae                 21

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on homeserver-root'


Unknown BootLoader on homeserver-swap_1'


Unknown BootLoader on sdc

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 f6 03  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 50 78 00 05 1e 00 00  00 00 00 00 02 00 00 00  |.Px.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 1e 06 16 d8 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa b8 b0 07 8e c0  |  FAT32   ......|
00000060  8e d8 b8 00 10 8e d0 bc  fe ff a0 fb 02 2c 01 72  |.............,.r|
00000070  1e 74 0f 3b 1e 00 01 74  09 a1 1c 01 0b 06 1e 01  |.t.;...t........|
00000080  75 0d 0a d2 75 05 80 26  fa 02 84 88 16 fc 02 fb  |u...u..&........|
00000090  bd cc 02 e8 1b 01 be f0  02 66 8b 1c 66 03 1e 1c  |.........f..f...|
000000a0  01 66 89 1c d0 0e fa 02  73 38 b4 41 bb aa 55 8a  |.f......s8.A..U.|
000000b0  16 fc 02 f6 c2 80 74 2a  cd 13 72 26 d1 e9 73 22  |......t*..r&..s"|
000000c0  81 fb 55 aa 75 1c b9 03  00 b4 42 8a 16 fc 02 be  |..U.u.....B.....|
000000d0  e8 02 8b 5c 10 89 5c 02  cd 13 72 04 0a e4 74 32  |...\..\...r...t2|
000000e0  e2 e7 d0 0e fa 02 73 13  b4 08 8a 16 fc 02 c4 3e  |......s........>|
000000f0  f4 02 cd 13 72 05 83 e1  3f 75 19 d0 0e fa 02 73  |....r...?u.....s|
00000100  0f 8a 36 1a 01 fe ce 8b  0e 18 01 83 e1 3f 75 04  |..6..........?u.|
00000110  eb 6d eb 75 88 36 f4 02  89 0e f6 02 8a d9 8a fe  |.m.u.6..........|
00000120  a1 f0 02 8b 16 f2 02 e8  6a 00 8a 16 fc 02 fe c3  |........j.......|
00000130  32 ff 8b f3 c4 1e ec 02  8b 2e f8 02 3b ee 79 02  |2...........;.y.|
00000140  8b f5 bf 03 00 0b db 75  09 b4 00 cd 13 4f 74 2f  |.......u.....Ot/|
00000150  72 f7 8b c6 b4 02 cd 13  72 ef 2b ee 74 2b c1 e6  |r.......r.+.t+..|
00000160  09 03 de 80 e1 c0 fe c1  8b 36 f6 02 fe c6 3a 36  |.........6....:6|
00000170  f4 02 76 c8 32 f6 fe c5  75 c2 80 c1 40 eb bd bd  |..v.2...u...@...|
00000180  df 02 e8 2c 00 cd 18 eb  fe bd d7 02 e8 22 00 ea  |...,........."..|
00000190  00 01 00 10 53 f7 f1 fe  c2 8a ca 8a df 32 ff 43  |....S........2.C|
000001a0  33 d2 f7 f3 8a f2 8a e8  c0 e4 06 5b 2a d9 0a cc  |3..........[*...|
000001b0  c3 60 1e 07 b4 0f cd 10  b4 03 cd 10 b8 01 13 b3  |.`..............|
000001c0  07 33 c9 26 8a 4e 00 45  cd 10 61 c3 0a 0d 0a 0a  |.3.&.N.E..a.....|
000001d0  4c 6f 61 64 69 6e 67 07  20 53 79 6d 6f 62 69 08  |Loading. Symobi.|
000001e0  20 45 52 52 4f 52 0d 0a  10 00 00 00 00 00 10 10  | ERROR..........|
000001f0  08 40 00 00 00 00 00 00  49 00 87 02 80 6e 55 aa  |.@......I....nU.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/homeserver-root': No such file or directory
hexdump: /dev/mapper/homeserver-root': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/homeserver-swap_1': No such file or directory
hexdump: /dev/mapper/homeserver-swap_1': No such file or directory


```

---

### Post by YesWeCan on 2011-08-19
The boot partition "flag" is ignored by Grub (which replaces the normal MBR boot code) so it doesn't matter which partition it is set to.

Would you mind posting your /etc/fstab? The bootinfoscript seems to have omitted it.

The best instructions for doing a chroot Grub install are here: [https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)
I'd recommend you start again and use these - they mount /dev/pts and do an update-grub.

Boot live CD
sudo apt-get install lvm2
sudo vgchange -ay

Then follow the chroot process, remembering as you did before to mount /dev/sda5 at /boot.


BTW you do not need a separate boot partition. It complicates things a little. If you wish you can copy its contents back to the original /boot and remove its mount from fstab and reinstall Grub. If you need details just ask.

---

