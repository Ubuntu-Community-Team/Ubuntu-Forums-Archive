---
title: "Yet another dual boot thread..."
date: 2012-04-21
forum: Installation &amp; Upgrades
---

### Post by Isl1ngt0n on 2012-04-21
So here's what I've got, a dell latitude 5510 with a 500 gig drive with W7 64 bit installed that I would like to have dual boot with 64 bit Ubuntu to run virtual machines.  So far I've tried the 4 partition method which results in a grub partition that is for some reason incapable of being properly set to see the root partition.  I've tried putting grub in the MBR and that leaves me with a system that boots straight to the grub rescue prompt.  I've tried manually configuring grub with no success, grub steadfastly refuses to recognize the file system on the root directory.  Grub rescue has done me no good, and I've attempted the boot repair app with no success.  I've tried 11.04, 11.10, and 12.04 all with basically the same results, if I setup a boot partition I get the grub prompt and no ability to recognize the appropriate drive to boot from, and if I go MBR I get the grub rescue prompt.  Any help or clarifications would be greatly appreciated, thanks. Oh and before anybody suggests drive failure, while not impossible would be highly unlikely, I just replaced the drive a month ago and w7 runs perfectly fine with no issue.

---

### Post by darkod on 2012-04-21
The disk is not dynamic in windows is it?

Also, I guess you are using msdos partition table and not gpt.

From ubuntu live mode (Try Ubuntu), post the results of:
sudo fdisk -l (small L)

Or even better, run the boot info script from the link in my signature and post the results. It will show more details of what you have.

It might be some error or corruption in the partition table too.

---

### Post by Isl1ngt0n on 2012-04-21
Here you go, this was run on my usb boot.

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

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
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu precise (development 
                       branch)
    Boot files:        /etc/fstab

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 4664554 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   335,546,367   335,339,520   7 NTFS / exFAT / HPFS
/dev/sda3         335,546,368   336,070,655       524,288  83 Linux
/dev/sda4         336,070,656   976,773,119   640,702,464   5 Extended
/dev/sda5         336,072,704   357,044,223    20,971,520  83 Linux
/dev/sda6         357,046,272   419,960,831    62,914,560  83 Linux
/dev/sda7         419,962,880   424,157,183     4,194,304  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8004 MB, 8004304896 bytes
255 heads, 63 sectors/track, 973 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    15,632,383    15,630,336   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048    31,266,815    31,264,768   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       08510def-d3ab-ba4a-b7cc-f6b4e84b2ac7   ext2       casper-rw
/dev/sda1        62A4DFECA4DFC0A9                       ntfs       System Reserved
/dev/sda2        7060F13E60F10C1A                       ntfs       
/dev/sda3        dbfd0ef1-848a-402b-87b3-060f2a7f6102   ext3       
/dev/sda5        099195bb-5ac7-4f7e-958a-dae697b2137e   ext4       
/dev/sda6        c0475fd5-1deb-4078-877c-9ab73ac3e62d   ext4       
/dev/sdb1        9092D7C492D7ACCA                       ntfs       
/dev/sdc1        12F7-1A21                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/9092D7C492D7ACCA  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


============================= sda3/grub/grub.cfg: ==============================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 099195bb-5ac7-4f7e-958a-dae697b2137e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root dbfd0ef1-848a-402b-87b3-060f2a7f6102
  set locale_dir=($root)/grub/locale
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
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
menuentry 'Ubuntu, with Linux 3.2.0-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root dbfd0ef1-848a-402b-87b3-060f2a7f6102
	linux	/vmlinuz-3.2.0-20-generic root=UUID=099195bb-5ac7-4f7e-958a-dae697b2137e ro   quiet splash vt.handoff=7
	initrd	/initrd.img-3.2.0-20-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root dbfd0ef1-848a-402b-87b3-060f2a7f6102
	echo	'Loading Linux 3.2.0-20-generic ...'
	linux	/vmlinuz-3.2.0-20-generic root=UUID=099195bb-5ac7-4f7e-958a-dae697b2137e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root dbfd0ef1-848a-402b-87b3-060f2a7f6102
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root dbfd0ef1-848a-402b-87b3-060f2a7f6102
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 62A4DFECA4DFC0A9
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 7060F13E60F10C1A
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

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  2
               =                grub/grub.cfg                                  1
               =                initrd.img-3.2.0-20-generic                   86
               =                vmlinuz-3.2.0-20-generic                      20

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=099195bb-5ac7-4f7e-958a-dae697b2137e /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=dbfd0ef1-848a-402b-87b3-060f2a7f6102 /boot           ext3    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=c0475fd5-1deb-4078-877c-9ab73ac3e62d /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
#UUID=3ebfa6dd-0f20-46d5-baa8-c07266d985fe none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

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

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
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

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
```

---

### Post by darkod on 2012-04-21
Look like grub2 wasn't installed on the MBR, only that. You can try to add it from live mode with the cd. Because you also installed a /boot partition you will have to mount it too.

In terminal in live mode try:
sudo mount /dev/sda5 /mnt
sudo mount /dev/sda3 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda

Restart and see if it helped.

---

### Post by Isl1ngt0n on 2012-04-21
Nope, sends me straight to the grub rescue prompt.

---

### Post by darkod on 2012-04-21
How about if you modify the third command into:
sudo grub-install --boot-directory=/mnt/boot /dev/sda

The first two remain the same.

---

### Post by Isl1ngt0n on 2012-04-21
That one did it, thanks!

---

