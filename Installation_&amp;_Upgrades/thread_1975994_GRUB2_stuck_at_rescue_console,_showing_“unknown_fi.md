---
title: "GRUB2 stuck at rescue console, showing “unknown filesystem” for all partitions"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by AndiDog on 2012-05-08
Hint: I also asked this at [http://askubuntu.com/questions/132821/grub2-stuck-at-rescue-console-showing-unknown-filesystem-for-all-partitions](http://askubuntu.com/questions/132821/grub2-stuck-at-rescue-console-showing-unknown-filesystem-for-all-partitions)

I installed Ubuntu 12.04 on my external USB drive, where I have a 700GB NTFS partition followed by the new 6GB ext4 partition and a swap partition (all primary). The GRUB MBR is also installed to the external hard disk.

Since my BIOS puts the external drive as first disk when booting, I removed my internal hard disk before installation in order to avoid ordering problems. (But even if I do the installation with the internal drive plugged in, I get the same issue.)

Now when I boot from the external drive, GRUB is stuck at the rescue console with the error "unknown filesystem".
```
    grub rescue> ls
    (hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)

    ls (hd0,<any of them>)/ gives me "unknown filesystem", thus also "insmod normal"
```GRUB doesn't seem to be able to read my Linux partition as you can see above?! How can I solve this?

Additional info:

bootinfoscript says (this is with the internal drive in again, but that does not make a difference) the following:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   312,578,047   312,371,200   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 749.5 GB, 749452918784 bytes
255 heads, 63 sectors/track, 91115 cylinders, total 1463775232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,450,459,135 1,450,457,088   7 NTFS / exFAT / HPFS
/dev/sdb2    *  1,450,459,136 1,462,796,287    12,337,152  83 Linux
/dev/sdb3       1,462,796,288 1,463,773,183       976,896  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        90D68375D6835A7C                       ntfs       System Reserved
/dev/sda2        265C854C5C8517A7                       ntfs       
/dev/sdb1        CCD44AFBD44AE6F4                       ntfs       MINI
/dev/sdb2        93775a99-72e7-4dfb-a8dc-9ca4d0a43e1f   ext4       
/dev/sdb3        0c8da017-b679-482e-918c-dff58bb0c647   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/MINI              fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb2        /media/93775a99-72e7-4dfb-a8dc-9ca4d0a43e1f ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set=root 93775a99-72e7-4dfb-a8dc-9ca4d0a43e1f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root 93775a99-72e7-4dfb-a8dc-9ca4d0a43e1f
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IE
  insmod gettext
fi
terminal_output gfxterm
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
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root 93775a99-72e7-4dfb-a8dc-9ca4d0a43e1f
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=93775a99-72e7-4dfb-a8dc-9ca4d0a43e1f ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root 93775a99-72e7-4dfb-a8dc-9ca4d0a43e1f
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=93775a99-72e7-4dfb-a8dc-9ca4d0a43e1f ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 93775a99-72e7-4dfb-a8dc-9ca4d0a43e1f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 93775a99-72e7-4dfb-a8dc-9ca4d0a43e1f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 90D68375D6835A7C
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

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=93775a99-72e7-4dfb-a8dc-9ca4d0a43e1f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=0c8da017-b679-482e-918c-dff58bb0c647 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

---

### Post by darkod on 2012-05-08
1. If you plug in the ext hdd but boot with the ubuntu cd in live mode, can you open and read the data in the root partition on the ext hdd?

2. From live mode in terminal, what does parted say about your partitions:
sudo parted /dev/sdb print all

---

### Post by AndiDog on 2012-05-08
1. Yes, it actually gets mounted automatically under /media/<uuid> and I can read all data in it, including the /boot folder.

2. Output of parted:
> 
Model: WD My Passport 070A (scsi)
Disk /dev/sdb: 749GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system     Flags
 1      1049kB  743GB  743GB   primary  ntfs
 2      743GB   749GB  6317MB  primary  ext4            boot
 3      749GB   749GB  500MB   primary  linux-swap(v1)


Model: ATA INTEL SSDSA2M160 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   160GB  160GB  primary  ntfs


Model: Optiarc DVD RW AD-7561S (scsi)
Disk /dev/sr0: 4700MB
Sector size (logical/physical): 2048B/2048B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      131kB  2929MB  2929MB  primary               boot, hiddenIt's not a problem with the offset of the /dev/sdb2 partition (@743 GB), is it?

---

### Post by darkod on 2012-05-08
It can be the offset, sometimes it doesn't want the boot files so far from the start.

But another thing can be the issue too. I just noticed that your root is barely 6GB. Why so small? On a 750GB disk you couldn't spare at least 15-20GB for root so it can breathe better?

But I'm not sure how we can check if root it too full, it doesn't say it has no space. It says unknown FS. Not sure if that message can be related to low space.

---

### Post by oldfred on 2012-05-08
Will the external boot with the internal disconnected. It refers to hd1, but the search by UUID is supposed to override that, so it should not matter if it is hd0 or hd1.

Some have had BIOS settings issues. 
IDE often is an issue, AHCI works but you need drivers installed first in Windows 7, LARGE or LBA or sometimes other terms so not IDE i.e. enabled or something. Every BIOS seems different.

Some externals do not work from the newer ports.
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs

---

### Post by AndiDog on 2012-05-08
I made it so small because the first partition contains a big TrueCrypt  file, so I can only spare around 15GB. But that shouldn't be a problem  since a fresh Ubuntu installation needs way less than 6GB.

Did I  say that "insmod ext2" works? Guess it must be included in the core  image. And still GRUB cannot list the contents of the ext4 partition.

Now  I successfully installed Ubuntu on another external hard drive where  the root partition is now at the beginning (using 50+ GB ext3 filesystem). So maybe it  was really the offset. I'd really like to find out what the problem  is...

Unfortunately my BIOS (HP 6730b laptop) does not offer any relevant choices IMO. I'm using AHCI mode.

---

### Post by AndiDog on 2012-05-09
Updated BIOS of my HP 6730b laptop to the latest version F.20 (from mid of 2011), still the same issue (tried a reinstall).

---

### Post by darkod on 2012-05-09
Don't disconnect the internal. You don't stop any ordering problems that way, because later you will have it connected and in fact that can produce ordering problems.

So, with both disks present, can you boot it manually from the grub rescue> ? If you don't know to load it manually it would be like:
```
set root=(hd0,msdos2)
linux /boot/vmlinuz-3.2.0-23-generic
initrd /boot/initrd.img-3.2.0-23-generic
boot
```

If you notice that the external is hd1, not hd0, change in the first command.

---

