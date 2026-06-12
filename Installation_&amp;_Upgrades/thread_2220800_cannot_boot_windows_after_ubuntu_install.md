---
title: "cannot boot windows after ubuntu install"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by mark1977 on 2014-04-29
Hi,

I had win 7 on one drive and just installed ubuntu 12.04 on my second drive. After the install, I do not get a grub boot menu option to boot into win 7. os-prober return nothing.
Here is the result of running the diagnostic in boot-repair:
[http://paste.ubuntu.com/7360153/](http://paste.ubuntu.com/7360153/)

Can you tell me how to get a grub menu including options for windows and ubuntu?

Thanks,

Mark

---

### Post by mark1977 on 2014-04-30
I tried to fix this by running boot-repair, and now I can't boot into any operating system, I simply get the message:

```
error:unknown file system
grub rescue

```

The latest pastebin after running boot-repair is: paste.ubuntu.com/7366724

I would really appreciate any help right now.

Thanks.

---

### Post by mark1977 on 2014-04-30
Here is the output of bootinfo script:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 599608 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grub.conf /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       194,559       192,512 EFI System partition
/dev/sda2         194,560 1,920,090,111 1,919,895,552 Data partition (Windows/Linux)
/dev/sda3   1,920,090,112 1,953,523,711    33,433,600 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,855,469,567 1,855,467,520  83 Linux
/dev/sdb2       1,855,471,614 1,894,531,071    39,059,458   5 Extended
/dev/sdb5       1,855,471,616 1,894,531,071    39,059,456  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 8103 MB, 8103395328 bytes
256 heads, 21 sectors/track, 2944 cylinders, total 15826944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63    15,826,943    15,826,881   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        5DBB-D649                              vfat       
/dev/sda2        8C6EBA1D6EB9FFCE                       ntfs       
/dev/sda3        1d70aa44-007f-4d2f-ab37-7895267201ff   swap       
/dev/sdb1        15be1a02-8fb7-4705-b945-175a7884ea61   ext4       
/dev/sdb5        19856e7b-9e1a-49ec-89bd-1715b68f9aa5   swap       
/dev/sdc1        103C-2A44                              vfat       PENDRIVE
/dev/sr0                                                iso9660    CDROM

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot/efi                vfat       (rw)
/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 15be1a02-8fb7-4705-b945-175a7884ea61
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root 15be1a02-8fb7-4705-b945-175a7884ea61
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
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
menuentry 'Ubuntu, with Linux 3.5.0-49-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 15be1a02-8fb7-4705-b945-175a7884ea61
    linux    /boot/vmlinuz-3.5.0-49-generic root=UUID=15be1a02-8fb7-4705-b945-175a7884ea61 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-49-generic
}
menuentry 'Ubuntu, with Linux 3.5.0-49-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 15be1a02-8fb7-4705-b945-175a7884ea61
    echo    'Loading Linux 3.5.0-49-generic ...'
    linux    /boot/vmlinuz-3.5.0-49-generic root=UUID=15be1a02-8fb7-4705-b945-175a7884ea61 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.5.0-49-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.5.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 15be1a02-8fb7-4705-b945-175a7884ea61
    linux    /boot/vmlinuz-3.5.0-23-generic root=UUID=15be1a02-8fb7-4705-b945-175a7884ea61 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.5.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 15be1a02-8fb7-4705-b945-175a7884ea61
    echo    'Loading Linux 3.5.0-23-generic ...'
    linux    /boot/vmlinuz-3.5.0-23-generic root=UUID=15be1a02-8fb7-4705-b945-175a7884ea61 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.5.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 5DBB-D649
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root 5DBB-D649
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=15be1a02-8fb7-4705-b945-175a7884ea61 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=5DBB-D649  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=1d70aa44-007f-4d2f-ab37-7895267201ff none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=19856e7b-9e1a-49ec-89bd-1715b68f9aa5 none            swap    sw              0       0
UUID=5DBB-D649    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 736.128433228 = 790.411886592  boot/grub/grub.cfg                             1
 735.474723816 = 789.709971456  boot/initrd.img-3.5.0-23-generic               2
  13.007793427 = 13.967011840   boot/initrd.img-3.5.0-49-generic               1
   0.404247284 = 0.434057216    boot/vmlinuz-3.5.0-23-generic                  1
 735.228469849 = 789.445558272  boot/vmlinuz-3.5.0-49-generic                  1
 735.373001099 = 789.600747520  boot/vmlinuz-3.5.0-49-generic.efi.signed       1
 735.474723816 = 789.709971456  initrd.img                                     2
 735.474723816 = 789.709971456  initrd.img.old                                 2
   0.404247284 = 0.434057216    vmlinuz                                        1

=============================== sdc1/grub.conf: ================================

--------------------------------------------------------------------------------
# This is a sample grub.conf for use with Genkernel, per the Gentoo handbook
# http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10#doc_chap2
# If you are not using Genkernel and you need help creating this file, you
# should consult the handbook. Alternatively, consult the grub.conf.sample that
# is included with the Grub documentation.

default 0
timeout 30
splashimage=(hd0,4)/grub/splash.xpm.gz

#title=Gentoo Linux (3.1.6-gentoo)
#root (hd0,4)
##kernel /kernel-genkernel-x86_64-3.1.6-gentoo real_root=/dev/sda4
#kernel /kernel-genkernel-x86_64-3.1.6-gentoo real_root=/dev/sda4
#initrd /initramfs-genkernel-x86_64-3.1.6-gentoo

title Gentoo Linux Mark2 (based on 3.1.6)
root (hd0,4)
kernel /kernel-Mark2-gentoo real_root=/dev/sda4 ro video=vesafb vga=0x0361 init=/sbin/bootchartd
initrd /initramfs-genkernel-x86_64-3.1.6-gentoo

title Windows 7
rootnoverify (hd0,0)
makeactive
chainloader +1


title Sabayon (guess)
root (hd0,6)
kernel /boot/kernel-genkernel-x86_64-3.0.0-sabayon root=/dev/sda7
initrd /boot/initramfs-genkernel-x86_64-3.0.0-sabayon


# vim:ft=conf:
--------------------------------------------------------------------------------

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit  
 
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             grub.conf                                      1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt


```

---

