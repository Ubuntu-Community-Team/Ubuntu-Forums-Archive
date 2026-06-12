---
title: "initrd freeze after upgrade 10.10 to 11.04 reboot"
date: 2011-09-11
forum: Installation &amp; Upgrades
---

### Post by BeowulfNode on 2011-09-11
I realise there are a lot of posts about problems with upgrading to 11.04 natty however I can only find ones that talk about graphics problems or ones were there are error messages, which does not seem to apply to the issue I am having.

I had a ubuntu 10.10 server install with ssh, zfs-fuse, samba, and no gui. The basic role for this pc is as a nas box, so sata ports are reserved for 6 data drives and ubuntu is installed on a raid1 of 2 USB sticks.  I'd been having some problems with a particular stick and at some stage decided to grow the raid1 to 3 usb sticks.  Before the upgrade I removed the problematic stick, and had done a ```
mdadm --manage /dev/md0 --remove faulty
``` but didn't 'shrink' the raid1 to 2 devices so it had 2 active and 1 removed.

Then I ran ```
do-release-upgrade
```.  It seemed to go fine until  the reboot, when the screen was just black after grub, not even a  blinking cursor.

So I tried the recovery option in grub and it froze with the words saying
```
Loading kernel...
Loading ramdisk...
```then nothing

So I tried the "Previous Linux versions" and choosing 'Ubuntu, with Linux 2.6.35-28-server' worked and got me to a login prompt.  I then found out natty had installed the 2.6.38-11-server kernel.

running the boot_info_script.sh available somewhere on this forum gave some weird thing saying "core.img is at this location and looks 
    for ?? on this drive." I tried doing some update-grub, grub-install, and dpkg-reconfigure grub-pc commands but it turns out the problem was lzma was not installed and grub did not have a problem. so running it again gave
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sdg and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (md0)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdh and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (md0)/boot/grub on this drive.

sdg1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdg2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdh1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdh2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

md0: ___________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

md1: ___________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda: ___________________________________________________________________________

    File system:       zfs
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type 'zfs'

sdb: ___________________________________________________________________________

    File system:       zfs
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type 'zfs'
mount: unknown filesystem type 'zfs'

sdc: ___________________________________________________________________________

    File system:       zfs
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type 'zfs'
mount: unknown filesystem type 'zfs'
mount: unknown filesystem type 'zfs'

sdd: ___________________________________________________________________________

    File system:       zfs
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type 'zfs'
mount: unknown filesystem type 'zfs'
mount: unknown filesystem type 'zfs'
mount: unknown filesystem type 'zfs'

sde: ___________________________________________________________________________

    File system:       zfs
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type 'zfs'
mount: unknown filesystem type 'zfs'
mount: unknown filesystem type 'zfs'
mount: unknown filesystem type 'zfs'
mount: unknown filesystem type 'zfs'

sdf: ___________________________________________________________________________

    File system:       zfs
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type 'zfs'
mount: unknown filesystem type 'zfs'
mount: unknown filesystem type 'zfs'
mount: unknown filesystem type 'zfs'
mount: unknown filesystem type 'zfs'
mount: unknown filesystem type 'zfs'

============================ Drive/Partition Info: =============================

Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 15.8 GB, 15833497600 bytes
64 heads, 32 sectors/track, 15100 cylinders, total 30924800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1    *          2,048    29,298,687    29,296,640  fd Linux raid autodetect
/dev/sdg2          29,298,688    30,298,111       999,424  fd Linux raid autodetect


Drive: sdh _____________________________________________________________________

Disk /dev/sdh: 16.0 GB, 16039018496 bytes
75 heads, 40 sectors/track, 10442 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdh1    *          3,000    29,297,999    29,295,000  fd Linux raid autodetect
/dev/sdh2          29,298,000    30,296,999       999,000  fd Linux raid autodetect


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/md0         290e3c87-4889-4f21-b19e-9167a7a5e3f2   ext3       sys
/dev/sda                                                zfs        
/dev/sdb                                                zfs        
/dev/sdc                                                zfs        
/dev/sdd                                                zfs        
/dev/sde                                                zfs        
/dev/sdf                                                zfs        
/dev/sdg1        166d6ae4-4eac-ea87-61d5-599cc7ed6bd3   linux_raid_member 
/dev/sdg2        08f14208-cae6-9235-fc96-6214ef60420b   linux_raid_member 
/dev/sdh1        166d6ae4-4eac-ea87-61d5-599cc7ed6bd3   linux_raid_member 
/dev/sdh2        08f14208-cae6-9235-fc96-6214ef60420b   linux_raid_member 

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/md0         /                        ext3       (rw,noatime,errors=remount-ro)


=========================== md0/boot/grub/grub.cfg: ============================

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

insmod raid
insmod mdraid09
insmod part_msdos
insmod part_msdos
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set=root 290e3c87-4889-4f21-b19e-9167a7a5e3f2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=2
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
menuentry 'Ubuntu, with Linux 2.6.38-11-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod raid
    insmod mdraid09
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set=root 290e3c87-4889-4f21-b19e-9167a7a5e3f2
    linux    /boot/vmlinuz-2.6.38-11-server root=UUID=290e3c87-4889-4f21-b19e-9167a7a5e3f2 ro   quiet
    initrd    /boot/initrd.img-2.6.38-11-server
}
menuentry 'Ubuntu, with Linux 2.6.38-11-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod raid
    insmod mdraid09
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set=root 290e3c87-4889-4f21-b19e-9167a7a5e3f2
    echo    'Loading Linux 2.6.38-11-server ...'
    linux    /boot/vmlinuz-2.6.38-11-server root=UUID=290e3c87-4889-4f21-b19e-9167a7a5e3f2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-server
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod raid
    insmod mdraid09
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set=root 290e3c87-4889-4f21-b19e-9167a7a5e3f2
    linux    /boot/vmlinuz-2.6.35-28-server root=UUID=290e3c87-4889-4f21-b19e-9167a7a5e3f2 ro   quiet
    initrd    /boot/initrd.img-2.6.35-28-server
}
menuentry 'Ubuntu, with Linux 2.6.35-28-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod raid
    insmod mdraid09
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set=root 290e3c87-4889-4f21-b19e-9167a7a5e3f2
    echo    'Loading Linux 2.6.35-28-server ...'
    linux    /boot/vmlinuz-2.6.35-28-server root=UUID=290e3c87-4889-4f21-b19e-9167a7a5e3f2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-server
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod raid
    insmod mdraid09
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set=root 290e3c87-4889-4f21-b19e-9167a7a5e3f2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod raid
    insmod mdraid09
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set=root 290e3c87-4889-4f21-b19e-9167a7a5e3f2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-11-server (on /dev/sdg1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdg,msdos1)'
    search --no-floppy --fs-uuid --set=root 290e3c87-4889-4f21-b19e-9167a7a5e3f2
    linux /boot/vmlinuz-2.6.38-11-server root=UUID=290e3c87-4889-4f21-b19e-9167a7a5e3f2 ro quiet
    initrd /boot/initrd.img-2.6.38-11-server
}
menuentry "Ubuntu, with Linux 2.6.38-11-server (recovery mode) (on /dev/sdg1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdg,msdos1)'
    search --no-floppy --fs-uuid --set=root 290e3c87-4889-4f21-b19e-9167a7a5e3f2
    linux /boot/vmlinuz-2.6.38-11-server root=UUID=290e3c87-4889-4f21-b19e-9167a7a5e3f2 ro single
    initrd /boot/initrd.img-2.6.38-11-server
}
menuentry "Ubuntu, with Linux 2.6.35-28-server (on /dev/sdg1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdg,msdos1)'
    search --no-floppy --fs-uuid --set=root 290e3c87-4889-4f21-b19e-9167a7a5e3f2
    linux /boot/vmlinuz-2.6.35-28-server root=UUID=290e3c87-4889-4f21-b19e-9167a7a5e3f2 ro quiet
    initrd /boot/initrd.img-2.6.35-28-server
}
menuentry "Ubuntu, with Linux 2.6.35-28-server (recovery mode) (on /dev/sdg1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdg,msdos1)'
    search --no-floppy --fs-uuid --set=root 290e3c87-4889-4f21-b19e-9167a7a5e3f2
    linux /boot/vmlinuz-2.6.35-28-server root=UUID=290e3c87-4889-4f21-b19e-9167a7a5e3f2 ro single
    initrd /boot/initrd.img-2.6.35-28-server
}
menuentry "Ubuntu, with Linux 2.6.38-11-server (on /dev/sdh1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdh,msdos1)'
    search --no-floppy --fs-uuid --set=root 290e3c87-4889-4f21-b19e-9167a7a5e3f2
    linux /boot/vmlinuz-2.6.38-11-server root=UUID=290e3c87-4889-4f21-b19e-9167a7a5e3f2 ro quiet
    initrd /boot/initrd.img-2.6.38-11-server
}
menuentry "Ubuntu, with Linux 2.6.38-11-server (recovery mode) (on /dev/sdh1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdh,msdos1)'
    search --no-floppy --fs-uuid --set=root 290e3c87-4889-4f21-b19e-9167a7a5e3f2
    linux /boot/vmlinuz-2.6.38-11-server root=UUID=290e3c87-4889-4f21-b19e-9167a7a5e3f2 ro single
    initrd /boot/initrd.img-2.6.38-11-server
}
menuentry "Ubuntu, with Linux 2.6.35-28-server (on /dev/sdh1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdh,msdos1)'
    search --no-floppy --fs-uuid --set=root 290e3c87-4889-4f21-b19e-9167a7a5e3f2
    linux /boot/vmlinuz-2.6.35-28-server root=UUID=290e3c87-4889-4f21-b19e-9167a7a5e3f2 ro quiet
    initrd /boot/initrd.img-2.6.35-28-server
}
menuentry "Ubuntu, with Linux 2.6.35-28-server (recovery mode) (on /dev/sdh1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdh,msdos1)'
    search --no-floppy --fs-uuid --set=root 290e3c87-4889-4f21-b19e-9167a7a5e3f2
    linux /boot/vmlinuz-2.6.35-28-server root=UUID=290e3c87-4889-4f21-b19e-9167a7a5e3f2 ro single
    initrd /boot/initrd.img-2.6.35-28-server
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

================================ md0/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=290e3c87-4889-4f21-b19e-9167a7a5e3f2 /               ext3    noatime,errors=remount-ro 0       1
# swap was on /dev/md1 during installation
# UUID=1d86812e-4bcc-4b77-9735-50ff615115c0 none            swap    sw              0       0
#
# File systems for storage in ram
#
none    /tmp        tmpfs    defaults,noatime    0    0
none    /var/run    tmpfs    defaults,noatime    0    0
none    /var/lock    tmpfs    defaults,noatime    0    0
none    /var/tmp    tmpfs    defaults,noatime    0    0
none    /var/log    tmpfs    defaults,noatime    0    0
--------------------------------------------------------------------------------

==================== md0: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   9.359706879 = 10.049908736   boot/grub/core.img                             1
   9.367198944 = 10.057953280   boot/grub/grub.cfg                             1
   9.299690247 = 9.985466368    boot/initrd.img-2.6.35-28-server               7
   9.264705658 = 9.947901952    boot/initrd.img-2.6.38-11-server               7
   9.358608246 = 10.048729088   boot/vmlinuz-2.6.35-28-server                  3
   9.374458313 = 10.065747968   boot/vmlinuz-2.6.38-11-server                  3
   9.264705658 = 9.947901952    initrd.img                                     7
   9.374458313 = 10.065747968   vmlinuz                                        3

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdg2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000200

Unknown BootLoader on sdh2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000200

Unknown BootLoader on md1

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000200

Unknown BootLoader on sdb

00000000  33 c0 8e d0 bc 00 7c 8e  c0 8e d8 be 00 7c bf 00  |3.....|......|..|
00000010  06 b9 00 02 fc f3 a4 50  68 1c 06 cb fb b9 04 00  |.......Ph.......|
00000020  bd be 07 80 7e 00 00 7c  0b 0f 85 10 01 83 c5 10  |....~..|........|
00000030  e2 f1 cd 18 88 56 00 55  c6 46 11 05 c6 46 10 00  |.....V.U.F...F..|
00000040  b4 41 bb aa 55 cd 13 5d  72 0f 81 fb 55 aa 75 09  |.A..U..]r...U.u.|
00000050  f7 c1 01 00 74 03 fe 46  10 66 60 80 7e 10 00 74  |....t..F.f`.~..t|
00000060  26 66 68 00 00 00 00 66  ff 76 08 68 00 00 68 00  |&fh....f.v.h..h.|
00000070  7c 68 01 00 68 10 00 b4  42 8a 56 00 8b f4 cd 13  ||h..h...B.V.....|
00000080  9f 83 c4 10 9e eb 14 b8  01 02 bb 00 7c 8a 56 00  |............|.V.|
00000090  8a 76 01 8a 4e 02 8a 6e  03 cd 13 66 61 73 1e fe  |.v..N..n...fas..|
000000a0  4e 11 0f 85 0c 00 80 7e  00 80 0f 84 8a 00 b2 80  |N......~........|
000000b0  eb 82 55 32 e4 8a 56 00  cd 13 5d eb 9c 81 3e fe  |..U2..V...]...>.|
000000c0  7d 55 aa 75 6e ff 76 00  e8 8a 00 0f 85 15 00 b0  |}U.un.v.........|
000000d0  d1 e6 64 e8 7f 00 b0 df  e6 60 e8 78 00 b0 ff e6  |..d......`.x....|
000000e0  64 e8 71 00 b8 00 bb cd  1a 66 23 c0 75 3b 66 81  |d.q......f#.u;f.|
000000f0  fb 54 43 50 41 75 32 81  f9 02 01 72 2c 66 68 07  |.TCPAu2....r,fh.|
00000100  bb 00 00 66 68 00 02 00  00 66 68 08 00 00 00 66  |...fh....fh....f|
00000110  53 66 53 66 55 66 68 00  00 00 00 66 68 00 7c 00  |SfSfUfh....fh.|.|
00000120  00 66 61 68 00 00 07 cd  1a 5a 32 f6 ea 00 7c 00  |.fah.....Z2...|.|
00000130  00 cd 18 a0 b7 07 eb 08  a0 b6 07 eb 03 a0 b5 07  |................|
00000140  32 e4 05 00 07 8b f0 ac  3c 00 74 fc bb 07 00 b4  |2.......<.t.....|
00000150  0e cd 10 eb f2 2b c9 e4  64 eb 00 24 02 e0 f8 24  |.....+..d..$...$|
00000160  02 c3 49 6e 76 61 6c 69  64 20 70 61 72 74 69 74  |..Invalid partit|
00000170  69 6f 6e 20 74 61 62 6c  65 00 45 72 72 6f 72 20  |ion table.Error |
00000180  6c 6f 61 64 69 6e 67 20  6f 70 65 72 61 74 69 6e  |loading operatin|
00000190  67 20 73 79 73 74 65 6d  00 4d 69 73 73 69 6e 67  |g system.Missing|
000001a0  20 6f 70 65 72 61 74 69  6e 67 20 73 79 73 74 65  | operating syste|
000001b0  6d 00 00 00 00 62 7a 99  91 b4 05 00 00 00 00 00  |m....bz.........|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sde

00000000  33 c0 8e d0 bc 00 7c 8e  c0 8e d8 be 00 7c bf 00  |3.....|......|..|
00000010  06 b9 00 02 fc f3 a4 50  68 1c 06 cb fb b9 04 00  |.......Ph.......|
00000020  bd be 07 80 7e 00 00 7c  0b 0f 85 10 01 83 c5 10  |....~..|........|
00000030  e2 f1 cd 18 88 56 00 55  c6 46 11 05 c6 46 10 00  |.....V.U.F...F..|
00000040  b4 41 bb aa 55 cd 13 5d  72 0f 81 fb 55 aa 75 09  |.A..U..]r...U.u.|
00000050  f7 c1 01 00 74 03 fe 46  10 66 60 80 7e 10 00 74  |....t..F.f`.~..t|
00000060  26 66 68 00 00 00 00 66  ff 76 08 68 00 00 68 00  |&fh....f.v.h..h.|
00000070  7c 68 01 00 68 10 00 b4  42 8a 56 00 8b f4 cd 13  ||h..h...B.V.....|
00000080  9f 83 c4 10 9e eb 14 b8  01 02 bb 00 7c 8a 56 00  |............|.V.|
00000090  8a 76 01 8a 4e 02 8a 6e  03 cd 13 66 61 73 1e fe  |.v..N..n...fas..|
000000a0  4e 11 0f 85 0c 00 80 7e  00 80 0f 84 8a 00 b2 80  |N......~........|
000000b0  eb 82 55 32 e4 8a 56 00  cd 13 5d eb 9c 81 3e fe  |..U2..V...]...>.|
000000c0  7d 55 aa 75 6e ff 76 00  e8 8a 00 0f 85 15 00 b0  |}U.un.v.........|
000000d0  d1 e6 64 e8 7f 00 b0 df  e6 60 e8 78 00 b0 ff e6  |..d......`.x....|
000000e0  64 e8 71 00 b8 00 bb cd  1a 66 23 c0 75 3b 66 81  |d.q......f#.u;f.|
000000f0  fb 54 43 50 41 75 32 81  f9 02 01 72 2c 66 68 07  |.TCPAu2....r,fh.|
00000100  bb 00 00 66 68 00 02 00  00 66 68 08 00 00 00 66  |...fh....fh....f|
00000110  53 66 53 66 55 66 68 00  00 00 00 66 68 00 7c 00  |SfSfUfh....fh.|.|
00000120  00 66 61 68 00 00 07 cd  1a 5a 32 f6 ea 00 7c 00  |.fah.....Z2...|.|
00000130  00 cd 18 a0 b7 07 eb 08  a0 b6 07 eb 03 a0 b5 07  |................|
00000140  32 e4 05 00 07 8b f0 ac  3c 00 74 fc bb 07 00 b4  |2.......<.t.....|
00000150  0e cd 10 eb f2 2b c9 e4  64 eb 00 24 02 e0 f8 24  |.....+..d..$...$|
00000160  02 c3 49 6e 76 61 6c 69  64 20 70 61 72 74 69 74  |..Invalid partit|
00000170  69 6f 6e 20 74 61 62 6c  65 00 45 72 72 6f 72 20  |ion table.Error |
00000180  6c 6f 61 64 69 6e 67 20  6f 70 65 72 61 74 69 6e  |loading operatin|
00000190  67 20 73 79 73 74 65 6d  00 4d 69 73 73 69 6e 67  |g system.Missing|
000001a0  20 6f 70 65 72 61 74 69  6e 67 20 73 79 73 74 65  | operating syste|
000001b0  6d 00 00 00 00 62 7a 99  2a fd 33 e9 00 00 00 00  |m....bz.*.3.....|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```I can't see any problems there myself but I'm not a linux guru.

I've tried various kernel parameters like removing quiet and adding different combinations of
nosplash --verbose text debug earlyprintk=vga,keep
and it still says nothing when running initrd for the 2.6.38.11-server kernel

**Any ideas on what to try next to get it to boot using the 2.6.38 series kernel?**
I have tried a desktop LiveCD and that worked no problem and had the kernel version 2.6.38.8-generic.  So I'm thinking there's some config problem, missing or extra kernel module causing problems, but I don't know how to troubleshoot that.

some info about my hardware from the commands
lspci -vvvnn
lsusb -v
lshw
also it is Motherboard revision 1.01G

```
root@dlnas:~# lspci -vvvnn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
    Subsystem: ASUSTeK Computer Inc. Device [1043:8388]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: [c4] HyperTransport: Slave or Primary Interface
        Command: BaseUnitID=0 UnitCnt=12 MastHost- DefDir- DUL-
        Link Control 0: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b-
        Link Config 0: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn-
        Link Control 1: CFlE- CST- CFE- <LkFail+ Init- EOC+ TXO+ <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b-
        Link Config 1: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
        Revision ID: 3.00
        Link Frequency 0: [b]
        Link Error 0: <Prot- <Ovfl- <EOC- CTLTm-
        Link Frequency Capability 0: 200MHz+ 300MHz- 400MHz+ 500MHz- 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz- 1.4GHz- 1.6GHz- Vend-
        Feature Capability: IsocFC- LDTSTOP+ CRCTM- ECTLT- 64bA- UIDRD-
        Link Frequency 1: 200MHz
        Link Error 1: <Prot- <Ovfl- <EOC- CTLTm-
        Link Frequency Capability 1: 200MHz- 300MHz- 400MHz- 500MHz- 600MHz- 800MHz- 1.0GHz- 1.2GHz- 1.4GHz- 1.6GHz- Vend-
        Error Handling: PFlE- OFlE- PFE- OFE- EOCFE- RFE- CRCFE- SERRFE- CF- RE- PNFE- ONFE- EOCNFE- RNFE- CRCNFE- SERRNFE-
        Prefetchable memory behind bridge Upper: 00-00
        Bus Number: 00
    Capabilities: [54] HyperTransport: UnitID Clumping
    Capabilities: [40] HyperTransport: Retry Mode
    Capabilities: [9c] HyperTransport: #1a
    Capabilities: [f8] HyperTransport: #1c

00:01.0 PCI bridge [0604]: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx) [1043:9602] (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe900000-feafffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device [1043:8388]
    Kernel modules: shpchp

00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606] (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity+ SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Express (v2) Root Port (Slot+), MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag+ RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #3, Speed 5GT/s, Width x1, ASPM L0s L1, Latency L0 <64ns, L1 <1us
            ClockPM- Surprise- LLActRep+ BwNot+
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt-
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
            Slot #6, PowerLimit 25.000W; Interlock- NoCompl+
        SltCtl:    Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
            Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
            Changed: MRL- PresDet+ LinkState+
        RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
        RootCap: CRSVisible-
        RootSta: PME ReqID 0000, PMEStatus- PMEPending-
        DevCap2: Completion Timeout: Not Supported, TimeoutDis- ARIFwd-
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- ARIFwd-
        LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -6dB
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Address: fee0300c  Data: 4141
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device [1043:8388]
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110 v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
            Status:    NegoPending- InProgress-
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device [1043:8389]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 22
    Region 0: I/O ports at c000 [size=8]
    Region 1: I/O ports at b000 [size=4]
    Region 2: I/O ports at a000 [size=8]
    Region 3: I/O ports at 9000 [size=4]
    Region 4: I/O ports at 8000 [size=16]
    Region 5: Memory at fe8ffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [60] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [70] SATA HBA v1.0 InCfgSpace
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:8389]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fe8fe000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.1 USB Controller [0c03]: ATI Technologies Inc SB7x0 USB OHCI1 Controller [1002:4398] (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:8389]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fe8fd000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:8389]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 17
    Region 0: Memory at fe8ff800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Bridge: PM- B3+
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:8389]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at fe8fc000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller [0c03]: ATI Technologies Inc SB7x0 USB OHCI1 Controller [1002:4398] (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:8389]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at fe8fb000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:8389]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 19
    Region 0: Memory at fe8ff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Bridge: PM- B3+
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3c)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:8389]
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort+ <MAbort- >SERR- <PERR- INTx-
    Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
    Kernel modules: i2c-piix4

00:14.1 IDE interface [0101]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c] (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device [1043:8389]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 16
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at ff00 [size=16]
    Capabilities: [70] MSI: Enable- Count=1/1 Maskable- 64bit-
        Address: 00000000  Data: 0000
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
    Subsystem: ASUSTeK Computer Inc. Device [1043:840c]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin ? routed to IRQ 16
    Region 0: Memory at fe8f4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
    Subsystem: ASUSTeK Computer Inc. Device [1043:8389]
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
    I/O behind bridge: 0000f000-00000fff
    Memory behind bridge: fff00000-000fffff
    Prefetchable memory behind bridge: fff00000-000fffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity+ SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

00:14.5 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399] (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device [1043:8389]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin C routed to IRQ 18
    Region 0: Memory at fe8fa000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Capabilities: [80] HyperTransport: Host or Secondary Interface
        Command: WarmRst+ DblEnd- DevNum=0 ChainSide- HostHide+ Slave- <EOCErr- DUL-
        Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn+ ExtCTL- 64b-
        Link Config: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn-
        Revision ID: 3.00
        Link Frequency: [b]
        Link Error: <Prot- <Ovfl- <EOC- CTLTm-
        Link Frequency Capability: 200MHz+ 300MHz- 400MHz+ 500MHz- 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz+ 1.4GHz- 1.6GHz- Vend-
        Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA+ UIDRD- ExtRS- UCnfE-

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc 760G [Radeon 3000] [1002:9616] (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device [1043:8388]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Region 1: I/O ports at d000 [size=256]
    Region 2: Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]
    Region 5: Memory at fe900000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Kernel driver in use: radeon
    Kernel modules: radeon

02:00.0 Ethernet controller [0200]: Atheros Communications AR8131 Gigabit Ethernet [1969:1063] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:83fe]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 41
    Region 0: Memory at febc0000 (64-bit, non-prefetchable) [size=256K]
    Region 2: I/O ports at ec00 [size=128]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee0100c  Data: 4169
    Capabilities: [58] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 4096 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag- AttnBtn+ AttnInd+ PwrInd+ RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 unlimited, L1 unlimited
            ClockPM+ Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [6c] Vital Product Data
        Not readable
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt+ UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP- SDES+ TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 14, GenCap+ CGenEn- ChkCap+ ChkEn-
    Capabilities: [180 v1] Device Serial Number ff-28-6e-bd-20-cf-30-ff
    Kernel driver in use: atl1c
    Kernel modules: atl1c



root@dlnas:~# lsusb -v
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.35-28-server ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:14.5
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        2 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.35-28-server ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:13.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        2 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.35-28-server ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:13.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        2 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.35-28-server ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:12.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        2 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.35-28-server ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:12.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        2 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.35-28-server ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:13.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 003: ID 05dc:a793 Lexar Media, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x05dc Lexar Media, Inc.
  idProduct          0xa793 
  bcdDevice           11.00
  iManufacturer           1 Lexar
  iProduct                2 USB Flash Drive
  iSerial                 3 365NWVHRE2ZO2H7TDDTP
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 002: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x058f Alcor Micro Corp.
  idProduct          0x6387 Transcend JetFlash Flash Drive
  bcdDevice            1.03
  iManufacturer           1 Generic
  iProduct                2 Mass Storage
  iSerial                 3 483F3178
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.35-28-server ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:12.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0503 highspeed power enable connect
   Port 2: 0000.0100 power
   Port 3: 0000.0503 highspeed power enable connect
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled



root@dlnas:~# lshw
dlnas
    description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=20BAECDE-3E99-DF11-949C-20CF30286EBD
  *-core
       description: Motherboard
       product: M4A78LT-M-LE
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev X.0x
       serial: 106361360000925
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0704
          date: 06/11/2010
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) II X2 235e Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) II X2 235e Processor
          serial: To Be Filled By O.E.M.
          slot: AM3
          size: 2700MHz
          capacity: 2700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=2 enabledcores=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS880 PCI to PCI bridge (int gfx)
             vendor: ASUSTeK Computer Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:d000(size=4096) memory:fe900000-feafffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: 760G [Radeon 3000]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:18 memory:d0000000-dfffffff ioport:d000(size=256) memory:feaf0000-feafffff memory:fe900000-fe9fffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 2)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:feb00000-febfffff
           *-network
                description: Ethernet interface
                product: AR8131 Gigabit Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: c0
                serial: 20:cf:30:28:6e:bd
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A ip=192.168.0.200 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:41 memory:febc0000-febfffff ioport:ec00(size=128)
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             logical name: scsi3
             logical name: scsi4
             logical name: scsi5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:c000(size=8) ioport:b000(size=4) ioport:a000(size=8) ioport:9000(size=4) ioport:8000(size=16) memory:fe8ffc00-fe8fffff
           *-disk:0
                description: ATA Disk
                product: ST2000DL003-9VT1
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sdc
                version: CC32
                serial: 5YD11MAJ
                size: 1863GiB (2TB)
                configuration: ansiversion=5
           *-disk:1
                description: ATA Disk
                product: WDC WD20EARS-00J
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdd
                version: 80.0
                serial: WD-WCAYY0084167
                size: 1863GiB (2TB)
                configuration: ansiversion=5 signature=0005b491
           *-disk:2
                description: ATA Disk
                product: ST31500341AS
                vendor: Seagate
                physical id: 2
                bus info: scsi@2:0.0.0
                logical name: /dev/sde
                version: CC1H
                serial: 9VS1B96Q
                size: 1397GiB (1500GB)
                configuration: ansiversion=5 signature=d64b0614
           *-disk:3
                description: ATA Disk
                product: WDC WD20EARS-00M
                vendor: Western Digital
                physical id: 3
                bus info: scsi@3:0.0.0
                logical name: /dev/sdf
                version: 50.0
                serial: WD-WMAZA0525490
                size: 1863GiB (2TB)
                configuration: ansiversion=5
           *-disk:4
                description: ATA Disk
                product: WDC WD20EARS-00M
                vendor: Western Digital
                physical id: 4
                bus info: scsi@4:0.0.0
                logical name: /dev/sdg
                version: 51.0
                serial: WD-WMAZA0766360
                size: 1863GiB (2TB)
                configuration: ansiversion=5 signature=e933fd2a
           *-disk:5
                description: ATA Disk
                product: WDC WD20EARS-00M
                vendor: Western Digital
                physical id: 5
                bus info: scsi@5:0.0.0
                logical name: /dev/sdh
                version: 51.0
                serial: WD-WCAZA1451296
                size: 1863GiB (2TB)
                configuration: ansiversion=5
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fe8fe000-fe8fefff
        *-usb:1
             description: USB Controller
             product: SB7x0 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fe8fd000-fe8fdfff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fe8ff800-fe8ff8ff
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe8fc000-fe8fcfff
        *-usb:4
             description: USB Controller
             product: SB7x0 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe8fb000-fe8fbfff
        *-usb:5
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:fe8ff400-fe8ff4ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi6
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM GSA-H55N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@6:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.05
                serial: [
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:fe8f4000-fe8f7fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-usb:6
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe8fa000-fe8fafff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          bus info: usb@1:3
          logical name: scsi9
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@9:0.0.0
             logical name: /dev/sda
             size: 14GiB (16GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=c3072e18
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@9:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: 290e3c87-4889-4f21-b19e-9167a7a5e3f2
                size: 13GiB
                capacity: 13GiB
                capabilities: primary bootable multi journaled extended_attributes large_files recover ext3 ext2 initialized
                configuration: created=2010-11-20 15:18:56 filesystem=ext3 label=sys modified=2011-06-04 08:38:50 mounted=2011-09-11 14:41:36 state=clean
           *-volume:1
                description: Linux raid autodetect partition
                physical id: 2
                bus info: scsi@9:0.0.0,2
                logical name: /dev/sda2
                capacity: 487MiB
                capabilities: primary multi
     *-scsi:1
          physical id: 2
          bus info: usb@1:1
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdb
             size: 14GiB (15GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=362a2304
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@8:0.0.0,1
                logical name: /dev/sdb1
                version: 1.0
                serial: 290e3c87-4889-4f21-b19e-9167a7a5e3f2
                size: 13GiB
                capacity: 13GiB
                capabilities: primary bootable multi journaled extended_attributes large_files recover ext3 ext2 initialized
                configuration: created=2010-11-20 15:18:56 filesystem=ext3 label=sys modified=2011-06-04 08:38:50 mounted=2011-09-11 14:41:36 state=clean
           *-volume:1
                description: Linux raid autodetect partition
                physical id: 2
                bus info: scsi@8:0.0.0,2
                logical name: /dev/sdb2
                capacity: 488MiB
                capabilities: primary multi


```

Also in case you need to know what is install I ran
```
aptitude search '?installed?not(?automatic)' > ~/packages.txt

which gives

Using username "root".
i   apt-transport-https             - APT https transport                       
i   aptitude                        - terminal-based package manager (terminal i
i   at                              - Delayed job execution and batch processing
i   bash                            - The GNU Bourne Again SHell                
i   busybox-static                  - Standalone rescue shell with tons of built
i   byobu                           - a set of useful profiles and a profile-swi
i   bzip2                           - high-quality block-sorting file compressor
i   command-not-found               - Suggest installation of packages in intera
i   command-not-found-data          - Set of data files for command-not-found.  
i   console-setup                   - console font and keymap setup program     
i   console-terminus                - Fixed-width fonts for fast reading on the 
i   cpufreqd                        - fully configurable daemon for dynamic freq
i   cpufrequtils                    - utilities to deal with the cpufreq Linux k
i   dhcp3-client                    - ISC DHCP server (transitional package)    
i   dhcp3-common                    - ISC DHCP common files (transitional packag
i   dmidecode                       - Dump Desktop Management Interface data    
i   dosfstools                      - utilities for making and checking MS-DOS F
i   dstat                           - versatile resource statistics tool        
i   ed                              - The classic UNIX line editor              
i   eject                           - ejects CDs and operates CD-Changers under 
i   friendly-recovery               - Make recovery more user-friendly          
i   ftp                             - The FTP client                            
i   gawk                            - GNU awk, a pattern scanning and processing
i   hdparm                          - tune hard disk parameters for high perform
i   info                            - Standalone GNU Info documentation browser 
i   iotop                           - simple top-like I/O monitor               
i   iproute                         - networking and traffic control tools      
i   iputils-ping                    - Tools to test the reachability of network 
i   iputils-tracepath               - Tools to trace the network path to a remot
i   irqbalance                      - Daemon to balance interrupts for SMP syste
i   kbd                             - Linux console font and keytable utilities 
i   less                            - pager program similar to more             
i   linux-server                    - Complete Linux kernel on Server Equipment.
i   lockfile-progs                  - Programs for locking and unlocking files a
i   lshw                            - information about hardware configuration  
i   lsof                            - List open files                           
i   ltrace                          - Tracks runtime library calls in dynamicall
i   lynx                            - Text-mode WWW Browser (transitional packag
i   lzma                            - Compression method of 7z format in 7-Zip p
i   man-db                          - on-line manual pager                      
i   manpages                        - Manual pages about using a GNU/Linux syste
i   mdadm                           - tool to administer Linux MD arrays (softwa
i   memtest86+                      - thorough real-mode memory tester          
i   nano                            - small, friendly text editor inspired by Pi
i   ntfs-3g                         - read-write NTFS driver for FUSE           
i   ntpdate                         - client for setting system time from NTP se
i   parted                          - The GNU Parted disk partition resizing pro
i   pciutils                        - Linux PCI Utilities                       
i   popularity-contest              - Vote for your favourite packages automatic
i   powermgmt-base                  - Common utils and configs for power managem
i   rsync                           - fast remote file copy program (like rcp)  
i   rsyslog                         - enhanced multi-threaded syslogd           
i   samba                           - SMB/CIFS file, print, and login server for
i   screen                          - terminal multiplexor with VT100/ANSI termi
i   smartmontools                   - control and monitor storage systems using 
i   sqlite3                         - A command line interface for SQLite 3     
i   ssh                             - secure shell client and server (metapackag
i   strace                          - A system call tracer                      
i   sudo                            - Provide limited super user privileges to s
i   telnet                          - The telnet client                         
i   time                            - The GNU time program for measuring cpu res
i   update-manager-core             - manage release upgrades                   
i   usbutils                        - Linux USB utilities                       
i   vim-common                      - Vi IMproved - Common files                
i   vim-tiny                        - Vi IMproved - enhanced vi editor - compact
i   webmin                          - web-based administration interface for Uni
i   wget                            - retrieves files from the web              
i   whiptail                        - Displays user-friendly dialog boxes from s
i   zfs-fuse                        - ZFS on FUSE                               

```

---

### Post by BeowulfNode on 2011-09-13
an update on so far, I've done a couple of things
- changed the /dev/md0 and /dev/md1 to only have 2 active disks each and updated /etc/mdadm/mdadm.conf to match.

- Another thing I did was a downgrade of kernel from 2.6.38.11 to 2.6.38.8, like the LiveCD that I tested, and it came back with a downgrade log of
```
dpkg: warning: downgrading linux-server from 2.6.38.11.26 to 2.6.38.8.22.
(Reading database ... 41148 files and directories currently installed.)
Preparing to replace linux-server 2.6.38.11.26 (using .../linux-server_2.6.38.8.22_amd64.deb) ...
Unpacking replacement linux-server ...
Selecting previously deselected package linux-image-2.6.38-8-server.
Unpacking linux-image-2.6.38-8-server (from .../linux-image-2.6.38-8-server_2.6.38-8.42_amd64.deb) ...
Done.
dpkg: warning: downgrading linux-image-server from 2.6.38.11.26 to 2.6.38.8.22.
Preparing to replace linux-image-server 2.6.38.11.26 (using .../linux-image-server_2.6.38.8.22_amd64.deb) ...
Unpacking replacement linux-image-server ...
(Reading database ... 44976 files and directories currently installed.)
Removing linux-image-2.6.38-11-server ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.38-11-server /boot/vmlinuz-2.6.38-11-server
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.38-11-server /boot/vmlinuz-2.6.38-11-server
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-server
Found linux image: /boot/vmlinuz-2.6.35-28-server
Found initrd image: /boot/initrd.img-2.6.35-28-server
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 11.04 (11.04) on /dev/sda1
Found Ubuntu 11.04 (11.04) on /dev/sdb1
done
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img
 you may need to re-run your boot loader[grub]
Selecting previously deselected package binutils.
(Reading database ... 41147 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.21.0.20110327-2ubuntu3_amd64.deb) ...
Selecting previously deselected package libdw1.
Unpacking libdw1 (from .../libdw1_0.148-1ubuntu1_amd64.deb) ...
Selecting previously deselected package linux-tools-common.
Unpacking linux-tools-common (from .../linux-tools-common_2.6.38-11.48_all.deb) ...
Selecting previously deselected package linux-tools-2.6.38-8.
Unpacking linux-tools-2.6.38-8 (from .../linux-tools-2.6.38-8_2.6.38-8.42_amd64.deb) ...
Selecting previously deselected package linux-tools.
Unpacking linux-tools (from .../linux-tools_2.6.38.8.22_amd64.deb) ...
Processing triggers for man-db ...
Setting up linux-image-2.6.38-8-server (2.6.38-8.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-8-server
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-8-server /boot/vmlinuz-2.6.38-8-server
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-8-server /boot/vmlinuz-2.6.38-8-server
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-server
Found initrd image: /boot/initrd.img-2.6.38-8-server
Found linux image: /boot/vmlinuz-2.6.35-28-server
Found initrd image: /boot/initrd.img-2.6.35-28-server
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 11.04 (11.04) on /dev/sda1
Found Ubuntu 11.04 (11.04) on /dev/sdb1
done
Setting up linux-image-server (2.6.38.8.22) ...
Setting up linux-server (2.6.38.8.22) ...
Setting up binutils (2.21.0.20110327-2ubuntu3) ...
Setting up libdw1 (0.148-1ubuntu1) ...
Setting up linux-tools-common (2.6.38-11.48) ...
Setting up linux-tools-2.6.38-8 (2.6.38-8.42) ...
Setting up linux-tools (2.6.38.8.22) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Press return to continue.

```I'm rather concerned about the lines that say
```
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img
 you may need to re-run your boot loader[grub]
```so I ran
fsck -fv /dev/md0
from a LiveCD, which found data in the journal even though it was marked as clean.

however none of that changed the result

after a bit more investigating I found out that it hadn't frozen **it  was stuck at the initramfs prompt after failing to mount the root file  system with a complaint about an invalid argument.**

The way I found this out was in the grub menu press 'e' and change the line that says
```
set gfxpayload=$linux_gfx_mode
to
set gfxpayload=text
```how do I check what command is being used for mounting /dev/md0 the root filesystem? and how do I correct it?

---

### Post by BeowulfNode on 2011-09-17
I'm starting to think this is a similar problem to
[http://ubuntuforums.org/showthread.php?t=1763854](http://ubuntuforums.org/showthread.php?t=1763854)
where upon upgrading to 11.04 a new array md127 with partition 1 /dev/md127p1 takes up raid devices preventing the regular array from assembling.  However I have the additional problem of the error occurring with my all in 1 root and boot partition '/'.

I'm not sure how to log the full startup log when it crashes before /var/log is available.  When I get to the initramfs prompt I can see
```
Begin: Running /scripts/local-premount ... done.
EXT3-fs (md127p1): recovery required on read only filesystem
EXT3-fs (md127p1): write access will be enabled during recovery
EXT3-fs: barriers not enabled
attempt to access beyond end of device
md127p1: rw=0, want 14159888, limit 1625984
JBD: IO error reading journal superblock
mounting /dev/disk/by-uuid/290e3c87-4889-4f21-b19e-9167a7a5e3f2 on /root
failed: Invalid argument
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... mount: mounting /dev on /root/dev failed: No such file or directory
done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No Init found. Try passing init= bootarg.

Busybox v1.17.1 (ubuntu........ etc etc) built in shell (ash)
Enter 'help' etc etc

(initramfs)

```
I should mention that there should only be md0 and md1 which contain no partitions. md0 is ext3 and contains the root filesystem.  md1 is formatted as swap, but I'm not using it at the moment.  When I boot in to 2.6.35 kernel this is how it appears.  But when trying to boot the 2.6.38 series md127p1 appears.

Anyone with any ideas?

---

### Post by BeowulfNode on 2011-10-15
still no responses :(

well I thought I was making some progress in that the few lines of text before it dumped me to an initramfs prompt were saying it could not mount the root file system.

at the initramfs prompt I could mount the root file system by doing
```
mdadm --stop /dev/md127p1
mdadm --stop /dev/md0
mdadm --assemble --no-degraded --scan
mount /dev/md0 /root
```so this seems to confirm that it is an issue with the mdadm config in the initrd image.  So I rebooted in to the previous linux kernel 2.6.35 and ran
update-initramfs -u
and tried to boot the new kernel, but this did not help

so after getting back in to the old kernel I tried running
update-initramfs -u -k 2.6.38-11-server
and again tried rebooting in to the new kernel, but that didn't work either.

so I tried running
update-initramfs -u -k all
dpkg-reconfigure grub-pc
and tried booting the new kernel and gain it did not work.

Now though I have a more annoying problem in that the previous kernel option no longer works as its initrd image has been updated with the new mdadm that reads the raid config wrong.

so now I'm really annoyed as any changes have to be made from a LiveCD unless I can continue the boot process from the initramfs prompt after I manually mount the root file system.  Any ideas on how to do this?

I tried running
./init 3
but it complains saying
mounting none on /sys failed. device or resource busy
mounting none on /proc failed. device or resource busy
... some other stuff ...
... can't mount /dev/disk/by-uuid/bunch_of_hex on /root device or resource busy ...
running /scripts/init-bottom....done.
Failed to connect to socket /com/ubuntu/upstart Connection refused.

---

### Post by BeowulfNode on 2011-10-15
well after 4 weeks of nobody helping, I finally figured out how to make it go.

I noticed at the initramfs prompt after running
mdadm --stop /dev/md127p1
mdadm --stop /dev/md0
that running
mdadm --examine --scan
would list md0 and md1

the 2 USB sticks used to have a 2nd partition on each which used to be an mdadm raid1 in addition to the 1st partitions on each that is the root folder.  These 2nd partitions used to be md1.  I had deleted the partitions, which as many linux people know does not delete the actual data it just deletes the references to the data.

However somehow mdadm was finding those 2nd partitions and getting itself confused over what to do with them, when it should have not seen them and done nothing about them!!

So in a LiveCD I finially hit apon the idea of writting over those areas of the drive with a new partition in another format like ext2.

HOORAY!!!!!!!!!!!!!! I fixed it!!!!!!!!!!!!!!!

Now I'm just left with the annoyance that the entire kernel loading process is a black screen until it starts running user level daemons like samba, zfs-fuse, etc, for the new kernel.


_**Solution Summary**_
0) if you can't see anything, use the 'e' button from the grub menu to change the line
set gfxpayload=$linux_gfx_mode
to
set gfxpayload=text
so you can actually see what is happening.

1) ensure /etc/mdadm/mdadm.conf is correct, particularly the lines starting with ARRAY, and leave off as much optional detail as you can
eg. ARRAY /dev/md0 UUID=166d6ae4:4eacea87:61d5599c:c7ed6bd3
no name or other stuff, just
ARRAY dev UUID=blah:blah:blah:blah

2) ensure that no drive has the remnants of any other mdadm raid

3) run
update-initramfs -u
if your problem kernel is the latest one, or if that doesn't work be more specific with the k switch, eg.
update-initramfs -u -k 2.6.38-11-server

4) run
dpkg-reconfigure grub-pc
and follow the prompts

---

