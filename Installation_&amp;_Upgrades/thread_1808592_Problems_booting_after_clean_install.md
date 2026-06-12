---
title: "Problems booting after clean install"
date: 2011-07-20
forum: Installation &amp; Upgrades
---

### Post by q41 on 2011-07-20
I installed Ubuntu 11.04 today. When I try to boot it my laptop freezes after displaying "Loading initial ramdisk". I searched for hours for a solution but still don't have a clue about what is going on here. Things I tried:
- booting in recovery mode
- reinstalling & reconfiguring GRUB2
- adding 'nomodeset' as a boot parameter in grub.
- reinstalling
They do not seem to have any effect though.

The really weird thing is, the 6th time or so my laptop booted, it booted just fine. I could however not reproduce this until the...err...15th? time. Once in a while my installation randomly decides to work apparently...

If any helpful suggestion would be appreciated.

---

### Post by q41 on 2011-07-21
I've attached the output of the boot info script, in case it is of any help.

---

### Post by Quackers on 2011-07-21
I've had a look at your boot script output (shown below in code tags) but I see nothing wrong.
What's in sda3? It's listed as Linux but isn't mounted as /home in /etc/fstab.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:   Syslinux looks at sector 7860 of /dev/sdb1 for its 
                       second stage. According to the info in the boot 
                       sector, sdb1 starts at sector 0. But according to the 
                       info from fdisk, sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.......`......0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1438080 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 32.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    41,945,714    41,945,652  83 Linux
/dev/sda2          41,945,715    46,138,679     4,192,965  82 Linux swap / Solaris
/dev/sda3          46,138,680   180,361,754   134,223,075  83 Linux
/dev/sda4    *    180,361,755   312,576,704   132,214,950   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2055 MB, 2055208960 bytes
64 heads, 62 sectors/track, 1011 cylinders, total 4014080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     4,011,647     4,011,586   c W95 FAT32 (LBA)


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 16.1 GB, 16131293184 bytes
64 heads, 32 sectors/track, 15384 cylinders, total 31506432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             32    31,506,431    31,506,400   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7e74ea19-1c14-42fc-a507-06669087b222   ext4       
/dev/sda2        56e7fe63-0d9e-499d-a2df-b8096aba066d   swap       
/dev/sda3        ebb1faea-bd6b-4b85-9564-2678346bb619   ext4       data
/dev/sda4        624EDB2B4EDAF6AF                       ntfs       
/dev/sdb1        F185-5906                              vfat       
/dev/sdc1        3798-A753                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc1        /media/3798-A753         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
search --no-floppy --fs-uuid --set=root 7e74ea19-1c14-42fc-a507-06669087b222
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 7e74ea19-1c14-42fc-a507-06669087b222
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
	search --no-floppy --fs-uuid --set=root 7e74ea19-1c14-42fc-a507-06669087b222
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=7e74ea19-1c14-42fc-a507-06669087b222 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 7e74ea19-1c14-42fc-a507-06669087b222
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=7e74ea19-1c14-42fc-a507-06669087b222 ro single 
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
	search --no-floppy --fs-uuid --set=root 7e74ea19-1c14-42fc-a507-06669087b222
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 7e74ea19-1c14-42fc-a507-06669087b222
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda4)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root 624EDB2B4EDAF6AF
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
UUID=7e74ea19-1c14-42fc-a507-06669087b222 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=56e7fe63-0d9e-499d-a2df-b8096aba066d none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   4.352988720 = 4.673986048    boot/grub/core.img                             1
   2.410525799 = 2.588282368    boot/grub/grub.cfg                             1
   1.887694836 = 2.026896896    boot/initrd.img-2.6.38-8-generic               2
   4.403411388 = 4.728126976    boot/vmlinuz-2.6.38-8-generic                  1
   1.887694836 = 2.026896896    initrd.img                                     2
   4.403411388 = 4.728126976    vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by q41 on 2011-07-21
Just my data partition. I was planning on adding it to fstab after the installation.

---

### Post by Quackers on 2011-07-22
If you want to share data between Ubuntu and Windows system I believe NTFS is a better format.
In the absence of any furhter input and in view of the fact that you have re-installed grub I can only suggest that you re-install the system. Maybe something didn't go quite right first time.

---

### Post by q41 on 2011-07-22
I already installed Ubuntu several times...

I was wondering whether it maybe could have to do something with the video driver. I never used Maverick because it always crashed after I installed the proprietary nvidia driver. I, off course, never got around to testing the driver on Natty, but maybe these problems have similar causes?

Is there any other way I could acquire information to help find the problem? Is something logged maybe during this phase of the boot process? Or during the installation?

p.s. ntfs-3g is not very nice (as in 100% CPU not nice) when you boot VMware images off of it. So I prefer ext ;)

---

### Post by Quackers on 2011-07-22
What is your graphics card and which driver did you use? How did you install that driver?

---

### Post by q41 on 2011-07-22
My graphics card is an NVIDIA GeForce 8600 GT. I installed it (on previous versions of Ubuntu) using the System > Administration > Addiditional Drivers utilities. The last version that worked (on Lucid) was version: 195.36.24

---

### Post by Quackers on 2011-07-22
Yes, version 195.36.24 was the nvidia-current driver at that time. It is now a larger number.
Obviously if you are not currently using the Nvidia driver it is not causing your current booting problems.
If you are seeing the grub menu when you boot (if not tap the shift key or the Esc key during boot), with the current Ubuntu version highlighted press the "e" key.
On the next screen using the arrow keys, navigate to the end of the line that currently ends with "quiet splash", then using the backspace key delete those two words then press ctrl + x to boot.
This will produce many lines of text on your screen. Wherever it stops might give us a clue as to why it has stopped. Make a note of the last couple of lines and post here please.

---

### Post by q41 on 2011-07-22
As mentioned in my first post, "Loading initial ramdisk" is the last line that is printed. Before that it only prints it's loading the kernel I believe. In any case, nothing unusual. This is the same output when booting in recovery mode.

---

### Post by dino99 on 2011-07-22
stupid question, but:

how is bios set for booting ? might be on this hdd used by grub

on boot line (hold "shift" key down to unhide grub menu at bios end process) remove "quiet splash" to let you see all the booting comments

be sure you dont have usb hardware plugged

and if you already have an other kernel installed, try to boot on it.

---

### Post by q41 on 2011-07-22
I've done a clean install, so there are unfortunatelly no older kernels installed. As for the bios settings, I'm not sure what you're getting at, but the it is certainly the correct disk that is booted from. The grub menu also lists my windows 7 installation correctly and that boots just fine.

Might there be a way to install Natty with a different kernel or install this afterwards from a live usb stick?

---

