---
title: "Fresh 9.10 install and Grub error 15"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by madhartigan on 2009-10-18
I'm trying to install 9.10 on my system and now I'm getting grub error 15.

I'll try to provide every bit of information that I think may be helpful.



I used the Ubuntu 9.10 alternate install disk.

When partitioning, I did the following:

sda is a 320GB drive in RAID 1 with sdd and should have /var on it

sdb is a 1TB drive in RAID 0 with sde and should have /home on it

sdc is the bootable drive that I had automatically partitioned when using the alternate install disk.


Here's the contents of /boot/grub/ (which oddly has no menu.lst file in it):

```

ubuntu@ubuntu:/media/disk/boot/grub$ ls
915resolution.mod  efiemu64.o     lspci.mod       reiserfs.mod
acpi.mod           efiemu.mod     lvm.mod         scsi.mod
affs.mod           elf.mod        mdraid.mod      search.mod
afs_be.mod         ext2.mod       memdisk.mod     serial.mod
afs.mod            extcmd.mod     memrw.mod       setjmp.mod
aout.mod           fat.mod        minicmd.mod     sfs.mod
ata.mod            font.mod       minix.mod       sh.mod
ata_pthru.mod      fs_file.mod    mmap.mod        sleep.mod
at_keyboard.mod    fshelp.mod     moddep.lst      tar.mod
befs_be.mod        fs.lst         msdospart.mod   terminfo.mod
befs.mod           fs_uuid.mod    multiboot.mod   test.mod
biosdisk.mod       gfxterm.mod    normal.mod      tga.mod
bitmap.mod         gptsync.mod    ntfscomp.mod    true.mod
blocklist.mod      grub.cfg       ntfs.mod        udf.mod
boot.img           grubenv        ohci.mod        ufs1.mod
boot.mod           gzio.mod       part_acorn.mod  ufs2.mod
bsd.mod            halt.mod       part_amiga.mod  uhci.mod
bufio.mod          handler.lst    part_apple.mod  usb_keyboard.mod
cat.mod            handler.mod    part_gpt.mod    usb.mod
cdboot.img         hdparm.mod     partmap.lst     usbms.mod
chain.mod          hello.mod      part_msdos.mod  usbtest.mod
cmp.mod            help.mod       part_sun.mod    vbeinfo.mod
command.lst        hexdump.mod    parttool.lst    vbe.mod
configfile.mod     hfs.mod        parttool.mod    vbetest.mod
core.img           hfsplus.mod    password.mod    vga.mod
cpio.mod           iso9660.mod    pci.mod         vga_text.mod
cpuid.mod          jfs.mod        play.mod        video_fb.mod
crc.mod            jpeg.mod       png.mod         video.mod
datehook.mod       kernel.img     probe.mod       videotest.mod
date.mod           keystatus.mod  pxeboot.img     xfs.mod
datetime.mod       linux16.mod    pxecmd.mod      xnu.mod
device.map         linux.mod      pxe.mod         xnu_uuid.mod
diskboot.img       lnxboot.img    raid5rec.mod    zfsinfo.mod
dm_nv.mod          loadenv.mod    raid6rec.mod    zfs.mod
drivemap.mod       loopback.mod   raid.mod
echo.mod           lsmmap.mod     read.mod
efiemu32.o         ls.mod         reboot.mod

```

Here's fdisk -lu:

```
ubuntu@ubuntu:/media/disk/boot/grub$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bdb37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625137344   312568641   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cf677

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003b2cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   139203224    69601581   83  Linux
/dev/sdc2       139203225   145211534     3004155    5  Extended
/dev/sdc5       139203288   145211534     3004123+  82  Linux swap / Solaris

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ea669

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   625137344   312568641   fd  Linux raid autodetect

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000072a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  1953520064   976760001   fd  Linux raid autodetect

```

Here's df, in case that's of any help:

```
ubuntu@ubuntu:/media/disk/boot/grub$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                  4041508      2760   4038748   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                  4041508      2760   4038748   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                  4041508         0   4041508   0% /lib/init/rw
varrun                 4041508       104   4041404   1% /var/run
varlock                4041508         0   4041508   0% /var/lock
udev                   4041508       176   4041332   1% /dev
tmpfs                  4041508      1656   4039852   1% /dev/shm
rootfs                 4041508     32932   4008576   1% /
/dev/sr0                713432    713432         0 100% /cdrom
/dev/loop0              689280    689280         0 100% /rofs
tmpfs                  4041508        12   4041496   1% /tmp
/dev/sdc1             68507476   2234048  62793352   4% /media/disk

```


Here's the results of using the boot info script:

```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       mdraid
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'mdraid'

sdb1: _________________________________________________________________________

    File system:       mdraid
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'mdraid'

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu karmic (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdd1: _________________________________________________________________________

    File system:       mdraid
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'mdraid'

sde1: _________________________________________________________________________

    File system:       mdraid
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'mdraid'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bdb37

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,137,344   625,137,282  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cf677

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003b2cc

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   139,203,224   139,203,162  83 Linux
/dev/sdc2         139,203,225   145,211,534     6,008,310   5 Extended
/dev/sdc5         139,203,288   145,211,534     6,008,247  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ea669

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   625,137,344   625,137,282  fd Linux raid autodetect


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000072a3

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63 1,953,520,064 1,953,520,002  fd Linux raid autodetect


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="7350c3d5-9157-63db-f569-c4eb4d494fba" TYPE="mdraid" 
/dev/sdb1: UUID="8be737e2-b410-b43c-c4cf-e7dc9e0feb67" TYPE="mdraid" 
/dev/sdc1: UUID="e7956f6c-4b15-4060-90f2-d6aa021ccf58" TYPE="ext4" 
/dev/sdd1: UUID="7350c3d5-9157-63db-f569-c4eb4d494fba" TYPE="mdraid" 
/dev/sde1: UUID="8be737e2-b410-b43c-c4cf-e7dc9e0feb67" TYPE="mdraid" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/disk type ext4 (rw,nosuid,nodev,uhelper=hal)


=========================== sdc1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd2,1)
search --no-floppy --fs-uuid --set e7956f6c-4b15-4060-90f2-d6aa021ccf58
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set e7956f6c-4b15-4060-90f2-d6aa021ccf58
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=e7956f6c-4b15-4060-90f2-d6aa021ccf58 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set e7956f6c-4b15-4060-90f2-d6aa021ccf58
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=e7956f6c-4b15-4060-90f2-d6aa021ccf58 ro single 
	initrd	/boot/initrd.img-2.6.31-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=e7956f6c-4b15-4060-90f2-d6aa021ccf58 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
#UUID=a78fa400-c7d1-4fa9-b57e-79ceacfabb8c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0

=================== sdc1: Location of files loaded by Grub: ===================


   4.0GB: boot/grub/grub.cfg
   4.1GB: boot/initrd.img-2.6.31-11-generic
   2.3GB: boot/vmlinuz-2.6.31-11-generic
   4.1GB: initrd.img
   2.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 10 8e d0 bc 00  b0 b8 00 00 8e d8 8e c0  |.c..............|
00000010  fb be 00 7c bf 00 06 b9  00 02 f3 a4 ea 21 06 00  |...|.........!..|
00000020  00 be be 07 38 04 75 0b  83 c6 10 81 fe fe 07 75  |....8.u........u|
00000030  f3 eb 16 b4 02 b0 01 bb  00 7c b2 80 8a 74 01 8b  |.........|...t..|
00000040  4c 02 cd 13 ea 00 7c 00  00 eb fe 00 00 00 00 00  |L.....|.........|
00000050  00 00 00 00 00 00 00 00  00 00 00 80 01 00 00 00  |................|
00000060  00 00 00 00 ff fa eb 07  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  be 88 7d e8 24 01 be 05  ||<.t...R..}.$...|
00000090  7c f6 c2 80 74 48 b4 41  bb aa 55 cd 13 5a 52 72  ||...tH.A..U..ZRr|
000000a0  3d 81 fb 55 aa 75 37 83  e1 01 74 32 31 c0 89 44  |=..U.u7...t21..D|
000000b0  04 40 88 44 ff 89 44 02  c7 04 10 00 66 8b 1e 5c  |.@.D..D.....f..\|
000000c0  7c 66 89 5c 08 66 8b 1e  60 7c 66 89 5c 0c c7 44  ||f.\.f..`|f.\..D|
000000d0  06 00 70 b4 42 cd 13 72  05 bb 00 70 eb 73 b4 08  |..p.B..r...p.s..|
000000e0  cd 13 73 0a f6 c2 80 0f  84 d8 00 e9 82 00 66 0f  |..s...........f.|
000000f0  b6 c6 88 64 ff 40 66 89  44 04 0f b6 d1 c1 e2 02  |...d.@f.D.......|
00000100  88 e8 88 f4 40 89 44 08  0f b6 c2 c0 e8 02 66 89  |....@.D.......f.|
00000110  04 66 a1 60 7c 66 09 c0  75 4e 66 a1 5c 7c 66 31  |.f.`|f..uNf.\|f1|
00000120  d2 66 f7 34 88 d1 31 d2  66 f7 74 04 3b 44 08 7d  |.f.4..1.f.t.;D.}|
00000130  37 fe c1 88 c5 30 c0 c1  e8 02 08 c1 88 d0 5a 88  |7....0........Z.|
00000140  c6 bb 00 70 8e c3 31 db  b8 01 02 cd 13 72 29 8c  |...p..1......r).|
00000150  c3 60 1e b9 00 01 8e db  31 f6 bf 00 80 8e c6 fc  |.`......1.......|
00000160  f3 a5 1f 61 ff 26 5a 7c  be 8e 7d e8 44 00 eb 0e  |...a.&Z|..}.D...|
00000170  be 93 7d e8 3c 00 eb 06  be 9d 7d e8 34 00 be a2  |..}.<.....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  37 db 0b 00 00 00 80 01  |...<.u..7.......|
000001c0  01 00 fd fe ff ff 3f 00  00 00 82 d6 42 25 00 00  |......?.....B%..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sde1

00000000  00 00 c0 03 10 00 c0 03  20 00 c0 03 e0 5f 00 20  |........ ...._. |
00000010  00 00 05 00 00 00 00 00  00 00 00 00 00 20 b7 dc  |............. ..|
00000020  01 00 c0 03 11 00 c0 03  20 02 c0 03 00 80 00 20  |........ ...... |
00000030  00 00 07 00 00 00 00 00  00 00 00 00 00 20 ca 47  |............. .G|
00000040  02 00 c0 03 12 00 c0 03  20 04 c0 03 00 80 00 20  |........ ...... |
00000050  00 00 07 00 00 00 00 00  00 00 00 00 00 20 a4 e6  |............. ..|
00000060  03 00 c0 03 13 00 c0 03  20 06 c0 03 00 80 00 20  |........ ...... |
00000070  00 00 07 00 00 00 00 00  00 00 00 00 00 20 7f 46  |............. .F|
00000080  04 00 c0 03 14 00 c0 03  20 08 c0 03 00 80 00 20  |........ ...... |
00000090  00 00 07 00 00 00 00 00  00 00 00 00 00 20 7b e4  |............. {.|
000000a0  05 00 c0 03 15 00 c0 03  20 0a c0 03 00 80 00 20  |........ ...... |
000000b0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 a0 44  |............. .D|
000000c0  06 00 c0 03 16 00 c0 03  20 0c c0 03 00 80 00 20  |........ ...... |
000000d0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 ce e5  |............. ..|
000000e0  07 00 c0 03 17 00 c0 03  20 0e c0 03 00 80 00 20  |........ ...... |
000000f0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 15 45  |............. .E|
00000100  08 00 c0 03 18 00 c0 03  20 10 c0 03 00 80 00 20  |........ ...... |
00000110  00 00 07 00 00 00 00 00  00 00 00 00 00 20 c5 e1  |............. ..|
00000120  09 00 c0 03 19 00 c0 03  20 12 c0 03 00 80 00 20  |........ ...... |
00000130  00 00 07 00 00 00 00 00  00 00 00 00 00 20 1e 41  |............. .A|
00000140  0a 00 c0 03 1a 00 c0 03  20 14 c0 03 00 80 00 20  |........ ...... |
00000150  00 00 07 00 00 00 00 00  00 00 00 00 00 20 70 e0  |............. p.|
00000160  0b 00 c0 03 1b 00 c0 03  20 16 c0 03 00 80 00 20  |........ ...... |
00000170  00 00 07 00 00 00 00 00  00 00 00 00 00 20 ab 40  |............. .@|
00000180  0c 00 c0 03 1c 00 c0 03  20 18 c0 03 00 80 00 20  |........ ...... |
00000190  00 00 07 00 00 00 00 00  00 00 00 00 00 20 af e2  |............. ..|
000001a0  0d 00 c0 03 1d 00 c0 03  20 1a c0 03 00 80 00 20  |........ ...... |
000001b0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 74 42  |............. tB|
000001c0  0e 00 c0 03 1e 00 c0 03  20 1c c0 03 00 80 00 20  |........ ...... |
000001d0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 1a e3  |............. ..|
000001e0  0f 00 c0 03 1f 00 c0 03  20 1e c0 03 00 80 00 20  |........ ...... |
000001f0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 c1 43  |............. .C|
00000200


```


When I go into grub from the LiveCD's terminal  I get this:

```
find /boot/grub/stage1

Error 15: File not found
grub> 

```


I'm really not sure what I can do to fix this seeing that I don't even have a menu.lst file and grub can't even find stage1. Should I attempt to do a clean install of grub?  And if so, how would I do that?

I'd really appreciate some help on this if anyone has the time.

---

### Post by mechro on 2009-10-18
From 9.10 it's grub2 with a grub.cfg file.

I don't yet know anything about grub2 but while you're waiting for more replies you could research grub2.

---

### Post by Sef on 2009-10-18
Moved to Karmic Koala T & D.

---

### Post by oldfred on 2009-10-18
One link that explains grub2 and has instructions on reinstalling grub2
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

How does your raid system boot if you have nothing in the MBR of the first disk? (I know nothing about setting up raid in linux)

---

### Post by madhartigan on 2009-10-18
Thank you for the replies!!

My raid systems were just for /var and /home.

Since Grub was looking at hd2,1 for my /boot I don't think the raid arrays were of any significance to the grub error.

Because I needed to move forward, I abandoned 9.10 and went back to 9.04.

I wish i had the skills to diagnose/fix the issue but I definitely do not.

I may try to fiddle with it on a test system if i find the time.

Sorry for being a quitter.  I just needed an up and running system quickly.

I'm still gonna read through that grub2 link.

Thank you for your help, nonetheless.

---

### Post by kansasnoob on 2009-10-18
From:

Known issues @ [http://www.ubuntu.com/testing/karmic/beta](http://www.ubuntu.com/testing/karmic/beta)

As is to be expected at this stage of the release process, there are several known bugs that users are likely to run into with Ubuntu 9.10 Beta. We have documented them here for your convenience along with any known workarounds, so that you don't need to spend time reporting these bugs again:

(SKIP)

      > If a RAID partitioning scheme is used during installation the grub boot loader will only be installed on the first hard drive instead of all the drives. Booting the system if the first drive has failed will not work. As a workaround users can manually install grub to each disk in the array using the grub-install command (427048).

If you're familiar with grub legacy and wish to revert I'm writing a tutorial:

[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

---

### Post by VMC on 2009-10-18
Follow this [guide]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD") to re-install grub2 on your mbr.

---

