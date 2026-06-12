---
title: "cant get Grub loading"
date: 2015-01-10
forum: Installation &amp; Upgrades
---

### Post by chkneater on 2015-01-10
I have an esternal HDD, it's my only HDD for this compl. I store everything on it rather than a Desktop and losing everything when the computer screw.s. I chrooted into the parttition and found out dpkg was't working at al...Every tteun I try to a normal command like 'dpkg' I get rons of errors and a longl ist of commands thag absoltoeoy did not work. whenI chrooted into the parttion I couodn't do nothing to fix it,.. I keep geting 'dpkg' errrors with dpkg and also keep getting messages about 'cannot find a device; is /dev mounted etc.. I can't do u[grdae-grub from chrooting in to it, it says it can't fine / is and is /dev mounted?) I tried to reinstall 12..04 .... Right now my main prob is getting the new install to boot to grub successfully wihitfh ws the original prob. After reinstalling i haven't booted into grub.  and also figure out why fstab does not see /dev and keeps saying "is /dev mounted?"

sorry had to edit, wsa half asleep fromworking onthis thing LOL

allright I see

---

### Post by oldfred on 2015-01-11
From Live installer:

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Have you run fsck on Linux partitions?

---

### Post by chkneater on 2015-01-11
allright, having issues with RAM space cuz I'm running off of Cd... gonna clear up some space

I checked the UUID's and they were correct,  Trying right now to chroot back into the partition right now, I lost the directions after I turned my comp off lol...

can't chroot into partition, do you know how oldfred?

Ok here is the boot info output, I have three partitions, the file system(sde1), the swap (sde5), and the NTFS (sde3) :

```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sde and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sde1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.2 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sde5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sde _____________________________________________________________________

Disk /dev/sde: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *          2,048   911,276,031   911,273,984  83 Linux
/dev/sde3         911,276,032 1,541,212,159   629,936,128   7 NTFS / exFAT / HPFS
/dev/sde4       1,541,214,206 1,572,358,143    31,143,938   5 Extended
/dev/sde5       1,541,214,208 1,572,358,143    31,143,936  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sde1        68753da9-750c-42ef-992d-219d76171e98   ext4       
/dev/sde3        409CCDDC6304A495                       ntfs       
/dev/sde5        8a07f495-e6df-4eb3-ac07-3e57c9dcdf3e   swap       
/dev/sr0                                                iso9660    Ubuntu-Studio 12.04.2 amd64

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jan 11 16:42 ata-TSSTcorpCD_DVDW_TS-H652L -> ../../sr0
lrwxrwxrwx 1 root root  9 Jan 11 16:42 usb-Generic-_Compact_Flash_20021111153705700-0:0 -> ../../sda
lrwxrwxrwx 1 root root  9 Jan 11 16:42 usb-Generic-_MS_MS-Pro_20021111153705700-0:3 -> ../../sdd
lrwxrwxrwx 1 root root  9 Jan 11 16:42 usb-Generic-_SD_MMC_20021111153705700-0:2 -> ../../sdc
lrwxrwxrwx 1 root root  9 Jan 11 16:42 usb-Generic-_SM_xD-Picture_20021111153705700-0:1 -> ../../sdb
lrwxrwxrwx 1 root root  9 Jan 11 16:50 usb-WD_My_Book_1140_574343305430363533303839-0:0 -> ../../sde
lrwxrwxrwx 1 root root 10 Jan 11 16:42 usb-WD_My_Book_1140_574343305430363533303839-0:0-part1 -> ../../sde1
lrwxrwxrwx 1 root root 10 Jan 11 16:50 usb-WD_My_Book_1140_574343305430363533303839-0:0-part3 -> ../../sde3
lrwxrwxrwx 1 root root 10 Jan 11 16:42 usb-WD_My_Book_1140_574343305430363533303839-0:0-part4 -> ../../sde4
lrwxrwxrwx 1 root root 10 Jan 11 16:42 usb-WD_My_Book_1140_574343305430363533303839-0:0-part5 -> ../../sde5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sde1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 68753da9-750c-42ef-992d-219d76171e98
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 68753da9-750c-42ef-992d-219d76171e98
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
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
menuentry 'Ubuntu, with Linux 3.2.0-37-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 68753da9-750c-42ef-992d-219d76171e98
    linux    /boot/vmlinuz-3.2.0-37-lowlatency root=UUID=68753da9-750c-42ef-992d-219d76171e98 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-37-lowlatency
}
menuentry 'Ubuntu, with Linux 3.2.0-37-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 68753da9-750c-42ef-992d-219d76171e98
    echo    'Loading Linux 3.2.0-37-lowlatency ...'
    linux    /boot/vmlinuz-3.2.0-37-lowlatency root=UUID=68753da9-750c-42ef-992d-219d76171e98 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-37-lowlatency
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 68753da9-750c-42ef-992d-219d76171e98
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 68753da9-750c-42ef-992d-219d76171e98
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

=============================== sde1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=68753da9-750c-42ef-992d-219d76171e98 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8a07f495-e6df-4eb3-ac07-3e57c9dcdf3e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sde1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  40.136260986 = 43.095982080   boot/grub/grub.cfg                             1
 120.431159973 = 129.311973376  boot/grub/core.img                             1
  40.134525299 = 43.094118400   boot/vmlinuz-3.2.0-37-lowlatency               1
  40.134525299 = 43.094118400   vmlinuz                                        1
   2.196289062 = 2.358247424    boot/initrd.img-3.2.0-37-lowlatency            2
   2.196289062 = 2.358247424    initrd.img                                     2

========= Devices which don't seem to have a corresponding hard drive: =========

sda sdb sdc sdd 


ADDITIONAL INFORMATION :
=================== log of boot-info 2015-01-11__16h50 ===================
boot-info version : 4ppa32
boot-sav version : 4ppa32
glade2script version : 3.2.2~ppa45~precise
boot-sav-extra version : 4ppa32
boot-info is executed in live-session (Ubuntu 12.04.2 LTS, precise, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/ubuntustudio.seed boot=casper initrd=/casper/initrd.lz quiet splash --
ls: cannot access /home/usr/.config: No such file or directory

=================== os-prober:
/dev/sde1:Ubuntu 12.04.2 LTS (12.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Ubuntu-Studio 12.04.2 amd64" TYPE="iso9660"
/dev/sde1: UUID="68753da9-750c-42ef-992d-219d76171e98" TYPE="ext4"
/dev/sde3: UUID="409CCDDC6304A495" TYPE="ntfs"
/dev/sde5: UUID="8a07f495-e6df-4eb3-ac07-3e57c9dcdf3e" TYPE="swap"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== sde1/etc/grub.d/ :
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




=================== sde1/etc/default/grub :

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




=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sde1    : sde,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sde1.
sde3    : sde,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sde3.

sde    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     usb-disk,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: WD My Book 1140 (scsi)
Disk /dev/sde: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  467GB  467GB   primary   ext4            boot
3      467GB   789GB  323GB   primary   ntfs
4      789GB   805GB  15.9GB  extended
5      789GB   805GB  15.9GB  logical   linux-swap(v1)


Error: Can't have a partition outside the disk!

=================== parted -lm:

BYT;
/dev/sde:1000GB:scsi:512:512:msdos:WD My Book 1140;
1:1049kB:467GB:467GB:ext4::boot;
3:467GB:789GB:323GB:ntfs::;
4:789GB:805GB:15.9GB:::;
5:789GB:805GB:15.9GB:linux-swap(v1)::;

Error: Can't have a partition outside the disk!




=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu-studio/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu-studio)
/dev/sde1 on /mnt/boot-sav/sde1 type ext4 (rw)
/dev/sde3 on /mnt/boot-sav/sde3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sde1 sde3 sde4 sde5 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dmfm dmmidi dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet input kmsg log lp0 mapper mcelog mem midi net network_latency network_throughput null oldmem parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sdb sdc sdd sde sde1 sde3 sde4 sde5 sg0 sg1 sg2 sg3 sg4 sg5 sg6 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 usbmon6 usbmon7 vga_arbiter zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sde3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 f8 50 36  |........?.....P6|
00000020  00 00 00 00 80 00 80 00  f8 0f 8c 25 00 00 00 00  |...........%....|
00000030  04 00 00 00 00 00 00 00  84 a8 01 01 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  95 a4 04 63 dc cd 9c 40  |...........c...@|
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
/cow           overlayfs  1.5G  175M  1.3G  12% /
udev           devtmpfs   1.5G   12K  1.5G   1% /dev
tmpfs          tmpfs      603M  896K  602M   1% /run
/dev/sr0       iso9660    2.0G  2.0G     0 100% /cdrom
/dev/loop0     squashfs   1.4G  1.4G     0 100% /rofs
tmpfs          tmpfs      1.5G   20K  1.5G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.5G   92K  1.5G   1% /run/shm
/dev/sde1      ext4       428G  4.4G  402G   2% /mnt/boot-sav/sde1
/dev/sde3      fuseblk    301G   41G  261G  14% /mnt/boot-sav/sde3

=================== fdisk -l:

Disk /dev/sde: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00087fb3

Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048   911276031   455636992   83  Linux
/dev/sde3       911276032  1541212159   314968064    7  HPFS/NTFS/exFAT
/dev/sde4      1541214206  1572358143    15571969    5  Extended
/dev/sde5      1541214208  1572358143    15571968   82  Linux swap / Solaris


Partition outside the disk detected.


=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sde1 into the MBR of sde.
Additional repair would be performed: unhide-bootmenu-10s


=================== User settings
The settings chosen by the user will not act on the boot.



End.---------------------------------------
```

---

### Post by oldfred on 2015-01-11
Please use code tags if posting long terminal output.
With Boot-Repair better just to post link it gives.

I do not see anything in summary report. 
Was drive internal when you installed Ubuntu? It does show defaults as sda and hd0. But search by UUID should override that. 
Some BIOS do no like larger / (root) partitions on external drives. Some combination of BIOS and USB driver.  Often better if external drive to have a 25GB / partition at beginning of drive and use rest as /home or data partition(s).

First try fsck on whatever drive is seen as, sda, sde? Example is sdb, but change to where your drive is mounted.
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

    
Some examples of chroot.
 drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by chkneater on 2015-01-11
had to fsck instead of e4fsck, but it ran anyway:

> 
fsck from util-linux 2.20.1
                                                                               
  189977 inodes used (0.67%)
      32 non-contiguous files (0.0%)
     179 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 147975/3
 2939386 blocks used (2.58%)
       0 bad blocks
       1 large file

  124006 regular files
   14952 directories
      57 character device files
      25 block device files
       0 fifos
       1 link
   50928 symbolic links (41909 fast symbolic links)
       0 sockets
--------
  189969 files


---

### Post by oldfred on 2015-01-11
I believe fsck only does something if partition is already flagged as having an issue.

Better to run the e2fsck not e4fsck. You can just copy & paste commands from here into your terminal.

---

### Post by chkneater on 2015-01-23
Allright here is what happened... I ran off the LiveCD for a few weeks casually looking for answers to this.  I have to explain that I have no power button, so I have to short it to turn it on and off...  to start it I have to short it and plug in the Ext HDD just before the BIOS comes on.  I was running off the liveCD and the power wires shorted and restarted and when it restarted it went ritght into the login screen?  The LiveCd was still in the drive also and it is set to boot first.  I did all updates, then installed grub-imageboot, and sudo update-grub.  Now it works just liek before?!? 

Not complaining, but I wonder does anyone know why this happened so if it happens again I know wut to do?

---

### Post by oldfred on 2015-01-23
You cannot be shorting system all the time without having issues.

It may have run a fsck when rebooting?

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[xhttp://kember.net/articles/reisub-the-gentle-linux-restart/](xhttp://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by chkneater on 2015-01-23
by shorting the system I meant the POWER BUTTON, which is supposed to short to shut down and start up... that's not the issue, the issue is the Grub won't load at startup after kernel updates. They accidentally touched and when it rebooted it worked... look at OP plz???  Tired of explaining this over and over... Ext HDD WD, ubunut 12.04... did kernel update, grub broke... ran off CD for weeks looking for answers and the power wires touched shutting down system, it rebooted and is working,... now can ANYONE figure out why this is breaking the GRUB??   THAT is the problem as indicated in OP....

by shorting the system I meant the POWER BUTTON, which is supposed to short to shut down and start up... that's not the issue, the issue is the Grub won't load at startup after kernel updates. They accidentally touched and when it rebooted it worked... look at OP plz???  Tired of explaining this over and over... Ext HDD WD, ubunut 12.04... did kernel update, grub broke... ran off CD for weeks looking for answers and the power wires touched shutting down system, it rebooted and is working,... now can ANYONE figure out why this is breaking the GRUB??   THAT is the problem as indicated in OP....

---

### Post by oldfred on 2015-01-23
And you never should shutdown with power switch.

If external drive, does system boot faster than drive spins up. Or if you warm reboot does it then work? 
Is external drive separately powered or does it run only off USB ports? Do you power it up and is it running before you boot?

---

### Post by chkneater on 2015-01-23
i DON't use the power button... where did I say that?  i use the shut down button... it was an accident it got shut down as I said... it was after THAT my system started working again... Ext drive is seprately powered and has to be unplugged before turning on comp. then plug in Ext Hdd durin BIOS... it finds Grub, fails and goes to Grub rescue... no system does not start up faster than drive... drive works fine... all my volumes show up on LiveCd and mount.. nothing is wrong with Ext HDD... GRUB is not recognizing it after system updates and goes to grub rescue... if Ext HDD, the ONLY drive were at fault it would say 'no media found' not go to grub rescue... and as I said after ACCIDENTALLY shorting the power wires, the system rebooted and is working liek it used to.   

This problem I have had MANY tiems before and usually dropping 60_grub-imageboot into /etc/grub.d it will boot... My problem is WHY do I have problems booting off the Ext HDD drive which is evidentally fine and works perfect not being recognized by Grub after kernel updates?

I would LIEK to upgrade to 14.10 but not if I'm going to have to go thru this grub rescue BS again.

boot repair does nothing to fix this either.

---

### Post by oldfred on 2015-01-24
Post just the one line that shows drive, want to see if update of grub is to same drive you boot from.

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short

---

### Post by chkneater on 2015-01-27
Here is the output of ' sudo debconf-show grub-pc # for BIOS with grub-pc "

>  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub-pc/install_devices: /dev/disk/by-id/usb-WD_My_Book_1140_574343305430363533303839-0:0
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: true
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 10


And here's the output for ' sudo lshw -C Disk -short ' :

>  H/W path             Device      Class       Description
========================================================
/0/100/14.1/0.0.0    /dev/cdrom  disk        CD/DVDW TS-H652L
/0/100/14.1/0.0.0/0  /dev/cdrom  disk        
/0/1/0.0.0           /dev/sda    disk        1TB My Book 1140
/0/2/0.0.0           /dev/sdb    disk        SCSI Disk
/0/2/0.0.1           /dev/sdc    disk        SCSI Disk
/0/2/0.0.2           /dev/sdd    disk        SCSI Disk
/0/2/0.0.3           /dev/sde    disk        SCSI Disk


This disk is split into an NTFS partition and is the only HDD... I use the NTFS for storage only, there are no system files on it... from the output it looks liek grub is seeing it fine... the only thing I can possibly think is that when I originally place the 60_grub-imageboot file into the /etc/grub.d directory I originally did it using Gedit from the terminal while running on the LiveCD... it worked as far as placing the file there.  Then I decided to re-install and Chrooted into the OS and installed the grub-imageboot file with synaptic after doing update-grub and that was shortly before the power wire shorted and shut it down, when it rebooted it started up liek normal, no grub rescue.   I'm not sure that was the solution or not, but I'm trying to diagnose this and prevent it from happening again so I can upgrade soon.  And the fact that it WAS going to grub rescue means that the BIOS IS trying to boot from the HDD.  Can't think of any thing else important you might need to know?...

And yes I know I need to get a power button LOL

---

### Post by oldfred on 2015-01-27
Is not your My Book an external drive?
But your BIOS has promoted it to sda, and that is now the default reinstall location of grub.

What are sdb, sdc, sdd, & sde? do you also have a multi-card reader?

* grub-pc/install_devices: /dev/disk/by-id/usb-WD_My_Book_1140_574343305430363533303839-0:0

And device is:
/0/1/0.0.0           /dev/sda    disk        1TB My Book 1140

But then the names do not exactly match. So part of issue could be the extra spaces in the name and then something is not parsing the space correctly. Normally with Linux we do not use spaces.

---

### Post by chkneater on 2015-01-27
Um yeah, the My book is the Ext HDD, the only HDD... gparted shows it as sda1-5; sda3 is the swap, sda4 is the ext. and sda5 is the NTFS. sdb is the CD I bleieve and numerous usb ports and a broken multi card reader,  Boot order is Cd, HDD, USB but there is no serial or SATA HDD, just the Ext HDD and the CDRom.  I'm not sure about the syntax witht the spacing, it would make sense, but what would make it work if it's still the same??

---

### Post by oldfred on 2015-01-28
I would try changing name, not exactly sure how to do that. Disk Utility or Gparted may show that info somewhere.
I would also change boot order in BIOS. No reason to have system search thru non-existing devices which would slow boot. See USB as first, or if like may system the hard drive that really is the external drive connected. Depends just on how your BIOS shows external drive.

---

