---
title: "Boot (mbr\grub) problem Ub 12.04"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by Sda1986 on 2012-04-30
Hi all, I have a Samsung 700z3a laptop.
This laptop has a 8Gb SSD (sdb) and a 750Gb HDD (sda)

I was used to install on sda (SSD) the root folder (/) and on my HDD (sda) the /home, /var and swap.

I did it with 11.10 and one time with 12.04. It worked awesome, very fast and nice. After some random test with configuration (with kernel and other but not boot) and more I had to reinstall my OS but this time if I install as usual I am not able to make it work. The laptop doesn't see any bootable device.
I spend some time and I realized I can make Ubuntu work only if I install all the system on "/dev/sda" with the standard partition. If I try to install with my partion definitio won't work.

What could it be? I have no idea! It seems like grub doesn't work but the installation is able to make it work if i don't touch the partition by myaself.

Thanks!

---

### Post by oldfred on 2012-04-30
Is there some reason for a separate /var?

This is an older bug, not sure it applies.
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441)

---

### Post by Sda1986 on 2012-05-05
Sorry for the late answer lot of work recently!

So I wanted to have /var on a bigger HD because when I create KVM virtual machines usually the system create my images on /var/...

It's not a big deal I can create the images on other paths, anyway today I tried to put / on SDB (SSD8gb) and /home and swap on SDA (hdd750gb)

Nothing changed, no startup, I had to install again everything with basic configuration....

I can have a partition on sdb, but i must create it AFTER installation or maybe (never tried) have it already when I install.

Somehow I think it's something about grub and mbr but i dont' know what to search....

thanks

---

### Post by oldfred on 2012-05-05
Did grub install to the other drive and that is where it want to boot from?

Post link to the report from BootInfo:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

---

### Post by Sda1986 on 2012-05-06
I think the problem somehow it's UEFI, when I start BootRepair to fix standard issues it told me i have UEFI on and I should create a fat32 partition to make it work, this is something i really don't want! UEFI is disabled on my bios now (I tried one time).
Now on my boot list I have ubuntu and I don't know how fix it.
I found this topic: [http://ubuntuforums.org/showthread.php?t=1935699](http://ubuntuforums.org/showthread.php?t=1935699)
This is more or less my problem on the same pc, but I am unable to solve it, I would like to delete TGP and ubuntu from my boot menu... But I am not able to!

(writing from a LIVE CD session)

---

### Post by oldfred on 2012-05-06
Post link to BootInfo report that Boot-Repair can create. Then we can see your entire configuration and perhaps suggest something.

---

### Post by Sda1986 on 2012-05-06
I'm gonna try this: [http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)

I'm a bit confuse about UEFI, on my bios i can say enable\disable. But seems like one time you say yes you cannot come back, even when you reset the bios to default settings...

Thanks

```

            Boot Info Script 0.61-git-patched      [23 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20120131
    Boot sector info:  Syslinux looks at sector 1459488 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048 1,445,617,663 1,445,615,616  83 Linux
/dev/sda2       1,445,619,710 1,465,147,391    19,527,682   5 Extended
/dev/sda5       1,445,619,712 1,465,147,391    19,527,680  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8012 MB, 8012390400 bytes
24 heads, 9 sectors/track, 72450 cylinders, total 15649200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    15,648,767    15,646,720  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 7927 MB, 7927234560 bytes
244 heads, 62 sectors/track, 1023 cylinders, total 15482880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             62    15,475,943    15,475,882   c W95 FAT32 (LBA)


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 4005 MB, 4005527552 bytes
124 heads, 62 sectors/track, 1017 cylinders, total 7823296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             62     7,818,695     7,818,634   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        07f7052f-5047-468b-a404-dfff5fa2edff   ext4       
/dev/sdb1        f88c935f-4b90-445e-a764-1ee1476fb281   ext4       
/dev/sdc1        3804-2FB1                              vfat       
/dev/sdd1        34664B5B69CE57E6                       ntfs       x

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdd1        /media/x                 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root f88c935f-4b90-445e-a764-1ee1476fb281
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root f88c935f-4b90-445e-a764-1ee1476fb281
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root f88c935f-4b90-445e-a764-1ee1476fb281
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=f88c935f-4b90-445e-a764-1ee1476fb281 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root f88c935f-4b90-445e-a764-1ee1476fb281
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=f88c935f-4b90-445e-a764-1ee1476fb281 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root f88c935f-4b90-445e-a764-1ee1476fb281
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root f88c935f-4b90-445e-a764-1ee1476fb281
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=10
    else
      set timeout=10
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=10
    fi
  fi
fi
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
UUID=f88c935f-4b90-445e-a764-1ee1476fb281 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=07f7052f-5047-468b-a404-dfff5fa2edff /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
#UUID=2072ebbf-f288-4a23-bca5-eb2eca8fda34 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   2.336246490 = 2.508525568    boot/grub/core.img                             1
   0.144233704 = 0.154869760    boot/grub/grub.cfg                             1
   0.797851562 = 0.856686592    boot/initrd.img-3.2.0-23-generic               2
   0.682926178 = 0.733286400    boot/vmlinuz-3.2.0-23-generic                  1
   0.797851562 = 0.856686592    initrd.img                                     2
   0.682926178 = 0.733286400    vmlinuz                                        1

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)


ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-05-06__17h04 ===================
boot-repair version : 3.18-0ppa9~precise
boot-sav version : 3.18-0ppa19~precise
glade2script version : 0.3.2.1-0ppa7~precise
internet: connected
boot-repair is executed in live-session (Ubuntu 12.04 LTS , precise , Ubuntu , x86_64)

=================== OSPROBER:
/dev/sdb1:Ubuntu 12.04 LTS (12.04):Ubuntu:linux

=================== BLKID:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="07f7052f-5047-468b-a404-dfff5fa2edff" TYPE="ext4"
/dev/sdb1: UUID="f88c935f-4b90-445e-a764-1ee1476fb281" TYPE="ext4"
/dev/sdc1: UUID="3804-2FB1" TYPE="vfat"
/dev/sdd1: LABEL="x" UUID="34664B5B69CE57E6" TYPE="ntfs"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== /mnt/boot-sav/sdb1/etc/default/grub :

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




=================== dmesg | grep EFI :
[    0.000000] ACPI: UEFI 000000009afe9000 0003E (v01 SECCSD LH43STAR 00000002 PTL  00000002)
[    0.000000] ACPI: UEFI 000000009afe8000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 000000009afe5000 00256 (v01 SECCSD LH43STAR 00000002 PTL  00000002)
[    4.022553] EFI Variables Facility v0.08 2004-May-17


=================== PARTITIONS & DISKS:
sda1	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not-on-gpt-disk,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	/mnt/boot-sav/sda1.
sdb1	: sdb,	not-sepboot,	grubenv-ok	grub2,	grub-pc,	update-grub,	64,	with-boot,	is-os,	not-on-gpt-disk,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	apt-get,	grub-install,	/mnt/boot-sav/sdb1.
sdd1	: sdd,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not-on-gpt-disk,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	/media/x.

sda	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	2048 sectors * 512 bytes
sdb	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	2048 sectors * 512 bytes
sdd	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	62 sectors * 512 bytes

=================== PARTED:

Model: ATA Hitachi HTS72757 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
1      1049kB  740GB  740GB   primary   ext4
2      740GB   750GB  9998MB  extended
5      740GB   750GB  9998MB  logical


Model: ATA SanDisk iSSD P4 (scsi)
Disk /dev/sdb: 8012MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  8012MB  8011MB  primary  ext4         boot


Model: Verbatim  (scsi)
Disk /dev/sdc: 7927MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      31.7kB  7924MB  7924MB  primary  fat32        boot, lba


Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdd: 4006MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      31.7kB  4003MB  4003MB  primary  ntfs         boot, lba


=================== MOUNT:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdd1 on /media/x type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /mnt/boot-sav/sda1 type ext4 (rw)
/dev/sdb1 on /mnt/boot-sav/sdb1 type ext4 (rw)


/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sdd:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdd1 size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  agpgart autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fb1 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sdb sdb1 sdc sdc1 sdd sdd1 sg0 sg1 sg2 sg3 sg4 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 v4l vga_arbiter video0 zero
/dev/mapper:  control

=================== DF:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  2.9G  149M  2.8G   6% /
udev           devtmpfs   2.9G   12K  2.9G   1% /dev
tmpfs          tmpfs      1.2G  916K  1.2G   1% /run
/dev/sdc1      vfat       7.4G  698M  6.7G  10% /cdrom
/dev/loop0     squashfs   664M  664M     0 100% /rofs
tmpfs          tmpfs      2.9G   44K  2.9G   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs      2.9G  176K  2.9G   1% /run/shm
/dev/sdd1      fuseblk    3.8G   20M  3.8G   1% /media/x
/dev/sda1      ext4       689G   11G  644G   2% /mnt/boot-sav/sda1
/dev/sdb1      ext4       7.5G  2.3G  4.8G  33% /mnt/boot-sav/sdb1

=================== FDISK:

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000df538

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  1445617663   722807808   83  Linux
/dev/sda2      1445619710  1465147391     9763841    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1445619712  1465147391     9763840   82  Linux swap / Solaris

Disk /dev/sdb: 8012 MB, 8012390400 bytes
24 heads, 9 sectors/track, 72450 cylinders, total 15649200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ad451

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    15648767     7823360   83  Linux

Disk /dev/sdc: 7927 MB, 7927234560 bytes
244 heads, 62 sectors/track, 1023 cylinders, total 15482880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005c829

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          62    15475943     7737941    c  W95 FAT32 (LBA)

Disk /dev/sdd: 4005 MB, 4005527552 bytes
124 heads, 62 sectors/track, 1017 cylinders, total 7823296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00030e44

Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          62     7818695     3909317    c  W95 FAT32 (LBA)



=================== Before mainwindow
FSCK no PASTEBIN yes WUBI no WINBOOT no
recommendedrepair, reinstall, QTY_OF_PART_FOR_REINSTAL 1 no-kernel-purge
UNHIDEBOOT_ACTION yes (10s), noflag (sdb1)
PART_TO_REINSTALL_GRUB sdb1, FORCE_GRUB all (sdb) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sda1) grub2 ()
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE  ( )

=================== Actions
FSCK no PASTEBIN yes WUBI no WINBOOT no
bootinfo, nombraction, QTY_OF_PART_FOR_REINSTAL 1 no-kernel-purge
UNHIDEBOOT_ACTION no (10s), noflag (sdb1)
PART_TO_REINSTALL_GRUB sdb1, FORCE_GRUB all (sdb) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sda1) grub2 ()
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE  ( )
No change has been performed on your computer. See you soon!
internet: connected
pastebinit  packages needed
User refused to install pastebinit
```

---

### Post by oldfred on 2012-05-06
With UEFI, you need to partition to gpt with an efi partition first. I use gpt with BIOS boot and one my new SSD left space for an efi partiiton, but needed a bios_grub to boot with BIOS. 

Changing to gpt will erase drive, although you may be able to convert. I do use gpt on my boot drive but have data partitions for NTFS and ext3 on a MBR drive.

---

### Post by Sda1986 on 2012-05-06
Yes I put "/" on all sdb (ssd 8gb) and the uefi partition on the 750hd (sda) and all worked well, but I still think how can I use it with EUFI disabled!

I tried format che hd with ms-dos partition, but didn't work. I would like to install linux without UEFI. 

Is better run pc with or without UEFI?

---

### Post by oldfred on 2012-05-06
Some say UEFI is faster booting and others cannot get it to work. 

It seems vendors do not have a consistent implementation of UEFI and some work better than others.

---

### Post by Sda1986 on 2012-05-06
I don't think my laptop is booting faster. It add around 1-2 sec because it adds some "work" between grub and real ubuntu boot. I don't care much about it, I won't die for some seconds, but I cannot understand why I cannot go back without UEFI...

---

### Post by miatawnt2b on 2012-06-06
Did you ever find a solution?  I am in the same boat, same laptop, trying to do the same thing.

I guess I could always put /boot on the HD and / on the iSSD...

-J

---

