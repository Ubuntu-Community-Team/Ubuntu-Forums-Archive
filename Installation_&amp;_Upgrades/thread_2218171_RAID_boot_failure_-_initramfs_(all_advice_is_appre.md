---
title: "RAID: boot failure - initramfs (all advice is appreciated)"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by rollyah on 2014-04-19
I have a system with 9 disks that represent a couple of raid 10 arrays
the two raid arrays degraded and caused a boot failure (one of them was the main "/" partition)

i plugged a 10th disk and installed ubuntu 12.04 LTS over it. 
now when i reboot,it passes grub successfully and then it stalls on /dev/sdm and /dev/sdn and then falls back to initramfs

i rebooted into livecd, and commented everything in fstab except the new disk (" /" and swap) 
though rebooting keeps going into initramfs

it's worth to note that if i physically disconnect all other drives, the system boots normally with the same exact config

with the help of "bootinfoscript" i managed to find the below information.
any advice on how to troubleshoot this issue, would be greatly appreciated

 [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)



                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sdd.
 => No known boot loader is installed in the MBR of /dev/sdf.
 => No known boot loader is installed in the MBR of /dev/sdg.
 => No known boot loader is installed in the MBR of /dev/sdh.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdi and looks at sector 34 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (mduuid/345c489c63e34d58c1c1a2ac8ff8a6b6)/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdj and looks at sector 34 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (mduuid/345c489c63e34d58c1c1a2ac8ff8a6b6)/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdl and looks at sector 34 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt2)/grub on this drive.

sdd1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdf1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdf2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdg1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdg2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdh1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdh2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdi1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sdi2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdi3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info: 

sdi4: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdj1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sdj2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdj3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info: 

sdj4: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdl1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sdl2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdl3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdl4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /etc/fstab

sda: ___________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdb: ___________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdc: ___________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdk: ___________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdm: ___________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdn: ___________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdd1           2,048 2,639,306,751 2,639,304,704 Data partition (Windows/Linux)

Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1               2,048        34,815        32,768   7 NTFS / exFAT / HPFS
/dev/sdf2              34,816 3,907,024,895 3,906,990,080   7 NTFS / exFAT / HPFS


Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1               2,048        34,815        32,768   7 NTFS / exFAT / HPFS
/dev/sdg2              34,816 3,907,024,895 3,906,990,080   7 NTFS / exFAT / HPFS


Drive: sdh _____________________________________________________________________

Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdh1               2,048        34,815        32,768   7 NTFS / exFAT / HPFS
/dev/sdh2              34,816 3,907,024,895 3,906,990,080   7 NTFS / exFAT / HPFS


Drive: sdi _____________________________________________________________________

Disk /dev/sdi: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdi1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdi1              34         1,987         1,954 BIOS Boot partition
/dev/sdi2           1,988       587,925       585,938 RAID partition (Linux)
/dev/sdi3         587,926   293,556,676   292,968,751 RAID partition (Linux)
/dev/sdi4     293,556,677 2,639,307,646 2,345,750,970 RAID partition (Linux)

Drive: sdj _____________________________________________________________________

Disk /dev/sdj: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdj1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdj1              34         1,987         1,954 BIOS Boot partition
/dev/sdj2           1,988       587,925       585,938 RAID partition (Linux)
/dev/sdj3         587,926   293,556,676   292,968,751 RAID partition (Linux)
/dev/sdj4     293,556,677 2,639,307,646 2,345,750,970 RAID partition (Linux)

Drive: sdl _____________________________________________________________________

Disk /dev/sdl: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdl1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdl1              34         1,987         1,954 BIOS Boot partition
/dev/sdl2           1,988       587,925       585,938 Data partition (Windows/Linux)
/dev/sdl3         587,926    31,837,926    31,250,001 Swap partition (Linux)
/dev/sdl4      31,837,927 2,639,307,646 2,607,469,720 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda         97bc8b41-7e94-cd23-9711-40e37f678210   linux_raid_member dam:3
/dev/sdb         97bc8b41-7e94-cd23-9711-40e37f678210   linux_raid_member dam:3
/dev/sdc         6d9f8ebe-164e-c09f-c845-e08f8499e99c   linux_raid_member ams:2
/dev/sdf1        1E06443406440F69                       ntfs       mia_HD01
/dev/sdg1        189A640A9A63E32C                       ntfs       mia_HD02
/dev/sdh1        B09CB4979CB45A14                       ntfs       mia_HD03
/dev/sdi2        345c489c-63e3-4d58-c1c1-a2ac8ff8a6b6   linux_raid_member ams:0
/dev/sdi3        cbbd6bfa-0b94-1536-cfa5-9cdb802f0733   linux_raid_member ams:1
/dev/sdi4        6d9f8ebe-164e-c09f-c845-e08f8499e99c   linux_raid_member ams:2
/dev/sdj2        345c489c-63e3-4d58-c1c1-a2ac8ff8a6b6   linux_raid_member ams:0
/dev/sdj3        cbbd6bfa-0b94-1536-cfa5-9cdb802f0733   linux_raid_member ams:1
/dev/sdj4        6d9f8ebe-164e-c09f-c845-e08f8499e99c   linux_raid_member ams:2
/dev/sdk         6d9f8ebe-164e-c09f-c845-e08f8499e99c   linux_raid_member ams:2
/dev/sdl2        ddd47847-9399-4265-8c63-f9cd74d201d3   ext4       
/dev/sdl3        6b6bf336-9e71-458a-9b16-6009b8e744d8   swap       
/dev/sdl4        2a171660-f5cf-40ab-8044-da3cb57bf1e9   ext4       
/dev/sdm         97bc8b41-7e94-cd23-9711-40e37f678210   linux_raid_member dam:3
/dev/sdn         97bc8b41-7e94-cd23-9711-40e37f678210   linux_raid_member dam:3
/dev/sr0                                                iso9660    Ubuntu 14.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdf1        /media/ubuntu/mia_HD01 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdg1        /media/ubuntu/mia_HD02 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdh1        /media/ubuntu/mia_HD03 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


============================= sdl2/grub/grub.cfg: ==============================

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

insmod part_gpt
insmod ext2
set root='(hd0,gpt4)'
search --no-floppy --fs-uuid --set=root 2a171660-f5cf-40ab-8044-da3cb57bf1e9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt2)'
  search --no-floppy --fs-uuid --set=root ddd47847-9399-4265-8c63-f9cd74d201d3
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
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
function gfxmode {
  set gfxpayload="$1"
  if [ "$1" = "keep" ]; then
    set vt_handoff=vt.handoff=7
  else
    set vt_handoff=
  fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
  recordfail
  gfxmode $linux_gfx_mode
  insmod gzio
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt2)'
  search --no-floppy --fs-uuid --set=root ddd47847-9399-4265-8c63-f9cd74d201d3
  linux /vmlinuz-3.2.0-23-generic root=UUID=2a171660-f5cf-40ab-8044-da3cb57bf1e9 ro   
  initrd  /initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
  recordfail
  insmod gzio
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt2)'
  search --no-floppy --fs-uuid --set=root ddd47847-9399-4265-8c63-f9cd74d201d3
  echo  'Loading Linux 3.2.0-23-generic ...'
  linux /vmlinuz-3.2.0-23-generic root=UUID=2a171660-f5cf-40ab-8044-da3cb57bf1e9 ro recovery nomodeset 
  echo  'Loading initial ramdisk ...'
  initrd  /initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt2)'
  search --no-floppy --fs-uuid --set=root ddd47847-9399-4265-8c63-f9cd74d201d3
  linux16 /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt2)'
  search --no-floppy --fs-uuid --set=root ddd47847-9399-4265-8c63-f9cd74d201d3
  linux16 /memtest86+.bin console=ttyS0,115200n8
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

=================== sdl2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== sdl4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=2a171660-f5cf-40ab-8044-da3cb57bf1e9 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=ddd47847-9399-4265-8c63-f9cd74d201d3 /boot           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=6b6bf336-9e71-458a-9b16-6009b8e744d8 none            swap    sw              0       0

# /dev/md126 added by mario - old grub probably
#UUID=79a513a8-d101-4097-a72a-fc82ec00ef6e /mnt/oldgrub              ext4    defaults         0        2

# /dev/md127 added by mario   - this is extra
#UUID=1440cb56-fa9e-4c50-8fa6-b88c254095b9 /mnt/storage/extra/       ext4    defaults         0       2  
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdf

00000000  45 52 02 00 00 0a 3f b1  00 00 00 00 00 00 00 00  |ER....?.........|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 31 43 6c 6b  27 e8 9d c2 bd 2a 00 20  |....1Clk'....*. |
000001c0  21 00 07 2a 28 02 00 08  00 00 00 80 00 00 00 2a  |!..*(..........*|
000001d0  29 02 07 fe ff ff 00 88  00 00 00 f0 df e8 00 00  |)...............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown MBR on /dev/sdg

00000000  45 52 02 00 00 0a 3e eb  00 00 00 00 00 00 00 00  |ER....>.........|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 31 43 6c 6b  52 64 79 24 00 00 00 20  |....1ClkRdy$... |
000001c0  21 00 07 2a 28 02 00 08  00 00 00 80 00 00 00 2a  |!..*(..........*|
000001d0  29 02 07 fe ff ff 00 88  00 00 00 f0 df e8 00 00  |)...............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown MBR on /dev/sdh

00000000  45 52 02 00 00 0a 3f b1  00 00 00 00 00 00 00 00  |ER....?.........|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 31 43 6c 6b  52 64 79 24 00 00 00 20  |....1ClkRdy$... |
000001c0  21 00 07 2a 28 02 00 08  00 00 00 80 00 00 00 2a  |!..*(..........*|
000001d0  29 02 07 fe ff ff 00 88  00 00 00 f0 df e8 00 00  |)...............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdf2

00000000  58 36 ed 38 47 0b 4e eb  e5 d5 a2 c7 90 22 a1 0c  |X6.8G.N......"..|
00000010  a0 42 b7 19 12 f7 03 11  c1 74 10 5a 4a 04 2c 58  |.B.......t.ZJ.,X|
00000020  5d 2b 73 1c 57 2e 7d 1a  ec 45 91 10 ac 11 a4 72  |]+s.W.}..E.....r|
00000030  0f 39 63 eb 78 a8 de 1b  56 99 70 c7 10 af 10 94  |.9c.x...V.p.....|
00000040  85 58 1b ea 99 a7 5d f2  73 26 57 7c 24 19 d8 92  |.X....].s&W|$...|
00000050  7b b4 01 e1 1a 0f e4 18  d6 70 4c 66 06 47 20 15  |{........pLf.G .|
00000060  f7 b0 c7 c7 bd fe 76 a5  fe 62 a8 a6 79 ad ce c1  |......v..b..y...|
00000070  19 f5 4e d7 e3 3b 86 82  7d 53 49 ca 04 ce 0a e6  |..N..;..}SI.....|
00000080  71 aa d2 9d f3 48 7b f2  37 0f 80 09 0a fe a0 3c  |q....H{.7......<|
00000090  34 ec fd a6 47 81 df 44  ed d9 23 00 0f 30 28 59  |4...G..D..#..0(Y|
000000a0  ac 67 33 c2 63 af 6b cc  91 7f 62 d2 b4 d7 6d 24  |.g3.c.k...b...m$|
000000b0  04 17 23 26 fe a6 12 c8  99 9d 71 49 e9 84 22 4d  |..#&......qI.."M|
000000c0  df f3 18 90 94 5a 08 79  54 a7 4f 07 ca 00 d8 05  |.....Z.yT.O.....|
000000d0  dc da 64 ce 1d fb e3 2d  5a 44 8d c0 e1 47 68 c6  |..d....-ZD...Gh.|
000000e0  10 28 b5 6f ba dc 6c 53  ef 14 16 cd bf b1 47 a3  |.(.o..lS......G.|
000000f0  b3 a2 f2 92 9b 9d 72 f4  b4 69 a4 7a e6 fc f2 52  |......r..i.z...R|
00000100  b7 e7 d7 ed eb 85 b5 4d  95 ab 41 7e a2 77 84 c9  |.......M..A~.w..|
00000110  56 7f 0c 8b b5 4a 70 33  b5 3b aa bf 24 3a fe 37  |V....Jp3.;..$:.7|
00000120  a4 8f 6a 5b 8a 21 f4 9e  41 7e 87 fe a9 0f 3b 8b  |..j[.!..A~....;.|
00000130  85 2c 32 73 5f cc e7 35  40 28 d6 8c e1 0c 8f 17  |.,2s_..5@(......|
00000140  af 62 ae 7c 02 ae c3 51  d6 67 79 d6 21 9d a3 27  |.b.|...Q.gy.!..'|
00000150  fc a0 f3 7e 93 0f c0 9d  52 26 3c 44 6c 54 b0 f0  |...~....R&<DlT..|
00000160  68 7c 89 e2 d2 37 a3 fd  bd bb 03 05 da 68 1c 08  |h|...7.......h..|
00000170  05 9c da 7f 6d e6 eb 15  8c 80 37 b1 f8 39 3f 3d  |....m.....7..9?=|
00000180  0d 06 ec 26 ed 46 ad 3d  0e 99 b4 a2 b9 a1 8b 3e  |...&.F.=.......>|
00000190  19 38 75 ea 46 2d a3 fb  2d 48 40 83 9b e7 33 9a  |.8u.F-..-H@...3.|
000001a0  ea 0a 25 e1 5c a1 c3 2b  a7 55 72 fe 14 a2 ba 4f  |..%.\..+.Ur....O|
000001b0  a3 0e 54 55 ac 9c 88 11  d8 2e ed 90 cb d7 41 27  |..TU..........A'|
000001c0  b8 73 11 ca 2d 0a d3 15  6e f6 7d 13 ff 1e 3b ab  |.s..-...n.}...;.|
000001d0  fc 8f c6 6e 04 79 81 d7  1d 01 49 b3 9d 8d a7 be  |...n.y....I.....|
000001e0  00 e3 d7 f1 fd 19 eb f0  05 47 29 5b 7a c5 46 f9  |.........G)[z.F.|
000001f0  c6 21 81 7c 1f 4e 76 c6  d6 94 21 be 2d 9e 02 18  |.!.|.Nv...!.-...|
00000200

Unknown BootLoader on sdg2

00000000  4d de 6e 00 e2 ce b1 b3  57 a7 eb 64 3b ff 0f 17  |M.n.....W..d;...|
00000010  32 34 b8 d2 84 da bd 93  70 6b 71 8b 52 b7 29 a6  |24......pkq.R.).|
00000020  c0 ad d8 fe 57 81 07 ad  b1 97 11 78 03 ba da 2f  |....W......x.../|
00000030  43 9d 5f 7d 06 05 49 09  5d 3a 3f 6d a7 24 9f 91  |C._}..I.]:?m.$..|
00000040  bc b4 fc 75 e5 01 6e bf  17 c2 a3 95 29 74 c4 db  |...u..n.....)t..|
00000050  a4 61 94 2f 8c e5 f1 36  83 20 9a 6e 43 5f 8b 5e  |.a./...6. .nC_.^|
00000060  5c 0c c8 26 92 76 92 8b  77 ae 1a 73 62 ef 15 0c  |\..&.v..w..sb...|
00000070  bf a6 2a ab f5 ec ae c6  aa 78 0d 9c 42 05 ce b9  |..*......x..B...|
00000080  ba fa 28 55 44 75 7f ad  9d 44 9a a0 78 3f 0f ff  |..(UDu...D..x?..|
00000090  f9 15 11 d9 ed 24 3c 90  7d f5 b1 7b e5 ea 5e c3  |.....$<.}..{..^.|
000000a0  b0 cf 27 cb ba db 8d ea  fb a3 ef 57 10 8a fc a9  |..'........W....|
000000b0  ed 5f f0 81 c5 fa 83 60  d5 34 2b 4f 66 e7 e0 ff  |._.....`.4+Of...|
000000c0  ae 84 65 23 51 bf 8e 57  7f 4a ba 44 b3 92 bd 51  |..e#Q..W.J.D...Q|
000000d0  cb 66 59 ec c5 c0 c5 33  1e 20 4d 81 5f 31 e7 74  |.fY....3. M._1.t|
000000e0  dd 59 51 8f 11 08 fa 3c  dc d8 1c cf 2e b9 e6 68  |.YQ....<.......h|
000000f0  9c 57 98 6d ba c1 f7 e5  05 bc 55 d7 1e 25 e4 bf  |.W.m......U..%..|
00000100  aa 29 8e bf 33 04 c9 49  e9 39 2d d2 05 5c e0 21  |.)..3..I.9-..\.!|
00000110  0f 73 5e 15 fc 5d a1 55  b9 81 2b 51 92 7e 7c 83  |.s^..].U..+Q.~|.|
00000120  9d 10 ef 42 df 1c 67 be  50 d5 82 c9 70 28 33 5d  |...B..g.P...p(3]|
00000130  e0 fc 41 43 62 c3 f5 7d  a7 d4 f0 8b a8 0d e3 a8  |..ACb..}........|
00000140  a2 97 88 2b c3 ab e4 2a  93 b5 50 f2 c3 b9 5d f4  |...+...*..P...].|
00000150  f4 8f 13 9e cb 7a 7d 7b  c8 8c 07 16 1d c9 0f da  |.....z}{........|
00000160  44 46 65 93 14 99 2a a4  0a 74 1e c0 7a 48 39 4d  |DFe...*..t..zH9M|
00000170  1f 73 b7 02 6d 7c 04 90  e9 79 01 1c 88 d6 e0 bb  |.s..m|...y......|
00000180  72 25 fa 5d 45 96 ef f1  0f d0 d5 7a ee 1d b0 55  |r%.]E......z...U|
00000190  27 b9 ff a8 54 cb 9e ac  78 6f 87 5f c8 29 25 40  |'...T...xo._.)%@|
000001a0  db d9 45 5f d2 d4 d2 61  d4 de 93 41 70 d0 48 1d  |..E_...a...Ap.H.|
000001b0  2c 55 eb 59 76 dd 41 8b  9c 3e e3 3f aa 04 fd 56  |,U.Yv.A..>.?...V|
000001c0  ed 6d 05 c1 ed e2 67 e1  da 54 65 8a f6 61 58 16  |.m....g..Te..aX.|
000001d0  5e c6 a1 e3 5a 4e d9 39  6c 71 d2 0f 17 6f 03 85  |^...ZN.9lq...o..|
000001e0  51 6e 5b 7b 0e a8 79 b5  71 0a dd f6 ad 61 cf 12  |Qn[{..y.q....a..|
000001f0  3b 63 7a 5d b4 49 ad f5  f5 8f 00 44 40 4e 2d e2  |;cz].I.....D@N-.|
00000200

Unknown BootLoader on sdh2

00000000  a4 d5 c2 98 a3 51 f0 2f  99 79 72 ff 45 5b 51 7d  |.....Q./.yr.E[Q}|
00000010  11 1e f9 4a 32 3a d9 f6  22 03 9d c0 44 ca 5b ba  |...J2:.."...D.[.|
00000020  e6 c0 a9 66 c4 e7 9d 73  64 0f ab 61 c4 05 cd 69  |...f...sd..a...i|
00000030  81 29 f4 04 06 26 c7 5b  cf f3 ac ee d6 f0 85 79  |.)...&.[.......y|
00000040  c9 86 c2 19 a1 d7 a7 32  be 30 b0 3d 88 55 a6 3d  |.......2.0.=.U.=|
00000050  ff aa 88 e3 c4 1b 93 53  91 83 74 96 05 04 3e d9  |.......S..t...>.|
00000060  53 81 34 5b 45 51 e7 0d  86 49 7d 4a fc c8 4e 32  |S.4[EQ...I}J..N2|
00000070  5d a9 79 33 a0 c1 cc 93  bd 13 99 40 a2 fc 34 1d  |].y3.......@..4.|
00000080  1e a8 76 0e 3e 98 1a e0  cf e9 27 76 04 73 d1 c1  |..v.>.....'v.s..|
00000090  2b 6b 33 a0 8a 1e 5d 2b  b1 49 48 3f 62 3f e6 08  |+k3...]+.IH?b?..|
000000a0  02 d1 4a a5 f2 e6 85 25  3b d9 c0 5b 8d a2 5a ec  |..J....%;..[..Z.|
000000b0  1f ec 6e 1d 3d b8 70 b4  81 e8 8b 28 13 e4 4f 62  |..n.=.p....(..Ob|
000000c0  35 a4 74 1d 6d cf 66 05  9e e5 d0 93 4b 11 5b 0e  |5.t.m.f.....K.[.|
000000d0  04 f4 37 14 6d 68 4c 65  67 41 86 4e ce 48 7e e7  |..7.mhLegA.N.H~.|
000000e0  3f b6 56 c5 aa 8f 3b 66  9f 43 f0 7c 60 5e 2c a0  |?.V...;f.C.|`^,.|
000000f0  57 4f b9 14 37 b7 20 38  6c 5e be cd b2 1e 5c 35  |WO..7. 8l^....\5|
00000100  38 ed 4b bd f4 2a 71 a5  bd 46 3a b5 a3 7a ea 5d  |8.K..*q..F:..z.]|
00000110  2c c5 ac 65 01 18 85 00  a4 f7 48 c3 51 44 e1 f5  |,..e......H.QD..|
00000120  44 fd 6f b7 02 7d be 1e  4b 16 09 16 50 9e 94 1d  |D.o..}..K...P...|
00000130  67 01 90 2f 68 c7 16 95  7f 38 2f d3 43 a3 ad 41  |g../h....8/.C..A|
00000140  9e ad 03 a5 14 c0 de 16  5e 8c 3d 9b 26 be 40 ff  |........^.=.&.@.|
00000150  a5 79 38 01 35 fe ea 63  6e 71 80 f2 45 90 3c 4f  |.y8.5..cnq..E.<O|
00000160  c1 1c f7 33 70 c4 53 96  85 8b 9d 2b 82 7b cd 41  |...3p.S....+.{.A|
00000170  c2 6b e7 2c ac 1d 36 c7  0f 60 f1 a9 71 88 0d ab  |.k.,..6..`..q...|
00000180  4b 78 93 26 77 37 df 0d  38 79 1a a7 3d bc c1 b6  |Kx.&w7..8y..=...|
00000190  70 bd 2d 3f e1 21 f7 76  7f d9 5f ec 2a 9e ff 2b  |p.-?.!.v.._.*..+|
000001a0  2a e5 99 29 28 ed e1 2b  43 0c 54 46 62 01 80 08  |*..)(..+C.TFb...|
000001b0  59 84 83 f7 5d 64 3d 7b  6b 4e e8 8b 06 b4 11 78  |Y...]d={kN.....x|
000001c0  62 ef 3f eb fd fb e1 8d  55 56 33 b8 95 fd 33 bc  |b.?.....UV3...3.|
000001d0  65 3b 78 ed c9 e4 c2 4c  4d 70 a4 9a 16 37 b6 55  |e;x....LMp...7.U|
000001e0  3b 34 fb a1 ed b4 5c 52  00 25 8a e9 44 f5 bb e8  |;4....\R.%..D...|
000001f0  43 c2 ce f5 ad 00 2f a9  13 a9 ec 13 0e 40 a2 9e  |C...../......@..|
00000200

Unknown BootLoader on sdi3

00000000  44 65 75 74 73 63 68 20  28 4d 61 63 69 6e 74 6f  |Deutsch (Macinto|
00000010  73 68 2c 20 6f 68 6e 65  20 41 6b 7a 65 6e 74 74  |sh, ohne Akzentt|
00000020  61 73 74 65 6e 29 0a 64  65 2a 76 61 72 69 61 6e  |asten).de*varian|
00000030  74 2a 64 65 2a 64 73 62  2a 44 65 75 74 73 63 68  |t*de*dsb*Deutsch|
00000040  20 2d 20 4e 69 65 64 65  72 73 6f 72 62 69 73 63  | - Niedersorbisc|
00000050  68 0a 64 65 2a 76 61 72  69 61 6e 74 2a 64 65 2a  |h.de*variant*de*|
00000060  72 6f 5f 6e 6f 64 65 61  64 6b 65 79 73 2a 44 65  |ro_nodeadkeys*De|
00000070  75 74 73 63 68 20 2d 20  52 75 6d c3 a4 6e 69 73  |utsch - Rum..nis|
00000080  63 68 20 28 44 65 75 74  73 63 68 6c 61 6e 64 2c  |ch (Deutschland,|
00000090  20 6f 68 6e 65 20 41 6b  7a 65 6e 74 74 61 73 74  | ohne Akzenttast|
000000a0  65 6e 29 0a 64 65 2a 76  61 72 69 61 6e 74 2a 64  |en).de*variant*d|
000000b0  65 2a 72 6f 2a 44 65 75  74 73 63 68 20 2d 20 52  |e*ro*Deutsch - R|
000000c0  75 6d c3 a4 6e 69 73 63  68 20 28 44 65 75 74 73  |um..nisch (Deuts|
000000d0  63 68 6c 61 6e 64 29 0a  64 65 2a 76 61 72 69 61  |chland).de*varia|
000000e0  6e 74 2a 64 65 2a 64 76  6f 72 61 6b 2a 44 65 75  |nt*de*dvorak*Deu|
000000f0  74 73 63 68 20 2d 20 44  65 75 74 73 63 68 20 28  |tsch - Deutsch (|
00000100  44 76 6f 72 61 6b 29 0a  64 65 2a 76 61 72 69 61  |Dvorak).de*varia|
00000110  6e 74 2a 64 65 2a 64 73  62 5f 71 77 65 72 74 7a  |nt*de*dsb_qwertz|
00000120  2a 44 65 75 74 73 63 68  20 2d 20 4e 69 65 64 65  |*Deutsch - Niede|
00000130  72 73 6f 72 62 69 73 63  68 20 28 71 77 65 72 74  |rsorbisch (qwert|
00000140  7a 29 0a 64 65 2a 76 61  72 69 61 6e 74 2a 64 65  |z).de*variant*de|
00000150  2a 6e 65 6f 2a 44 65 75  74 73 63 68 20 2d 20 44  |*neo*Deutsch - D|
00000160  65 75 74 73 63 68 20 28  4e 65 6f 20 32 29 0a 64  |eutsch (Neo 2).d|
00000170  65 2a 6c 61 79 6f 75 74  2a 72 6f 2a 52 75 6d c3  |e*layout*ro*Rum.|
00000180  a4 6e 69 73 63 68 0a 64  65 2a 76 61 72 69 61 6e  |.nisch.de*varian|
00000190  74 2a 72 6f 2a 2a 52 75  6d c3 a4 6e 69 73 63 68  |t*ro**Rum..nisch|
000001a0  0a 64 65 2a 76 61 72 69  61 6e 74 2a 72 6f 2a 77  |.de*variant*ro*w|
000001b0  69 6e 6b 65 79 73 2a 52  75 6d c3 a4 6e 69 73 63  |inkeys*Rum..nisc|
000001c0  68 20 2d 20 52 75 6d c3  a4 6e 69 73 63 68 20 28  |h - Rum..nisch (|
000001d0  57 69 6e 64 6f 77 73 2d  54 61 73 74 65 6e 29 0a  |Windows-Tasten).|
000001e0  64 65 2a 76 61 72 69 61  6e 74 2a 72 6f 2a 73 74  |de*variant*ro*st|
000001f0  64 5f 63 65 64 69 6c 6c  61 2a 52 75 6d c3 a4 6e  |d_cedilla*Rum..n|
00000200

Unknown BootLoader on sdj3

00000000  44 65 75 74 73 63 68 20  28 4d 61 63 69 6e 74 6f  |Deutsch (Macinto|
00000010  73 68 2c 20 6f 68 6e 65  20 41 6b 7a 65 6e 74 74  |sh, ohne Akzentt|
00000020  61 73 74 65 6e 29 0a 64  65 2a 76 61 72 69 61 6e  |asten).de*varian|
00000030  74 2a 64 65 2a 64 73 62  2a 44 65 75 74 73 63 68  |t*de*dsb*Deutsch|
00000040  20 2d 20 4e 69 65 64 65  72 73 6f 72 62 69 73 63  | - Niedersorbisc|
00000050  68 0a 64 65 2a 76 61 72  69 61 6e 74 2a 64 65 2a  |h.de*variant*de*|
00000060  72 6f 5f 6e 6f 64 65 61  64 6b 65 79 73 2a 44 65  |ro_nodeadkeys*De|
00000070  75 74 73 63 68 20 2d 20  52 75 6d c3 a4 6e 69 73  |utsch - Rum..nis|
00000080  63 68 20 28 44 65 75 74  73 63 68 6c 61 6e 64 2c  |ch (Deutschland,|
00000090  20 6f 68 6e 65 20 41 6b  7a 65 6e 74 74 61 73 74  | ohne Akzenttast|
000000a0  65 6e 29 0a 64 65 2a 76  61 72 69 61 6e 74 2a 64  |en).de*variant*d|
000000b0  65 2a 72 6f 2a 44 65 75  74 73 63 68 20 2d 20 52  |e*ro*Deutsch - R|
000000c0  75 6d c3 a4 6e 69 73 63  68 20 28 44 65 75 74 73  |um..nisch (Deuts|
000000d0  63 68 6c 61 6e 64 29 0a  64 65 2a 76 61 72 69 61  |chland).de*varia|
000000e0  6e 74 2a 64 65 2a 64 76  6f 72 61 6b 2a 44 65 75  |nt*de*dvorak*Deu|
000000f0  74 73 63 68 20 2d 20 44  65 75 74 73 63 68 20 28  |tsch - Deutsch (|
00000100  44 76 6f 72 61 6b 29 0a  64 65 2a 76 61 72 69 61  |Dvorak).de*varia|
00000110  6e 74 2a 64 65 2a 64 73  62 5f 71 77 65 72 74 7a  |nt*de*dsb_qwertz|
00000120  2a 44 65 75 74 73 63 68  20 2d 20 4e 69 65 64 65  |*Deutsch - Niede|
00000130  72 73 6f 72 62 69 73 63  68 20 28 71 77 65 72 74  |rsorbisch (qwert|
00000140  7a 29 0a 64 65 2a 76 61  72 69 61 6e 74 2a 64 65  |z).de*variant*de|
00000150  2a 6e 65 6f 2a 44 65 75  74 73 63 68 20 2d 20 44  |*neo*Deutsch - D|
00000160  65 75 74 73 63 68 20 28  4e 65 6f 20 32 29 0a 64  |eutsch (Neo 2).d|
00000170  65 2a 6c 61 79 6f 75 74  2a 72 6f 2a 52 75 6d c3  |e*layout*ro*Rum.|
00000180  a4 6e 69 73 63 68 0a 64  65 2a 76 61 72 69 61 6e  |.nisch.de*varian|
00000190  74 2a 72 6f 2a 2a 52 75  6d c3 a4 6e 69 73 63 68  |t*ro**Rum..nisch|
000001a0  0a 64 65 2a 76 61 72 69  61 6e 74 2a 72 6f 2a 77  |.de*variant*ro*w|
000001b0  69 6e 6b 65 79 73 2a 52  75 6d c3 a4 6e 69 73 63  |inkeys*Rum..nisc|
000001c0  68 20 2d 20 52 75 6d c3  a4 6e 69 73 63 68 20 28  |h - Rum..nisch (|
000001d0  57 69 6e 64 6f 77 73 2d  54 61 73 74 65 6e 29 0a  |Windows-Tasten).|
000001e0  64 65 2a 76 61 72 69 61  6e 74 2a 72 6f 2a 73 74  |de*variant*ro*st|
000001f0  64 5f 63 65 64 69 6c 6c  61 2a 52 75 6d c3 a4 6e  |d_cedilla*Rum..n|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sde 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
cat: /tmp/BootInfo-J8mClc9i/Tmp_Log: No such file or directory
  No volume groups found
mdadm: Devices UUID-6d9f8ebe:164ec09f:c845e08f:8499e99c and UUID-6d9f8ebe:164ec09f:c845e08f:8499e99c have the same name: /dev/md/2
mdadm: Duplicate MD device names in conf file were found.

---

