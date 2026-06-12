---
title: "EFI Dualboot Ubuntu 13.04 and Windows 8 on Lenovo IdeaPad Y500"
date: 2013-06-21
forum: Installation &amp; Upgrades
---

### Post by gdoron on 2013-06-21
I know there are a few posts about the matter, but none of the solutions seem to work.  I have the version that does not come with a system installed, meaning that EFI SecureBoot is not activated. Windows 8 installed fine, and I left free space for Ubuntu. Windows 8 created the efi partition and one more which I don't know what is bit for. Ubuntu also installs fine, but will not boot. Windows boots fine till I run boot repair. After that, there is an error saying that the default boot media does not work. If I click enter I get to the boot device selection BIOS prompt. If I choose any of the OSs(windows and Ubuntu) a prompt will come up saying that the security policy blocks it. I updated the BIOS with no change

I would prefer to run it natively instead of a VM so if anyone could explain this I would be grateful.

Thanks

---

### Post by fantab on 2013-06-21
Post the output of what 'BootInfo Summary' generates from Boot-Repair. That Summmary has valuable information to see what's going on.

---

### Post by gdoron on 2013-06-21
The output from the latest attempt:

 ```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 3June2013]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.00-3.35) is installed in the MBR of /dev/sdb.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdc and looks on the 
    same drive in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/grubx64.efi 
                       /EFI/Microsoft/Boot/bkpbootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi /bootmgr /boot/bcd

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.04 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06
    Boot sector info:  Syslinux looks at sector 32776 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sdc1 has 
                       1907734424 sectors, but according to the info from 
                       fdisk, it has 1953523119 sectors.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048   215,959,551   215,957,504 Data partition (Windows/Linux)
/dev/sda2     215,959,552 1,849,272,319 1,633,312,768 Data partition (Windows/Linux)
/dev/sda3   1,849,272,320 1,849,886,719       614,400 Windows Recovery Environment (Windows)
/dev/sda4   1,849,886,720 1,850,091,519       204,800 EFI System partition
/dev/sda5   1,850,091,520 1,850,353,663       262,144 Microsoft Reserved Partition (Windows)
/dev/sda6   1,850,353,664 1,920,077,823    69,724,160 Data partition (Windows/Linux)
/dev/sda7   1,920,077,824 1,953,523,711    33,445,888 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8166 MB, 8166703104 bytes
255 heads, 63 sectors/track, 992 cylinders, total 15950592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    15,950,591    15,948,544   c W95 FAT32 (LBA)


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 1,953,525,167 1,953,523,120   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        82AEF62EAEF61A7D                       ntfs       
/dev/sda2        CAE6F9A4E6F99145                       ntfs       
/dev/sda3        A8A8FD7EA8FD4B78                       ntfs       Odzyskiwanie
/dev/sda4        8EFE-E264                              vfat       
/dev/sda6        ef13a691-d5e8-4a30-b8b2-ef1cd77f702d   ext4       
/dev/sda7        3f4aa5e8-c8d2-49ef-a4a6-4b7981537618   swap       
/dev/sdb1        5435-0983                              vfat       UBUNTU 1304
/dev/sdc1        70D61C3FD61C084C                       ntfs       WD

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc1        /media/ubuntu/WD         fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda6/boot/grub/grub.cfg: ===========================

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

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  ef13a691-d5e8-4a30-b8b2-ef1cd77f702d
else
  search --no-floppy --fs-uuid --set=root ef13a691-d5e8-4a30-b8b2-ef1cd77f702d
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-ef13a691-d5e8-4a30-b8b2-ef1cd77f702d' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  ef13a691-d5e8-4a30-b8b2-ef1cd77f702d
    else
      search --no-floppy --fs-uuid --set=root ef13a691-d5e8-4a30-b8b2-ef1cd77f702d
    fi
    linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=ef13a691-d5e8-4a30-b8b2-ef1cd77f702d ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-19-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-ef13a691-d5e8-4a30-b8b2-ef1cd77f702d' {
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-ef13a691-d5e8-4a30-b8b2-ef1cd77f702d' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  ef13a691-d5e8-4a30-b8b2-ef1cd77f702d
        else
          search --no-floppy --fs-uuid --set=root ef13a691-d5e8-4a30-b8b2-ef1cd77f702d
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=ef13a691-d5e8-4a30-b8b2-ef1cd77f702d ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-ef13a691-d5e8-4a30-b8b2-ef1cd77f702d' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  ef13a691-d5e8-4a30-b8b2-ef1cd77f702d
        else
          search --no-floppy --fs-uuid --set=root ef13a691-d5e8-4a30-b8b2-ef1cd77f702d
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=ef13a691-d5e8-4a30-b8b2-ef1cd77f702d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 8EFE-E264
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root 8EFE-E264
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 8 (loader) (on /dev/sda4)' --class windows --class os $menuentry_id_option 'osprober-chain-8EFE-E264' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt4'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  8EFE-E264
    else
      search --no-floppy --fs-uuid --set=root 8EFE-E264
    fi
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=ef13a691-d5e8-4a30-b8b2-ef1cd77f702d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda4 during installation
#UUID=8EFE-E264  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda7 during installation
UUID=3f4aa5e8-c8d2-49ef-a4a6-4b7981537618 none            swap    sw              0       0
UUID=8EFE-E264    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 910.517539978 = 977.660764160  boot/grub/grub.cfg                             1
 882.857528687 = 947.961053184  boot/vmlinuz-3.8.0-19-generic                  1
 882.857528687 = 947.961053184  vmlinuz                                        1
 891.316802979 = 957.044129792  boot/initrd.img-3.8.0-19-generic               1
 891.316802979 = 957.044129792  initrd.img                                     1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1

=============================== StdErr Messages: ===============================

File descriptor 8 (/proc/6043/mounts) leaked on lvscan invocation. Parent PID 22738: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-06-20__21h39 ===================
boot-repair version : 3.199~ppa6~raring
boot-sav version : 3.199~ppa6~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.199~ppa6~raring
boot-repair is executed in live-session (Ubuntu 13.04, raring, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda4:Windows 8 (loader):Windows:chain
/dev/sda6:Ubuntu 13.04 (13.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="82AEF62EAEF61A7D" TYPE="ntfs"
/dev/sda2: UUID="CAE6F9A4E6F99145" TYPE="ntfs"
/dev/sda3: LABEL="Odzyskiwanie" UUID="A8A8FD7EA8FD4B78" TYPE="ntfs"
/dev/sda4: UUID="8EFE-E264" TYPE="vfat"
/dev/sda6: UUID="ef13a691-d5e8-4a30-b8b2-ef1cd77f702d" TYPE="ext4"
/dev/sda7: UUID="3f4aa5e8-c8d2-49ef-a4a6-4b7981537618" TYPE="swap"
/dev/sdb1: LABEL="UBUNTU 1304" UUID="5435-0983" TYPE="vfat"
/dev/sdc1: LABEL="WD" UUID="70D61C3FD61C084C" TYPE="ntfs"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda1.

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda4/EFI/Microsoft/Boot/bkpbootmgfw.efi
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda4/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda4/EFI/Microsoft/Boot/bootx64.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda4/EFI/Boot/bkpbootx64.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda4/EFI/Boot/bootx64.efi
Presence of .bkp file detected: /mnt/boot-sav/sda4/EFI/Boot/bkpbootx64.efi
Presence of .bkp file detected: /mnt/boot-sav/sda4/EFI/Microsoft/Boot/bkpbootmgfw.efi


=================== sda6/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== sda6/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jun 20 21:09 grub.d
drwxr-xr-x  2 root root    4096 Jun 20 21:08 grub.d.bak
total 72
-rwxr-xr-x 1 root root  7541 Apr  9 09:29 00_header
-rwxr-xr-x 1 root root  5974 Apr  9 08:53 05_debian_theme
-rwxr-xr-x 1 root root 11381 Apr  9 09:29 10_linux
-rwxr-xr-x 1 root root 10258 Apr  9 09:29 20_linux_xen
-rwxr-xr-x 1 root root   320 Jun 20 21:09 25_custom
-rwxr-xr-x 1 root root 10976 Apr  9 09:29 30_os-prober
-rwxr-xr-x 1 root root  1426 Apr  9 09:29 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  9 09:29 40_custom
-rwxr-xr-x 1 root root   216 Apr  9 09:29 41_custom
-rw-r--r-- 1 root root   483 Apr  9 09:29 README


/boot/efi detected in the fstab of sda6: UUID=8EFE-E264     (sda4)
efibootmgr -v
gui-g2slaunch.sh: line 127: efibootmgr: command not found
=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.
sda4    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda4.
sda6    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda6.
sdc1    : sdc,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /media/ubuntu/WD.

sda    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes
sdc    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     usb-disk,    no-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD10JPVT-24A (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
1      1049kB  111GB   111GB   ntfs
2      111GB   947GB   836GB   ntfs
3      947GB   947GB   315MB   ntfs            Basic data partition          hidden, diag
4      947GB   947GB   105MB   fat32           EFI system partition          boot
5      947GB   947GB   134MB                   Microsoft reserved partition  msftres
6      947GB   983GB   35.7GB  ext4
7      983GB   1000GB  17.1GB  linux-swap(v1)


Model: USB 2.0 USB Flash Drive (scsi)
Disk /dev/sdb: 8167MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  8167MB  8166MB  primary  fat32        boot, lba


Model: TrekStor DS maxi m.u (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  1000GB  1000GB  primary  ntfs

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:4096:gpt:ATA WDC WD10JPVT-24A;
1:1049kB:111GB:111GB:ntfs::;
2:111GB:947GB:836GB:ntfs::;
3:947GB:947GB:315MB:ntfs:Basic data partition:hidden, diag;
4:947GB:947GB:105MB:fat32:EFI system partition:boot;
5:947GB:947GB:134MB::Microsoft reserved partition:msftres;
6:947GB:983GB:35.7GB:ext4::;
7:983GB:1000GB:17.1GB:linux-swap(v1)::;

BYT;
/dev/sdb:8167MB:scsi:512:512:msdos:USB 2.0 USB Flash Drive;
1:1049kB:8167MB:8166MB:fat32::boot, lba;

BYT;
/dev/sdc:1000GB:scsi:512:512:msdos:TrekStor DS maxi m.u;
1:1049kB:1000GB:1000GB:ntfs::;


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/ubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/ubuntu/WD type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4 on /mnt/boot-sav/sda4 type vfat (rw)
/dev/sda6 on /mnt/boot-sav/sda6 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fb1 fd full fuse hidraw0 hidraw1 hidraw2 hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sdb sdb1 sdc sdc1 sg0 sg1 sg2 shm snapshot snd stderr stdin stdout uinput urandom usb v4l vga_arbiter vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 3f df 0c 00 00 00 00  |.........?......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  7d 1a f6 ae 2e f6 ae 82  |........}.......|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 48 df 0c  |........?....H..|
00000020  00 00 00 00 80 00 80 00  ff 5f 5a 61 00 00 00 00  |........._Za....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  45 91 f9 e6 a4 f9 e6 ca  |........E.......|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 39 6e  |........?.....9n|
00000020  00 00 00 00 80 00 80 00  ff 5f 09 00 00 00 00 00  |........._......|
00000030  00 64 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.d..............|
00000040  f6 00 00 00 01 00 00 00  78 4b fd a8 7e fd a8 a8  |........xK..~...|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda4
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 43 6e  |........?.....Cn|
00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 64 e2 fe 8e 4e  4f 20 4e 41 4d 45 20 20  |..)d...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdc1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  98 b7 b5 71 00 00 00 00  |...........q....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  4c 08 1c d6 3f 1c d6 70  |........L...?..p|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  7.9G   98M  7.8G   2% /
udev           devtmpfs   7.8G   12K  7.8G   1% /dev
tmpfs          tmpfs      1.6G  932K  1.6G   1% /run
/dev/sdb1      vfat       7.6G  785M  6.9G  11% /cdrom
/dev/loop0     squashfs   738M  738M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      7.9G  1.1M  7.9G   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs      7.9G  144K  7.9G   1% /run/shm
none           tmpfs      100M   32K  100M   1% /run/user
/dev/sdc1      fuseblk    910G  651G  259G  72% /media/ubuntu/WD
/dev/sda1      fuseblk    103G   74G   30G  72% /mnt/boot-sav/sda1
/dev/sda2      fuseblk    779G  165G  615G  22% /mnt/boot-sav/sda2
/dev/sda3      fuseblk    300M  218M   83M  73% /mnt/boot-sav/sda3
/dev/sda4      vfat        96M   44M   53M  46% /mnt/boot-sav/sda4
/dev/sda6      ext4        33G  3.0G   28G  10% /mnt/boot-sav/sda6

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 8166 MB, 8166703104 bytes
255 heads, 63 sectors/track, 992 cylinders, total 15950592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00746c04

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15950591     7974272    c  W95 FAT32 (LBA)

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x86bab26d

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953525167   976761560    7  HPFS/NTFS/exFAT


EFI detected. Please check the options.

=================== Default settings
Recommended-Repair
This setting would reinstall the grub-efi of sda6, using the following options:        sda4/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot backup-and-rename-efi-files

=================== Settings chosen by the user
Custom-Repair
This setting will purge (in order to fix packages) and reinstall the grub-efi of sda6, using the following options:        sda4/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s    backup-and-rename-efi-files


rm /mnt/boot-sav/sda4/efi/Microsoft/Boot/bootmgfw.efi
rm /mnt/boot-sav/sda4/efi/Microsoft/Boot/bootx64.efi /mnt/boot-sav/sda4/efi/Microsoft/Boot/bootx64.efi.grb
rm /mnt/boot-sav/sda4/efi/Boot/bootx64.efi
Mount sda4 on /mnt/boot-sav/sda6/boot/efi
ls /mnt/boot-sav/sda6/boot/efi: Boot
bootmgr
BOOTNXT
EFI  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
No sda6/boot/efi/efi/ubuntu/ folder
chroot /mnt/boot-sav/sda6 apt-get -y --force-yes update
Purge the GRUB of sda6
grub-efi available

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 100 not upgraded.
DEBCHECK debOK, grub-efi
DEBCHECK debOK
shim-signed available
linux-signed-generic available
Please type: sudo chroot "/mnt/boot-sav/sda6" dpkg --configure -ansudo chroot "/mnt/boot-sav/sda6" apt-get install -fynsudo chroot "/mnt/boot-sav/sda6" apt-get purge -y --force-yes grub*-common shim-signed linux-signed*
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda6/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda6/boot/efi/EFI/Boot/bootx64.efi

=================== sda6/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jun 20 21:42 grub.d
drwxr-xr-x  2 root root    4096 Jun 20 21:08 grub.d.bak
total 4
-rwxr-xr-x 1 root root 320 Jun 20 21:09 25_custom


/boot/efi detected in the fstab of sda6: UUID=8EFE-E264     (sda4)
Then type: sudo chroot "/mnt/boot-sav/sda6" apt-get install -y --force-yes grub-efi linux
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda6/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda6/boot/efi/EFI/Boot/bootx64.efi


=================== sda6/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== sda6/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jun 20 21:42 grub.d
drwxr-xr-x  2 root root    4096 Jun 20 21:08 grub.d.bak
total 68
-rwxr-xr-x 1 root root  7541 Apr  9 09:29 00_header
-rwxr-xr-x 1 root root  5974 Apr  9 08:53 05_debian_theme
-rwxr-xr-x 1 root root 11381 Apr  9 09:29 10_linux
-rwxr-xr-x 1 root root 10258 Apr  9 09:29 20_linux_xen
-rwxr-xr-x 1 root root 10976 Apr  9 09:29 30_os-prober
-rwxr-xr-x 1 root root  1426 Apr  9 09:29 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  9 09:29 40_custom
-rwxr-xr-x 1 root root   216 Apr  9 09:29 41_custom
-rw-r--r-- 1 root root   483 Apr  9 09:29 README


/boot/efi detected in the fstab of sda6: UUID=8EFE-E264     (sda4)
Unhide GRUB boot menu in sda6/etc/default/grub
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda6/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda6/boot/efi/EFI/Boot/bootx64.efi


=================== sda6/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== sda6/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jun 20 21:42 grub.d
drwxr-xr-x  2 root root    4096 Jun 20 21:08 grub.d.bak
total 68
-rwxr-xr-x 1 root root  7541 Apr  9 09:29 00_header
-rwxr-xr-x 1 root root  5974 Apr  9 08:53 05_debian_theme
-rwxr-xr-x 1 root root 11381 Apr  9 09:29 10_linux
-rwxr-xr-x 1 root root 10258 Apr  9 09:29 20_linux_xen
-rwxr-xr-x 1 root root 10976 Apr  9 09:29 30_os-prober
-rwxr-xr-x 1 root root  1426 Apr  9 09:29 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  9 09:29 40_custom
-rwxr-xr-x 1 root root   216 Apr  9 09:29 41_custom
-rw-r--r-- 1 root root   483 Apr  9 09:29 README


/boot/efi detected in the fstab of sda6: UUID=8EFE-E264     (sda4)
grub-install (GRUB) 2.00-13ubuntu3,grub-install (GRUB) 2.

chroot /mnt/boot-sav/sda6 efibootmgr -v
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0006,2001,0003,0002,0001,0000
Boot0000* Network Boot: Atheros Boot Agent    BIOS(80,0,ae)........................R..............................................
Boot0001* SATA HDD    : WDC WD10JPVT-24A1YT0                BIOS(2,500,18)................-.R.......R.A.R........................................
Boot0002* USB HDD     : USB 2.0 USB Flash Drive     BIOS(2,500,18).......................................................................
Boot0003* USB HDD     : TrekStorDS maxi m.u    BIOS(2,500,6d).......................................................................
Boot0004* EFI USB Device (USB 2.0 USB Flash Drive)    ACPI(a0341d0,0)PCI(14,0)USB(2,0)HD(1,800,f35b00,00746c04)RC
Boot0006* Windows Boot Manager    HD(4,6e430800,32000,0a3805e0-1401-4e71-b183-6e6fc3cfa926)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....J...............
Boot2001* EFI USB Device    RC

Reinstall the grub-efi linux of sda6
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi : exit code of grub-install :0
(debug) beglsefi1 ubuntu/grubx64.efi ; ubuntu , /mnt/boot-sav/sda6/boot/efi .
ls /mnt/boot-sav/sda6/boot/efi: Boot
bootmgr
BOOTNXT
EFI  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
df /dev/sda4
Save and rename /mnt/boot-sav/sda6/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi (/mnt/boot-sav/sda6/boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi)
cp /mnt/boot-sav/sda6/boot/efi/EFI/ubuntu/grubx64.efi /mnt/boot-sav/sda6/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
df /dev/sda4
cp /mnt/boot-sav/sda6/boot/efi/EFI/ubuntu/grubx64.efi /mnt/boot-sav/sda6/boot/efi/EFI/Microsoft/Boot/bootx64.efi (& .grb)
df /dev/sda4
Save and rename /mnt/boot-sav/sda6/boot/efi/EFI/Boot/bootx64.efi (/mnt/boot-sav/sda6/boot/efi/EFI/Boot/bkpbootx64.efi)
cp /mnt/boot-sav/sda6/boot/efi/EFI/ubuntu/grubx64.efi /mnt/boot-sav/sda6/boot/efi/EFI/Boot/bootx64.efi
ls /mnt/boot-sav/sda6/boot/efi: Boot
bootmgr
BOOTNXT
EFI  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Add /mnt/boot-sav/sda6/boot/efi efi entries in /mnt/boot-sav/sda6/etc/grub.d/25_custom
Adding custom /mnt/boot-sav/sda6/boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi
Adding custom /mnt/boot-sav/sda6/boot/efi/EFI/Boot/bkpbootx64.efi
sda4//mnt/boot-sav/sda6/boot/efi/EFI/Boot/bkpbootx64.efi already added
sda4//mnt/boot-sav/sda6/boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi already added
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi : exit code of grub-install :0

chroot /mnt/boot-sav/sda6 efibootmgr -v
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0006,2001,0003,0002,0001,0000
Boot0000* Network Boot: Atheros Boot Agent    BIOS(80,0,ae)........................R..............................................
Boot0001* SATA HDD    : WDC WD10JPVT-24A1YT0                BIOS(2,500,18)................-.R.......R.A.R........................................
Boot0002* USB HDD     : USB 2.0 USB Flash Drive     BIOS(2,500,18).......................................................................
Boot0003* USB HDD     : TrekStorDS maxi m.u    BIOS(2,500,6d).......................................................................
Boot0004* EFI USB Device (USB 2.0 USB Flash Drive)    ACPI(a0341d0,0)PCI(14,0)USB(2,0)HD(1,800,f35b00,00746c04)RC
Boot0006* Windows Boot Manager    HD(4,6e430800,32000,0a3805e0-1401-4e71-b183-6e6fc3cfa926)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....J...............
Boot2001* EFI USB Device    RC

chroot /mnt/boot-sav/sda6 update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found Windows 8 (loader) on /dev/sda4
Adding boot menu entry for EFI firmware configuration
Unhide GRUB boot menu in sda6/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (1000GB) disk!

```
I have attached a file with the URLs from other attempts including this one. I have tried different configurations. [ATTACH]244005[/ATTACH]

---

### Post by oldfred on 2013-06-21
Please use code tags on longer text to preserve formatting. With BootInfo better still to post link to pastebin it provides.

Did you move Windows? The Microsoft reserved partition must be the partition in front or just before the Windows install. Generally the efi partition is first but with Windows it usually installs its recovery (repair) partition first. Vendor recovery or image of hard drive is usually last.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by gdoron on 2013-06-21
Sorry about that, the link is in the attached text file in case it is needed. 

I did not move Windows. What I did was create 2 partitions (1: 103GB, 2: 700+GB) before installing Windows, which means they were first....

---

### Post by oldfred on 2013-06-21
If you are getting secure boot issues then you have turned secure boot back on? Some have reported that Windows can do that on updates.
Some Windows only boot with secure boot on, others boot with it on or off. Does your boot with it off?
Also some only boot bootmgfw.efi with secure boot. So Boot-Repair has a work around to rename grub's shim file to the Windows file name and from grub you boot the renamed /EFI/Microsoft/Boot/bkpbootmgfw.efi. 
Boot-Repair has renamed your Windows boot.

       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.

Also which grub entry are you booting? Grub2's os-prober still only creates BIOS entries, and Boot-Repair adds correct efi chain load entires to the renamed file.
      
 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bkpbootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

### Post by gdoron on 2013-06-21
The weird thing is, Windows reports SecureBoot as off and I can not find the option for it in the bios... It is possible that the security policy is enforced? The USB drive boots fine...

---

### Post by oldfred on 2013-06-21
The Microsoft contract with vendors says the user must be able to turn secure boot off. I gather it does not say you can still boot Windows with it off as some only boot with it on.

Some have specific settings for  secure boot. Others just have UEFI boot which means secure boot off or Legacy/CSM/BIOS boot which also means secure boot off and no UEFI boot. Some have auto modes also.

Other Lenovo info:
 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)

      
 Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)

---

### Post by gdoron on 2013-06-21
Well it installs fine... The BIOS is set on Legacy mode with UEFI first.. I have tried the 2 times boot repair and that did not work..

---

### Post by oldfred on 2013-06-21
Did you install in BIOS/Legacy mode? And are you running Boot-Repair in BIOS mode not UEFI?

What happens when you reboot. You do have to go into UEFI and choose to boot ubuntu entry.

---

### Post by gdoron on 2013-06-21
I use the uefi Ubuntu entry. I boot the USB with EfI entry  and windows has an efi entry. I get an error when selecting windows or Ubuntu that the security policy blocks it.

---

### Post by oldfred on 2013-06-21
That really sounds like secure boot is on.

You can use Boot-Repair when secure boot is on, and check secure boot box. Then it will download the signed version of grub and signed kernels to boot with secure boot on. 
No idea on Windows issues. Perhaps it really is saying it only boots with secure boot on. Some are configured that way.

---

### Post by gdoron on 2013-06-21
Well I've tried that and it did not work surprisingly enough, I can try again later.  The funny thing is, if I select the HDD through Legacy mode, I get the ubuntu live cd basically.. :)

---

### Post by gdoron on 2013-06-25
I tried it again. I get a failed to load grub error with the secureboot option...

BootInfo Summary:
[http://paste.ubuntu.com/5798834/](http://paste.ubuntu.com/5798834/)

---

### Post by oldfred on 2013-06-25
I do not see anything wrong other than partitions not in correct order. And with Windows that seems to be important with UEFI.

 Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
> Microsoft requires an MSR on every GPT disk, and recommends it to be  created as the disk is initially partitioned. It should be located after  the [EFI System Partition]("http://en.wikipedia.org/wiki/EFI_System_Partition") (ESP) and any [OEM]("http://en.wikipedia.org/wiki/Original_Equipment_Manufacturer") service partitions, but&#8212;most importantly&#8212;the first data partition must follow it. Initial size of MSR is 32 [MB]("http://en.wikipedia.org/wiki/Megabyte") on disks smaller than 16 [GB]("http://en.wikipedia.org/wiki/Gigabyte"),  or 128 MB on other disks, although it may later automatically shrink on  behalf of other partitions, for example during the conversion from [basic disk]("http://en.wikipedia.org/w/index.php?title=Basic_disk&action=edit&redlink=1") to [dynamic disk]("http://en.wikipedia.org/wiki/Dynamic_disk").

 

      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)

---

### Post by gdoron on 2013-06-25
I fixed it!

After the error appeared that grub can't be found in /EFI/Boot/, I did the following

[LIST=1]
[*]Copy the files from /EFI/ubuntu to /EFI/Boot/
[*]After it has booted, Windows 8 would not boot
[*]I repaired the Windows 8 boot files using the install DVD
[*]Now I use the boot device menu to choose which OS I want. YAY! :D
[/LIST]


Thanks for all your help!

---

