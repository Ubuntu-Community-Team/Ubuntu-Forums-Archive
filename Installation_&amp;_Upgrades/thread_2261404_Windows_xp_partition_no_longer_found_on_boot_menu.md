---
title: "Windows xp partition no longer found on boot menu"
date: 2015-01-18
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2015-01-18
I cloned xubuntu 12.04 on another disk and moved it (Clonzilla) to a new disk that had windows xp on it.  After the move the new xubuntu ran fine, but windows would not boot.  However, it still appeared in the boot menu.  So (under the new xubuntu) I ran ```
sudo update-grub
sudo grub-install /dev/sda
```  Then I rebooted and windows xp had been deleted from the boot menu.  However, it still showed up fine in gparted.  I ran Boot-Repair-Disk (default repair) and it didn't help.  So I ran Boot-Info (from Boot-Repair-Disk) and am showing it below. 

Any help in getting windows back is much appreciated!!

File is named "Boot-Info_2015-01-18__14h50.txt"  The old date must be the date I created the OS or the date it was last updated.

 ```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.2 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    26,568,703    26,568,641   7 NTFS / exFAT / HPFS
/dev/sda2          26,568,704    29,765,631     3,196,928  82 Linux swap / Solaris
/dev/sda3          29,765,632    78,139,391    48,373,760   5 Extended
/dev/sda5          57,352,192    78,139,391    20,787,200  83 Linux
/dev/sda6          29,767,680    43,491,327    13,723,648  83 Linux
/dev/sda7          43,493,376    57,350,143    13,856,768  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        79AC8C39365F348E                       ntfs       
/dev/sda2        eb7dd038-2e7d-4df7-b6e5-847a6af46a43   swap       
/dev/sda5        78342a8a-c4e1-4ff9-9a4e-b8206d35223b   ext4       PresData
/dev/sda6        10c8b10c-6ac0-4e3f-acf8-d0b221e1aa71   ext4       xprecise
/dev/sda7        6aac5c71-0886-4505-ab09-ed9644c4d226   ext4       
/dev/sr0                                                iso9660    Boot-Repair-Disk 32bit
/dev/zram0       5e428aec-5764-4c21-9ccf-bfed5fe136b8   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jan 18 14:50 ata-ST94011A_3KW07K8G -> ../../sda
lrwxrwxrwx 1 root root 10 Jan 18 14:50 ata-ST94011A_3KW07K8G-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jan 18 14:38 ata-ST94011A_3KW07K8G-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jan 18 14:38 ata-ST94011A_3KW07K8G-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jan 18 14:38 ata-ST94011A_3KW07K8G-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jan 18 14:38 ata-ST94011A_3KW07K8G-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Jan 18 14:38 ata-ST94011A_3KW07K8G-part7 -> ../../sda7
lrwxrwxrwx 1 root root  9 Jan 18 14:38 ata-TOSHIBA_DVD-ROM_SD-R2312_9368315505 -> ../../sr0

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 10c8b10c-6ac0-4e3f-acf8-d0b221e1aa71
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 10c8b10c-6ac0-4e3f-acf8-d0b221e1aa71
  set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 3.2.0-40-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 10c8b10c-6ac0-4e3f-acf8-d0b221e1aa71
    linux    /boot/vmlinuz-3.2.0-40-generic root=UUID=10c8b10c-6ac0-4e3f-acf8-d0b221e1aa71 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-40-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-40-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 10c8b10c-6ac0-4e3f-acf8-d0b221e1aa71
    echo    'Loading Linux 3.2.0-40-generic ...'
    linux    /boot/vmlinuz-3.2.0-40-generic root=UUID=10c8b10c-6ac0-4e3f-acf8-d0b221e1aa71 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-40-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 10c8b10c-6ac0-4e3f-acf8-d0b221e1aa71
    linux    /boot/vmlinuz-3.2.0-39-generic root=UUID=10c8b10c-6ac0-4e3f-acf8-d0b221e1aa71 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-39-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 10c8b10c-6ac0-4e3f-acf8-d0b221e1aa71
    echo    'Loading Linux 3.2.0-39-generic ...'
    linux    /boot/vmlinuz-3.2.0-39-generic root=UUID=10c8b10c-6ac0-4e3f-acf8-d0b221e1aa71 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-39-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-37-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 10c8b10c-6ac0-4e3f-acf8-d0b221e1aa71
    linux    /boot/vmlinuz-3.2.0-37-generic root=UUID=10c8b10c-6ac0-4e3f-acf8-d0b221e1aa71 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-37-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 10c8b10c-6ac0-4e3f-acf8-d0b221e1aa71
    echo    'Loading Linux 3.2.0-37-generic ...'
    linux    /boot/vmlinuz-3.2.0-37-generic root=UUID=10c8b10c-6ac0-4e3f-acf8-d0b221e1aa71 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-37-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 10c8b10c-6ac0-4e3f-acf8-d0b221e1aa71
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 10c8b10c-6ac0-4e3f-acf8-d0b221e1aa71
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=10c8b10c-6ac0-4e3f-acf8-d0b221e1aa71 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=eb7dd038-2e7d-4df7-b6e5-847a6af46a43 none            swap    sw              0       0
# PresData Entry follows:
# UUID=78342a8a-c4e1-4ff9-9a4e-b8206d35223b    /media/PresData    ext4    rw,nosuid,nodev,users,acl,user_xattr
#UUID=78342a8a-c4e1-4ff9-9a4e-b8206d35223b    /media/PresData    ext4    rw,nosuid,nodev,users,acl,user_xattr errors=remount-ro 0       1
#Ralph made PresData entry just like Share_Data in Latitude
UUID=78342a8a-c4e1-4ff9-9a4e-b8206d35223b    /media/PresData    ext4    defaults,acl,user_xattr errors=remount-ro 0       1

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/9275/mounts) leaked on lvs invocation. Parent PID 16092: bash
File descriptor 63 (pipe:[82966]) leaked on lvs invocation. Parent PID 16092: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-info 2015-01-18__14h50 ===================
boot-info version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/9275/mounts) leaked on lvs invocation. Parent PID 10785: /bin/sh
No volume groups found
boot-info is executed in live-session (Boot-Repair-Disk 32bit 29nov2014, trusty, Ubuntu, i686)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --

=================== os-prober:
/dev/sda6:Ubuntu 12.04.2 LTS (12.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="79AC8C39365F348E" TYPE="ntfs"
/dev/sda2: UUID="eb7dd038-2e7d-4df7-b6e5-847a6af46a43" TYPE="swap"
/dev/sda5: LABEL="PresData" UUID="78342a8a-c4e1-4ff9-9a4e-b8206d35223b" TYPE="ext4"
/dev/sda6: LABEL="xprecise" UUID="10c8b10c-6ac0-4e3f-acf8-d0b221e1aa71" TYPE="ext4"
/dev/sda7: UUID="6aac5c71-0886-4505-ab09-ed9644c4d226" TYPE="ext4"
/dev/sr0: LABEL="Boot-Repair-Disk 32bit" TYPE="iso9660"
/dev/zram0: UUID="5e428aec-5764-4c21-9ccf-bfed5fe136b8" TYPE="swap"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== sda6/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Feb 13  2013 grub.d
total 60
-rwxr-xr-x 1 root root 6743 Jan 22  2013 00_header
-rwxr-xr-x 1 root root 5522 Jan 22  2013 05_debian_theme
-rwxr-xr-x 1 root root 7780 Jan 22  2013 10_linux
-rwxr-xr-x 1 root root 6335 Jan 22  2013 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 Jan 22  2013 30_os-prober
-rwxr-xr-x 1 root root 1388 Jan 22  2013 30_uefi-firmware
-rwxr-xr-x 1 root root  214 Jan 22  2013 40_custom
-rwxr-xr-x 1 root root   95 Jan 22  2013 41_custom
-rw-r--r-- 1 root root  483 Jan 22  2013 README




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



=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda5    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda5.
sda6    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda6.
sda7    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda7.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes


=================== parted -l:

Model: ATA ST94011A (scsi)
Disk /dev/sda: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  13.6GB  13.6GB  primary   ntfs            boot
2      13.6GB  15.2GB  1637MB  primary   linux-swap(v1)
3      15.2GB  40.0GB  24.8GB  extended
6      15.2GB  22.3GB  7027MB  logical   ext4
7      22.3GB  29.4GB  7095MB  logical   ext4
5      29.4GB  40.0GB  10.6GB  logical   ext4



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Error: /dev/zram0: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:40.0GB:scsi:512:512:msdos:ATA ST94011A;
1:32.3kB:13.6GB:13.6GB:ntfs::boot;
2:13.6GB:15.2GB:1637MB:linux-swap(v1)::;
3:15.2GB:40.0GB:24.8GB:::;
6:15.2GB:22.3GB:7027MB:ext4::;
7:22.3GB:29.4GB:7095MB:ext4::;
5:29.4GB:40.0GB:10.6GB:ext4::;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Error: /dev/zram0: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type ext4 (rw)
/dev/sda6 on /mnt/boot-sav/sda6 type ext4 (rw)
/dev/sda7 on /mnt/boot-sav/sda7 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  agpgart autofs block bsg btrfs-control bus cdrom char console core cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse fw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda5 sda6 sda7 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  b8 67 95 01 00 00 00 00  |.........g......|
00000030  04 00 00 00 00 00 00 00  fc bd 18 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  8e 34 5f 36 39 8c ac 79  |.........4_69..y|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  469M  5.1M  464M   2% /
udev           devtmpfs   456M   12K  456M   1% /dev
tmpfs          tmpfs       94M  964K   93M   2% /run
/dev/sr0       iso9660    599M  599M     0 100% /cdrom
/dev/loop0     squashfs   543M  543M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      469M   12K  469M   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      469M     0  469M   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sda1      fuseblk     13G   65M   13G   1% /mnt/boot-sav/sda1
/dev/sda5      ext4       9.7G  5.4G  3.8G  59% /mnt/boot-sav/sda5
/dev/sda6      ext4       6.4G  3.8G  2.3G  63% /mnt/boot-sav/sda6
/dev/sda7      ext4       6.4G   15M  6.1G   1% /mnt/boot-sav/sda7

=================== fdisk -l:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xae32ae32

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    26568703    13284320+   7  HPFS/NTFS/exFAT
/dev/sda2        26568704    29765631     1598464   82  Linux swap / Solaris
/dev/sda3        29765632    78139391    24186880    5  Extended
/dev/sda5        57352192    78139391    10393600   83  Linux
/dev/sda6        29767680    43491327     6861824   83  Linux
/dev/sda7        43493376    57350143     6928384   83  Linux

Partition table entries are not in disk order




=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda6 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by oldfred on 2015-01-19
Please use code tags on long text or terminal output.

You show no Windows boot files.
       Windows BIOS Boot files:

WinXP
/boot.ini /ntldr /NTDETECT.COM

Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

If full install is there, you can use Windows XP disk in Repair console to repair it. But usually boot files would not just disappear. Are you sure you were not booting from another Windows partition or another drive? All installs of Windows only have boot files in the one active (boot flag) partition on the one drive set as boot in BIOS.

---

### Post by zach25 on 2015-01-19
> **oldfred said:**
> Please use code tags on long text or terminal output.

You show no Windows boot files.
       Windows BIOS Boot files:

WinXP
/boot.ini /ntldr /NTDETECT.COM

Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

If full install is there, you can use Windows XP disk in Repair console to repair it. But usually boot files would not just disappear. Are you sure you were not booting from another Windows partition or another drive? All installs of Windows only have boot files in the one active (boot flag) partition on the one drive set as boot in BIOS.

You can use the XP disk to repair, as stated above. Did you install using manual (gparted) partitioning? Or auto.

---

### Post by Ralph L on 2015-01-21
Thank you guys for replying.  I really appreciate it.
However, I couldn't find a way to mount my windows partition hda1, when I brought up windows from the cd.  If I mounted the windows partition in xubuntu, nautilus couldn't find any files on it.  So I think that the windows partition had been damaged.  Anyway I gave up and did a clone (clonzilla) of a windows partition on a different disk and copied it to the sda1 partition.  Then ran Boot Disk Repair and was able to boot both windows and xubuntu.  So now I am trying to configure windows xp to connect to my lan using wpa2 personal.

Thanks for the help.

---

