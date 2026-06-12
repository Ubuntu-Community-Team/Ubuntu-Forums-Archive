---
title: "ASRock UEFI bios + Ubuntu Server = operating system not found"
date: 2013-06-10
forum: Installation &amp; Upgrades
---

### Post by Sunius on 2013-06-10
Hello guys.

I'm trying to install Ubuntu Server to one of my PCs and I've encountered issues. Spent loads of time (a few days) searching the web for a similar issue and solution, though I couldn't find anything at all.

This is my PC Configuration:

ASRock AD2550B-ITX motherboard with embedded Intel Atom CPU
2 GB of DDR3 RAM
4 GB USB Flash drive (acting as hard drive, from now on I'll call it OS USB drive)
Another USB Flash drive (acting as installation media, I'll call it installation USB drive)

Basically, setup completes successfully, tells me that the installation is ready and I should reboot to continue to the newly installed OS. However, after rebooting, I've getting this message:

[http://sdrv.ms/11CdfII](http://sdrv.ms/11CdfII)

Here are my boot options in UEFI setup (after the installation is complete):

[http://sdrv.ms/11Cdp2I](http://sdrv.ms/11Cdp2I)

Note: neither USB nor UEFI mode booting from OS USB drive works. I'm able to boot from the installation USB drive if I make it first boot option. I can also enter rescue mode through it. Here are the partitions its recognizing:

[http://sdrv.ms/14rH8MX](http://sdrv.ms/14rH8MX)

"fdisk -l" and "efibootmgr -v" outputs after mounting OS partition:

[http://sdrv.ms/14rHe7d](http://sdrv.ms/14rHe7d)

Some files on OS USB drive:

[http://sdrv.ms/14rHhzS](http://sdrv.ms/14rHhzS)
[http://sdrv.ms/14rHmDP](http://sdrv.ms/14rHmDP)

"parted -l" output:

[http://sdrv.ms/14rHnre](http://sdrv.ms/14rHnre)

What I have tried:
 
* Reinstalling whole OS from scratch.
* Clearing all partitions and repartitioning
* Updating BIOS to latest version
* Reinstallating grub through rescue mode to all available partitions (one at a time)

Does anyone have any idea how I can make it work? :/

Thanks in advance!

---

### Post by dino99 on 2013-06-10
an uefi installation overview: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Sunius on 2013-06-10
To make sure it was installed in EFI mode I used two out of three methods of "Identifying if an Ubuntu has been installed in EFI mode" in that link you gave me. Results for /etc/fstab file content:

[http://sdrv.ms/1148JTy](http://sdrv.ms/1148JTy)

Result of "[ -d /sys/firmware/efi ] && echo "Installed in EFI mode" || echo "Installed in Legacy mode"":

[http://sdrv.ms/ZEZ7h3](http://sdrv.ms/ZEZ7h3)

I have no idea how to check if it uses the grub-efi bootloader, though. Any guidance is welcome.

---

### Post by oldfred on 2013-06-10
Post from a live installer the link to BootInfo report. Server installer is not a live installer version.
You can use any Ubuntu live version or download the Boot-Repair CD.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

See also my signature.
If you do not have another flash drive, you can download bootinfoscript which is a terminal list of system. It is also used by Boot-Repair and is about the first third of a BootInfo report. Or BootInfo gives more info especially on UEFI systems.
       Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in advanced  edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by dargaud on 2013-06-11
I haven't looked at all your screenshots, but why don't you simply disable UEFI ? There should be a 'Legacy boot' option somewhere, no ?

---

### Post by Sunius on 2013-06-12
> **dargaud said:**
> I haven't looked at all your screenshots, but why don't you simply disable UEFI ? There should be a 'Legacy boot' option somewhere, no ?

Unfortunately, there isn't such option in the UEFI setup.

@Oldfred: 

Thanks for a very detailed reply. I'll try it and report back.

EDIT:

Here are the results:

```

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 3June2013]


============================= Boot Info Summary: ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 2048.
    Operating System:  
    Boot files:        /EFI/ubuntu/grubx64.efi

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.04 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 4040 MB, 4040724480 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7892040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *            128     7,891,967     7,891,840   b W95 FAT32


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4051 MB, 4051697664 bytes
255 heads, 63 sectors/track, 492 cylinders, total 7913472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1     7,913,471     7,913,471  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048       194,559       192,512 EFI System partition
/dev/sdb2         194,560     7,911,423     7,716,864 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        A002-E277                              vfat       
/dev/sdb1        97E9-2098                              vfat       
/dev/sdb2        d516fa8f-5165-4286-b73f-aa23f203517e   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdb2        /media/ubuntu/d516fa8f-5165-4286-b73f-aa23f203517e ext4       (rw,nosuid,nodev,uhelper=udisks2)


=========================== sda1/boot/grub/grub.cfg: ===========================

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

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

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
set root='hd1,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  d516fa8f-5165-4286-b73f-aa23f203517e
else
  search --no-floppy --fs-uuid --set=root d516fa8f-5165-4286-b73f-aa23f203517e
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-d516fa8f-5165-4286-b73f-aa23f203517e' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd1,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  d516fa8f-5165-4286-b73f-aa23f203517e
    else
      search --no-floppy --fs-uuid --set=root d516fa8f-5165-4286-b73f-aa23f203517e
    fi
    linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=d516fa8f-5165-4286-b73f-aa23f203517e ro   
    initrd    /boot/initrd.img-3.8.0-19-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-d516fa8f-5165-4286-b73f-aa23f203517e' {
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-d516fa8f-5165-4286-b73f-aa23f203517e' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd1,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  d516fa8f-5165-4286-b73f-aa23f203517e
        else
          search --no-floppy --fs-uuid --set=root d516fa8f-5165-4286-b73f-aa23f203517e
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=d516fa8f-5165-4286-b73f-aa23f203517e ro   
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-d516fa8f-5165-4286-b73f-aa23f203517e' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd1,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  d516fa8f-5165-4286-b73f-aa23f203517e
        else
          search --no-floppy --fs-uuid --set=root d516fa8f-5165-4286-b73f-aa23f203517e
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=d516fa8f-5165-4286-b73f-aa23f203517e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
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
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
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
# / was on /dev/sdb2 during installation
UUID=d516fa8f-5165-4286-b73f-aa23f203517e /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb1 during installation
UUID=97E9-2098  /boot/efi       vfat    defaults        0       1
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.869457245 = 0.933572608    boot/grub/grub.cfg                             1
   0.382919312 = 0.411156480    boot/vmlinuz-3.8.0-19-generic                  1
   0.382919312 = 0.411156480    vmlinuz                                        1
   0.382919312 = 0.411156480    vmlinuz.old                                    1
   0.881248474 = 0.946233344    boot/initrd.img-3.8.0-19-generic               2
   0.881248474 = 0.946233344    initrd.img                                     2

========= Devices which don't seem to have a corresponding hard drive: =========

no block devices found 

=============================== StdErr Messages: ===============================

File descriptor 8 (/proc/11214/mounts) leaked on lvscan invocation. Parent PID 18001: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-06-12__06h28 ===================
boot-repair version : 3.199~ppa4~raring
boot-sav version : 3.199~ppa4~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.199~ppa4~raring
boot-repair is executed in live-session (Ubuntu 13.04, raring, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sdb2:Ubuntu 13.04 (13.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="A002-E277" TYPE="vfat"
/dev/sdb1: UUID="97E9-2098" TYPE="vfat"
/dev/sdb2: UUID="d516fa8f-5165-4286-b73f-aa23f203517e" TYPE="ext4"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.



=================== /media/ubuntu/d516fa8f-5165-4286-b73f-aa23f203517e/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
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




=================== /media/ubuntu/d516fa8f-5165-4286-b73f-aa23f203517e/etc/grub.d/ :
drwxr-xr-x 2 root root    4096 Jun 10 08:53 grub.d
total 72
-rwxr-xr-x 1 root root  7541 Apr  9 09:29 00_header
-rwxr-xr-x 1 root root  5974 Apr  9 08:53 05_debian_theme
-rwxr-xr-x 1 root root 11381 Apr  9 09:29 10_linux
-rwxr-xr-x 1 root root 10258 Apr  9 09:29 20_linux_xen
-rwxr-xr-x 1 root root  1688 Dec  5  2012 20_memtest86+
-rwxr-xr-x 1 root root 10976 Apr  9 09:29 30_os-prober
-rwxr-xr-x 1 root root  1426 Apr  9 09:29 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  9 09:29 40_custom
-rwxr-xr-x 1 root root   216 Apr  9 09:29 41_custom
-rw-r--r-- 1 root root   483 Apr  9 09:29 README


/boot/efi detected in the fstab of sdb2: UUID=97E9-2098   (sdb1)
ls /sys/firmware/efi/vars : UsbSupport-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,USB_POINT-8be4df61-93ca-11d2-aa0d-00e098032b8c,UsbMassDevValid-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,UsbMassDevNum-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,Timeout-8be4df61-93ca-11d2-aa0d-00e098032b8c,StdDefaults-4599d26f-1a11-49b8-b91f-858745cff824,StageChk-8f132913-6907-4192-a227-6cbcd7a50e6c,Setup-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,SetupCpuFeatures-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,Setup-80e1202e-2697-4264-9cc9-80762c3e5863,Q_ASR_QUICKON-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,PNP0604_0_VV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0604_0_NV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0510_0_VV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0510_0_NV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0501_1_VV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0501_1_NV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0501_0_VV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0501_0_NV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0400_0_VV-560bf58a-1e0d-4d7e-953f-2980a261e031,PNP0400_0_NV-560bf58a-1e0d-4d7e-953f-2980a261e031,PlatformLangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c,PlatformLang-8be4df61-93ca-11d2-aa0d-00e098032b8c,OldLegacyDevOrder-a56074db-65fe-45f7-bd21-2d2bdd8e9652,new_var,MonotonicCounter-8be4df61-93ca-11d2-aa0d-00e098032b8c,MemCeil.-8be4df61-93ca-11d2-aa0d-00e098032b8c,LoadSetupDefault-8be4df61-93ca-11d2-aa0d-00e098032b8c,LegacyDevOrder-a56074db-65fe-45f7-bd21-2d2bdd8e9652,LangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c,Lang-8be4df61-93ca-11d2-aa0d-00e098032b8c,HiiDB-1b838190-4625-4ead-abc9-cd5e6af18fe0,GoodNightLed-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,ErrOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ErrOut-8be4df61-93ca-11d2-aa0d-00e098032b8c,DtsSetup-bc87e649-2bda-1995-b1e5-3f3ed6f22dc9,del_var,DefaultLegacyDevOrder-3c4ead08-45ae-4315-8d15-a60eaa8caf69,DefaultBootOrder-45cf35f6-0d6e-4d04-856a-0370a5b16f53,CpuS3Resume-30b98b95-dfa3-4501-a3ce-e38c186384a0,ConOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConOut-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConInDev-8be4df61-93ca-11d2-aa0d-00e098032b8c,ConIn-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootOrder-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot_Last_Device-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,Boot_Dev_name-8be4df61-93ca-11d2-aa0d-00e098032b8c,BootCurrent-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0003-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0002-8be4df61-93ca-11d2-aa0d-00e098032b8c,Boot0001-8be4df61-93ca-11d2-aa0d-00e098032b8c,ASR_USER_DEF_VER-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,ASR_USER_DEF_TSE-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,AsrHdasSetup-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,AMITSESetup-c811fa38-42c8-4579-a9bb-60e94eddfb34,AcpiGlobalVariable-af9ffd67-ec10-488a-9dfc-6cbf5ee22c2e,AcpiAslPtr-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,AAFTaddr-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9,
Please report this message to boot.repair@gmail.com
efibootmgr -v
gui-g2slaunch.sh: line 127: efibootmgr: command not found
=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot maybe enabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)


=================== PARTITIONS & DISKS:
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdb1.
sdb2    : sdb,    not-sepboot,    grubenv-ok    grub2,    grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /media/ubuntu/d516fa8f-5165-4286-b73f-aa23f203517e.

sdb    : GPT,    no-BIOS_boot,    has-correctEFI,     usb-disk,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: Ut165 USB Flash Disk (scsi)
Disk /dev/sda: 4041MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      65.5kB  4041MB  4041MB  primary  fat32        boot


Model: JetFlash Transcend 4GB (scsi)
Disk /dev/sdb: 4052MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
1      1049kB  99.6MB  98.6MB  fat32              boot
2      99.6MB  4051MB  3951MB  ext4

=================== parted -lm:

BYT;
/dev/sda:4041MB:scsi:512:512:msdos:Ut165 USB Flash Disk;
1:65.5kB:4041MB:4041MB:fat32::boot;

BYT;
/dev/sdb:4052MB:scsi:512:512:gpt:JetFlash Transcend 4GB;
1:1049kB:99.6MB:98.6MB:fat32::boot;
2:99.6MB:4051MB:3951MB:ext4::;


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sda1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
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
/dev/sdb2 on /media/ubuntu/d516fa8f-5165-4286-b73f-aa23f203517e type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb1 on /mnt/boot-sav/sdb1 type vfat (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet input kmsg log lp0 mapper mcelog mem net network_latency network_throughput null oldmem parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdb2 serial sg0 sg1 shm snapshot snd stderr stdin stdout uinput urandom vga_arbiter vhost-net zero
ls /dev/mapper:  control
ls /mnt/boot-sav/sdb1: /*/*/*/*

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 58 90 6d 6b 64 6f 73  66 73 00 00 02 01 20 00  |.X.mkdosfs.... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 7d 00 00 00 00 00  |........>.}.....|
00000020  00 f0 02 00 c9 05 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 98 20 e9 97 20  20 20 20 20 20 20 20 20  |..). ..         |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  996M   81M  916M   9% /
udev           devtmpfs   984M   12K  984M   1% /dev
tmpfs          tmpfs      200M  796K  199M   1% /run
/dev/sda1      vfat       3.8G  785M  3.0G  21% /cdrom
/dev/loop0     squashfs   738M  738M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      996M  1.1M  995M   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      996M   76K  996M   1% /run/shm
none           tmpfs      100M   32K  100M   1% /run/user
/dev/sdb2      ext4       3.6G  759M  2.7G  22% /media/ubuntu/d516fa8f-5165-4286-b73f-aa23f203517e
/dev/sdb1      vfat        93M  121K   93M   1% /mnt/boot-sav/sdb1

=================== fdisk -l:

Disk /dev/sda: 4040 MB, 4040724480 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7892040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         128     7891967     3945920    b  W95 FAT32

Disk /dev/sdb: 4051 MB, 4051697664 bytes
255 heads, 63 sectors/track, 492 cylinders, total 7913472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1     7913471     3956735+  ee  GPT


EFI detected. Please check the options.

=================== Default settings
Recommended-Repair
This setting would reinstall the grub-efi of sdb2, using the following options:        sdb1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    backup-and-rename-efi-files

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.

```

EDIT2:

Looks like recommended repair fixed it! Thanks a lot, it's been my headache for way longer than it should've been! :)

---

### Post by oldfred on 2013-06-12
Glad Boot-Repair worked. :)

---

