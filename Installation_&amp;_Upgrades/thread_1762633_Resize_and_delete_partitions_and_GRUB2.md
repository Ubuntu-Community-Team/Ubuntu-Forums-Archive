---
title: "Resize and delete partitions and GRUB2"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by frankiethepill on 2011-05-19
I have Ubuntu 11.04 installed in a partition of ~80gb on a 500gb drive. I originally installed an earlier version of Ubuntu on the whole disk, and when I installed 11.04 it for some reason installed the new version on the 80Gb partition. How can I remove the old version and put Ubuntu onto the whole disk (excepting things such as swap partitions etc)? Under windows (sorry) this would be easy, but speaking from bitter experience when I have tried this sort of thing on Ubuntu before everything goes well, until I hit the problem of Grub, and it invariably won't boot properly ever again. 
I have tried to put a screenshot of Gparted onto this message and failed, so I'll write out the disk structure as best as I can

/dev/sda1         extended    458Gb
    /dev/sda6     ext4         69gb       Ubuntu 11.04 partition
    /dev/sda7     ext4        380gb       old Ubuntu partition
    /dev/sda8     linux swap   5.86gb
    unallocated   unallocated  5Mb
    /dev/sda5     linux swap   1.8gb
    /dev/sda2     ntfs         Factory image  7Gb
    unallocated                unallocated     2Mb

What I would like to do is delete the sda7 partition and make the sda6 partition bigger to fill the space up- I am running out of space on the 69Gb partition. My fear is that Grub will then fall over. I know that it is possible to make alterations to the Grub2 config files by booting from a flash card or similar, but I have yet to succeed in this!
Can anyone help?

---

### Post by dino99 on 2011-05-19
into a terminal:

sudo dpkg-reconfigure grub-pc

check that grub is installed on sda (not sda6), then you can format sda7 with gparted (if unmounted only), then you need to rebuilt the grub menu:

sudo update-grub

---

### Post by frankiethepill on 2011-05-19
Thank you- can I delete sda7, and then resize sda6 to take up the free space? 
(Grub is installed on sda- thanks for that)

---

### Post by oldfred on 2011-05-19
Yes you can delete the old install and resize the new. But consider making it a separate /home.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by frankiethepill on 2011-05-21
Have taken your suggestion and moved the home folder to the newer partition- I tried carefully but obviously got it wrong somewhere because I can't boot into the system properly- at my login all I get is a prompt at the top of the screen telling me that there is an 'install problem' and that default configurations for Gnome power manager have not been installed properly. 
Any ideas as to where I go from here? I can login using a live disk so I can make alterations to Fstab etc but atm can't see too much that is wrong. Have a feeling that there may be an issue with ownership of the new home directory but can't seem to change the permissions

---

### Post by oldfred on 2011-05-21
I think one of the sites on moving home mentions this:

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name or use $USER
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

---

### Post by Hedgehog1 on 2011-05-21
> **frankiethepill said:**
> 
Any ideas as to where I go from here? I can login using a live disk so I can make alterations to Fstab etc but atm can't see too much that is wrong. Have a feeling that there may be an issue with ownership of the new home directory but can't seem to change the permissions

frankiethepill,

If the **chown** commands from **oldfred** did not resolve the issue, then the problem may not be ownership.

If you have run those commands and are still having issues, please do this:

Boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by frankiethepill on 2011-05-22
Thank you for these two replies- can't use the computer at the moment, but will try tomorrow morning and report back. 
Kind regards
Francis

---

### Post by frankiethepill on 2011-05-23
Been able to get to the computer again- the ownership issues etc seem to have made no difference, so I tried Hedgehog1's suggestion and here is the result:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /BOOT/BCD

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>..............0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 5086704 of /dev/sdf1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdf1 starts at sector 
                       0. But according to the info from fdisk, sdf1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,046   961,277,951   961,275,906   5 Extended
/dev/sda5         957,372,416   961,277,951     3,905,536  82 Linux swap / Solaris
/dev/sda6               2,048   146,486,422   146,484,375  83 Linux
/dev/sda7         146,487,296   945,074,175   798,586,880  83 Linux
/dev/sda8         945,076,224   957,362,175    12,285,952  82 Linux swap / Solaris
/dev/sda2         961,277,952   976,769,023    15,491,072   7 NTFS / exFAT / HPFS


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *             62     7,826,383     7,826,322   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       bd20422d-cdf9-4711-a2dc-127a0a7a7b02   ext3       
/dev/sda2        EEBA6A1DBA69E297                       ntfs       FACTORY_IMAGE
/dev/sda5        8c736e39-a23f-4f9f-9d1b-9da22d3da9a9   swap       
/dev/sda6        3d510f14-f2c3-40f7-8a6a-73c4a94d7ad5   ext4       
/dev/sda7        003e8924-e6d0-469a-b3b2-ea5ee11824d3   ext4       
/dev/sda8        f5e95c03-2ee1-42e0-997e-144d532ab75b   swap       
/dev/sdf1        94C1-C494                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdf1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 3d510f14-f2c3-40f7-8a6a-73c4a94d7ad5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 3d510f14-f2c3-40f7-8a6a-73c4a94d7ad5
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
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 3d510f14-f2c3-40f7-8a6a-73c4a94d7ad5
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=3d510f14-f2c3-40f7-8a6a-73c4a94d7ad5 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 3d510f14-f2c3-40f7-8a6a-73c4a94d7ad5
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=3d510f14-f2c3-40f7-8a6a-73c4a94d7ad5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 3d510f14-f2c3-40f7-8a6a-73c4a94d7ad5
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=3d510f14-f2c3-40f7-8a6a-73c4a94d7ad5 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 3d510f14-f2c3-40f7-8a6a-73c4a94d7ad5
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=3d510f14-f2c3-40f7-8a6a-73c4a94d7ad5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 3d510f14-f2c3-40f7-8a6a-73c4a94d7ad5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 3d510f14-f2c3-40f7-8a6a-73c4a94d7ad5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root EEBA6A1DBA69E297
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root ce9ff892-b056-4c0c-817e-889211bb4390
	linux /vmlinuz root=/dev/sda7
	initrd /initrd.img
}
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root ce9ff892-b056-4c0c-817e-889211bb4390
	linux /vmlinuz root=/dev/sda7
	initrd /initrd.img
}
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root ce9ff892-b056-4c0c-817e-889211bb4390
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda7
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root ce9ff892-b056-4c0c-817e-889211bb4390
	linux /vmlinuz root=/dev/sda7
	initrd /initrd.img
}
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root ce9ff892-b056-4c0c-817e-889211bb4390
	linux /vmlinuz root=/dev/sda7
	initrd /initrd.img
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
# Commented out by Dropbox
# UUID=3d510f14-f2c3-40f7-8a6a-73c4a94d7ad5 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
#UUID=8c736e39-a23f-4f9f-9d1b-9da22d3da9a9 / ext4 errors=remount-ro,user_xattr 0 1

# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=003e8924-e6d0-469a-b3b2-ea5ee11824d3   /home    ext4          nodev,nosuid       0       2 

#UUID=3d510f14-f2c3-40f7-8a6a-73c4a94d7ad5 /               ext4    errors=remount-ro 0       1
#/dev/sda5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.135524750 = 0.145518592    boot/grub/core.img                             1
   1.489604950 = 1.599451136    boot/grub/grub.cfg                             1
  31.785728455 = 34.129666048   boot/initrd.img-2.6.35-28-generic              2
  34.059833527 = 36.571467776   boot/initrd.img-2.6.38-8-generic               2
   0.590396881 = 0.633933824    boot/vmlinuz-2.6.35-28-generic                 1
  33.653625488 = 36.135305216   boot/vmlinuz-2.6.38-8-generic                  1
  34.059833527 = 36.571467776   initrd.img                                     2
  31.785728455 = 34.129666048   initrd.img.old                                 2
  33.653625488 = 36.135305216   vmlinuz                                        1
   0.590396881 = 0.633933824    vmlinuz.old                                    1

========================= sdf1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdf1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdf1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Downloads/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```


Hope it means something to you. I expect it will show what a **** I've been....!

---

### Post by oldfred on 2011-05-23
It looks like you comment out both of the entries you have for / (root) in fstab.

```
# / was on /dev/sda6 during installation
# Commented out by Dropbox
# UUID=3d510f14-f2c3-40f7-8a6a-73c4a94d7ad5 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
[COLOR=Black]#UUID=8c736e39-a23f-4f9f-9d1b-9da22d3da9a9 / ext4 errors=remount-ro,user_xattr 0 1
[/COLOR]
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=003e8924-e6d0-469a-b3b2-ea5ee11824d3   /home    ext4          nodev,nosuid       0       2 

[COLOR=Red]#UUID=3d510f14-f2c3-40f7-8a6a-73c4a94d7ad5 /               ext4    errors=remount-ro 0       1[/COLOR]
#/dev/sda5       none            swap    sw              0       0

```

The red entry should be uncommented, remove hash (#). This is sda6 your root partition.
/dev/sda6        3d510f14-f2c3-40f7-8a6a-73c4a94d7ad5   ext4

---

### Post by frankiethepill on 2011-05-24
Didn't work...
Am going to start again and reinstall- probably easier in the long run.
Thanks for all the help

---

### Post by oldfred on 2011-05-24
If you moved all your data to the new partition from /home, be sure to choose that partition as /home but DO NOT format it. 

You also just select your current / partition and what format ext3 or ext4 you want. It will find you current swap.

---

