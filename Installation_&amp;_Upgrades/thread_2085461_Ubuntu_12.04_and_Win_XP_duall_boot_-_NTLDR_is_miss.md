---
title: "Ubuntu 12.04 and Win XP duall boot - NTLDR is missing"
date: 2012-11-18
forum: Installation &amp; Upgrades
---

### Post by Dimco on 2012-11-18
[FONT=DejaVu Sans, sans-serif]Hi,[/FONT]
 [FONT=DejaVu Sans, sans-serif]I have this problem for few days now.[/FONT]
 [FONT=DejaVu Sans, sans-serif]Sorry if the problem sounds worn out.[/FONT]
 [FONT=DejaVu Sans, sans-serif]I have prowling through number of forums attempting to solve the problem to no avail.[/FONT]
 [FONT=DejaVu Sans, sans-serif]I am running dual boot machine with Ubuntu 12.04 and Win XP Pro. Both partitions are on the same HDD. I am having secondary HDD that is primarily used for storage/archiving. The secondary HDD in the past used to run  Win XP only.[/FONT]
 

 [FONT=DejaVu Sans, sans-serif]When I select Windows XP professional from the Grub2 menu I am getting the “NTLDR is missing....press Ctrl-Alt-Del to Restart” error.[/FONT]
 [FONT=DejaVu Sans, sans-serif]I have attempted the follwing:[/FONT]
 
[LIST=1]
[*][FONT=DejaVu Sans, sans-serif]Copying 	the  [/FONT][FONT=DejaVu Sans, sans-serif]NTDLR[/FONT][FONT=DejaVu Sans, sans-serif], 	[/FONT][FONT=DejaVu Sans, sans-serif]NTDETECT.COM 	files from  Windows XP CD-ROM to the partition where Win XP 	Professional is installed[/FONT]
[*][FONT=DejaVu Sans, sans-serif]Have 	run Recovery Console from the Windows XP startup disks or the 	Windows XP CD-ROM issuing the following commands:[/FONT]
 	 	[FONT=DejaVu Sans, sans-serif]FIXBOOT 	C:
BOOTCFG /rebuild 
chkdsk c: /r[/FONT]
 	 	[FONT=DejaVu Sans, sans-serif]After 	which the BOOT.INI file still maintains its original modified date [/FONT] 	
[/LIST]
 

```
[boot loader] 
 timeout=30 
 default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
 [operating systems] 
 multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer

```

 
[LIST=1]
[*][FONT=DejaVu Sans, sans-serif]I 	have re-installed Grub2 in case something has been corrupted. This 	is my  Boot Info Summary[/FONT]
[/LIST]
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 27084d1f-d6d1-42bf-b5bc-83cab8de8549 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /NTLDR /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 686483766 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive.
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   467,900,943   467,900,881   7 NTFS / exFAT / HPFS
/dev/sda2         467,902,462   976,773,119   508,870,658   5 Extended
/dev/sda5         467,909,190   960,156,854   492,247,665  83 Linux
/dev/sda6         960,167,936   976,773,119    16,605,184  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   153,179,774   153,179,712   7 NTFS / exFAT / HPFS
/dev/sdb2         153,179,775   156,296,384     3,116,610   f W95 Extended (LBA)
/dev/sdb5         153,179,838   156,296,384     3,116,547   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        059991FB7853B77D                       ntfs       
/dev/sda5        27084d1f-d6d1-42bf-b5bc-83cab8de8549   ext4       
/dev/sda6        33e38495-337a-4c4a-aa23-b020504bd78e   swap       
/dev/sdb1        E648B89448B86549                       ntfs       
/dev/sdb5        0D08-09EE                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 
--------------------------------------------------------------------------------

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
set default="Microsoft Windows XP Professional (on /dev/sda1)"
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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
  set locale_dir=($root)/boot/grub/locale
  set lang=en_AU
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-33-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    linux    /boot/vmlinuz-3.2.0-33-generic-pae root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-33-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-33-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    echo    'Loading Linux 3.2.0-33-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-33-generic-pae root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-33-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    linux    /boot/vmlinuz-3.2.0-33-generic root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-33-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    echo    'Loading Linux 3.2.0-33-generic ...'
    linux    /boot/vmlinuz-3.2.0-33-generic root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-33-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    linux    /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-32-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    echo    'Loading Linux 3.2.0-32-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-32-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    linux    /boot/vmlinuz-3.2.0-32-generic root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-32-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    echo    'Loading Linux 3.2.0-32-generic ...'
    linux    /boot/vmlinuz-3.2.0-32-generic root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-32-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-31-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    linux    /boot/vmlinuz-3.2.0-31-generic-pae root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-31-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-31-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    echo    'Loading Linux 3.2.0-31-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-31-generic-pae root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-31-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    linux    /boot/vmlinuz-3.2.0-31-generic root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-31-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    echo    'Loading Linux 3.2.0-31-generic ...'
    linux    /boot/vmlinuz-3.2.0-31-generic root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-31-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    linux    /boot/vmlinuz-3.2.0-30-generic-pae root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-30-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    echo    'Loading Linux 3.2.0-30-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-30-generic-pae root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-30-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    linux    /boot/vmlinuz-3.2.0-30-generic root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-30-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    echo    'Loading Linux 3.2.0-30-generic ...'
    linux    /boot/vmlinuz-3.2.0-30-generic root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-30-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    echo    'Loading Linux 3.2.0-29-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 27084d1f-d6d1-42bf-b5bc-83cab8de8549
    echo    'Loading Linux 3.2.0-29-generic ...'
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-29-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 059991FB7853B77D
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
# / was on /dev/sda5 during installation
UUID=27084d1f-d6d1-42bf-b5bc-83cab8de8549 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=33e38495-337a-4c4a-aa23-b020504bd78e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 297.333842278 = 319.259782144  boot/grub/core.img                             1
 285.264010429 = 306.299898880  boot/grub/grub.cfg                             1
 270.396876335 = 290.336435200  boot/initrd.img-3.2.0-29-generic               2
 259.152903557 = 278.263311360  boot/initrd.img-3.2.0-29-generic-pae           3
 274.410964012 = 294.646529024  boot/initrd.img-3.2.0-30-generic               3
 270.371638298 = 290.309336064  boot/initrd.img-3.2.0-30-generic-pae           2
 269.230547905 = 289.084099584  boot/initrd.img-3.2.0-31-generic               2
 267.155303001 = 286.855822336  boot/initrd.img-3.2.0-31-generic-pae           3
 281.022738457 = 301.745867776  boot/initrd.img-3.2.0-32-generic               2
 277.157149315 = 297.595223040  boot/initrd.img-3.2.0-32-generic-pae           3
 282.003493309 = 302.798945280  boot/initrd.img-3.2.0-33-generic               2
 282.019633293 = 302.816275456  boot/initrd.img-3.2.0-33-generic-pae           3
 276.456950188 = 296.843389952  boot/vmlinuz-3.2.0-29-generic                  1
 276.519595146 = 296.910654464  boot/vmlinuz-3.2.0-29-generic-pae              1
 277.652266502 = 298.126851072  boot/vmlinuz-3.2.0-30-generic                  1
 277.711001396 = 298.189917184  boot/vmlinuz-3.2.0-30-generic-pae              1
 266.660079002 = 286.324079616  boot/vmlinuz-3.2.0-31-generic                  1
 266.898501396 = 286.580083712  boot/vmlinuz-3.2.0-31-generic-pae              2
 277.804610252 = 298.290428928  boot/vmlinuz-3.2.0-32-generic                  2
 277.914130211 = 298.408025088  boot/vmlinuz-3.2.0-32-generic-pae              1
 281.785079002 = 302.564424704  boot/vmlinuz-3.2.0-33-generic                  1
 281.847723961 = 302.631689216  boot/vmlinuz-3.2.0-33-generic-pae              1
 282.019633293 = 302.816275456  initrd.img                                     3
 282.003493309 = 302.798945280  initrd.img.old                                 2
 281.847723961 = 302.631689216  vmlinuz                                        1
 281.785079002 = 302.564424704  vmlinuz.old                                    1

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Windows XP Professional" /Fastdetect 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="1" 1 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\="Previous Operating System on C:"  
--------------------------------------------------------------------------------

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt



```


 [FONT=DejaVu Sans, sans-serif]So far noting has worked to let me log to WinXP using Grub2.[/FONT]
 

 [FONT=DejaVu Sans, sans-serif]I have MultiSystem Live USB. One of the Options I have available is “Grub4Dos”. If I select this option it opens another screen with number of options one of which is “Find and load NTLDR of Windows NT/2K/XP”. Selecting this options I can log into my Win XP installation without any problems. [/FONT] 
 [FONT=DejaVu Sans, sans-serif]Is it possible that Grub2 points to boot.ini in secondary HDD (sdb) that does not have the NTLDR file, subsequently causing the  error.? If so how can I foprce Grub2 to point to boot,ini file in sda?[/FONT]
 

 [FONT=DejaVu Sans, sans-serif]I would appreciate if someone could point me to a solution.[/FONT]
 

 [FONT=DejaVu Sans, sans-serif]Many thanks,[/FONT]

---

