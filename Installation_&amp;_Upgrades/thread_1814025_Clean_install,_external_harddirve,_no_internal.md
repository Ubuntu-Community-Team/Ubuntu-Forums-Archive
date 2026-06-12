---
title: "Clean install, external harddirve, no internal"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by Sigudian on 2011-07-28
Trying to do a clean install Ubuntu on an external harddrive.
I have no internal harddrives today in this computer.

When the installation is finished and i try to boot i get,
error file not found, and i get to the grub rescue console.


The install is fine, but grub is messed up.
I know its possible to set up grub to do almost anything,
but I've never used it on anything but automatic.

---

### Post by lmarmisa on 2011-07-28
> **Sigudian said:**
> Trying to do a clean install Ubuntu on an external harddrive.
I have no internal harddrives today in this computer.

When the installation is finished and i try to boot i get,
error file not found, and i get to the grub rescue console.


The install is fine, but grub is messed up.
I know its possible to set up grub to do almost anything,
but I've never used it on anything but automatic.

Did you install the grub loader in the MBR of your external hard drive?.

Try to run the Info Boot Script and post the results:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Sigudian on 2011-07-29
Thanks for the reply, I am at work now but I am gonna see what this script gives back tonight :D

---

### Post by Sigudian on 2011-07-29
sda is the 500gig external I am trying to get booting.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>..........V...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1445280 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   968,384,511   968,382,464  83 Linux
/dev/sda2         968,386,558   976,771,071     8,384,514   5 Extended
/dev/sda5         968,386,560   976,771,071     8,384,512  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4051 MB, 4051697664 bytes
125 heads, 62 sectors/track, 1021 cylinders, total 7913472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,912,749     7,912,688   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6febc99f-5c7f-4b1f-a9ee-127a89ffdd23   ext4       
/dev/sda5        92cd3468-a838-4931-8166-abe1fb08f8b1   swap       
/dev/sdb1        EB3D-1275                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 6febc99f-5c7f-4b1f-a9ee-127a89ffdd23
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 6febc99f-5c7f-4b1f-a9ee-127a89ffdd23
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 6febc99f-5c7f-4b1f-a9ee-127a89ffdd23
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=6febc99f-5c7f-4b1f-a9ee-127a89ffdd23 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 6febc99f-5c7f-4b1f-a9ee-127a89ffdd23
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=6febc99f-5c7f-4b1f-a9ee-127a89ffdd23 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 6febc99f-5c7f-4b1f-a9ee-127a89ffdd23
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 6febc99f-5c7f-4b1f-a9ee-127a89ffdd23
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=6febc99f-5c7f-4b1f-a9ee-127a89ffdd23 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=92cd3468-a838-4931-8166-abe1fb08f8b1 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 140.135513306 = 150.469361664  boot/grub/core.img                             1
 140.135520935 = 150.469369856  boot/grub/grub.cfg                             1
 373.529548645 = 401.074298880  boot/initrd.img-2.6.38-8-generic               2
 140.133792877 = 150.467514368  boot/vmlinuz-2.6.38-8-generic                  1
 373.529548645 = 401.074298880  initrd.img                                     2
 140.133792877 = 150.467514368  vmlinuz                                        1

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

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by lmarmisa on 2011-07-29
The info looks good. 

Have you checked the BIOS menu in order to verify that the external drive is defined as the first priority device?.

Are you able to identify the file not found?.

---

### Post by Sigudian on 2011-07-30
The BIOS menu points to the device,
after POST it goes to the harddrive which has grub2 installed
and drops to grub2's recovery console.

It boots fine from a live USB environment.


Is there anyway in the grub2 recovery console I can troubleshoot?
Or as a pseudo solution, how can I setup grub on usb flash drive to
boot from this harddrive?

---

### Post by YesWeCan on 2011-07-30
See section 8.5 here: [https://help.ubuntu.com/community/Grub2#GRUB%202%20Prompt%20Usage](https://help.ubuntu.com/community/Grub2#GRUB%202%20Prompt%20Usage)
If you manage to boot it you should run
sudo update-grub
sudo grub-install /dev/sda

---

### Post by Sigudian on 2011-07-30
Can i do this from an live environment?

do i just skip the first command?

the harddrive im trying to use shows as sda in the live environment.

---

### Post by YesWeCan on 2011-07-30
Boot the external HD and get to the grub rescue> prompt
Then follow the instructions in section "Rescue Mode ("grub rescue>") Booting".
Use the drive name (hd0,1).
Once you have booted into Ubuntu then run the Grub update and install commands.

These are the grub rescue> commands that I have used successfully:
```
rescue> set prefix=(hd0,1)/boot/grub
rescue> insmod (hd0,1)/boot/grub/linux.mod
rescue> set root=(hd0,1)
rescue> linux /vmlinuz root=/dev/sda1 ro
rescue> initrd /initrd.img
rescue> boot
```

If it complains it can't recognise (hd0,1) then type 'ls' at the prompt and post the output.

---

### Post by Sigudian on 2011-07-30
Thanks a bunch, will try it as soon as im done here at work!! :D

---

### Post by Sigudian on 2011-07-30
> **YesWeCan said:**
> Boot the external HD and get to the grub rescue> prompt
Then follow the instructions in section "Rescue Mode ("grub rescue>") Booting".
Use the drive name (hd0,1).
Once you have booted into Ubuntu then run the Grub update and install commands.

These are the grub rescue> commands that I have used successfully:
```
rescue> set prefix=(hd0,1)/boot/grub
rescue> insmod (hd0,1)/boot/grub/linux.mod
rescue> set root=(hd0,1)
rescue> linux /vmlinuz root=/dev/sda1 ro
rescue> initrd /initrd.img
rescue> boot
```

If it complains it can't recognise (hd0,1) then type 'ls' at the prompt and post the output.


It does not complain about (hd0,1)
it complains after the second line at insmod.

"error: file not found."

EDIT:
I ran the other commands and the linux and initrd and boot commands dont work. Im guessing thats because the linux.mod file is not loaded??

EDIT2:
I ran ls on inside the drives, and it posts the content of the drive when i point ls to (hd0,1) and (hd0,msdos1). When I try to ls the contents of those folders i get nothing. When booting to a live environment where i have access to the drive I can see that the linux.mod file is in fact at the location you said.

---

### Post by oldfred on 2011-07-30
We see this occasionally with larger hard drives and one very large / (root) partition.

I think the real issue is a BIOS setting is not correct. But a quick fix to to have an install with a smaller / and large /home for your data. You can quickly test this by using gparted to shrink the sda1 partition to anything less than 50-100GB. Since you do not have much data it should shrink relatively fast. If that works, you can either move /home to a new partition for the rest of the drive or reinstall with two partitions & swap.

BIOS issues discussed here on SSD drive:
BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

---

### Post by Sigudian on 2011-07-30
> **oldfred said:**
> We see this occasionally with larger hard drives and one very large / (root) partition.

I think the real issue is a BIOS setting is not correct. But a quick fix to to have an install with a smaller / and large /home for your data. You can quickly test this by using gparted to shrink the sda1 partition to anything less than 50-100GB. Since you do not have much data it should shrink relatively fast. If that works, you can either move /home to a new partition for the rest of the drive or reinstall with two partitions & swap.

BIOS issues discussed here on SSD drive:
BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

Thanks, I always use this... the only reason I did not was cause I'm getting a SSD soon and I thought Id reinstall then. xD Thats what I get for breaking routine :P

Gonna try it out now and report back! :)

---

### Post by Sigudian on 2011-07-30
Thanks it worked!

---

