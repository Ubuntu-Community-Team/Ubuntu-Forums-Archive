---
title: "GRUB deleted my ubuntu after dual-boot"
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by drz on 2011-07-22
Hi there.
I'm quite new to linux - so please bear with me.

Two days ago i decided to try dual-boot crunchbang, and now ubuntu is inaccessible, what am I doing wrong ?
I tried update-grub with no luck.
I've been searching google for hours now, I'd be grateful if anyone could point me how to get it back ?
Thank you.

Some details
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003a470

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1034     8299520   82  Linux swap / Solaris
/dev/sda2            1034        7187    49422336   83  Linux
/dev/sda3            7187       60802   430661633    5  Extended
/dev/sda5            7187       36487   235350016   83  Linux
/dev/sda6           36487       49422   103905280   83  Linux
/dev/sda7   *       49422       50638     9764864   83  Linux
/dev/sda8           50638       51050     3307520   82  Linux swap / Solaris
/dev/sda9           51050       60802    78329856   83  Linux

```

ps. please let me know if you want me to provide anything else.

---

### Post by thefasterblueone on 2011-07-22
Did you run "update-grub" as root?

Here is a link to [Boot Info Script](http://bootinfoscript.sourceforge.net/), after running it, copy and paste the results in the code tags ( # ) for better viewing.

---

### Post by drz on 2011-07-22
Hi, thanks for replying
yes i run update-grub as root, here's the result
```
drz@tuff-gong:~$ sudo update-grub
Generating grub.cfg ...
Found background image: grub-splash-crunchbang.png
Found linux image: /boot/vmlinuz-2.6.32-5-amd64
Found initrd image: /boot/initrd.img-2.6.32-5-amd64
done
```

and here's boot_info_script result
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for (,msdos7)/boot/grub.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  CrunchBang Linux statler
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    16,601,087    16,599,040  82 Linux swap / Solaris
/dev/sda2          16,601,088   115,445,759    98,844,672  83 Linux
/dev/sda3         115,447,806   976,771,071   861,323,266   5 Extended
/dev/sda5         115,447,808   586,147,839   470,700,032  83 Linux
/dev/sda6         586,149,888   793,960,447   207,810,560  83 Linux
/dev/sda7    *    793,962,496   813,492,223    19,529,728  83 Linux
/dev/sda8         813,494,272   820,109,311     6,615,040  82 Linux swap / Solaris
/dev/sda9         820,111,360   976,771,071   156,659,712  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        81c543a6-e2d5-4417-826a-0c6be68e2983   swap       
/dev/sda2        9b151480-70a6-488d-9f0c-748a69f802ec   ext4       
/dev/sda5        9c60ca0a-f777-4c3d-a0f9-c96384cd3fbb   ext4       
/dev/sda6        476d2c85-ab8b-4ef9-b082-ed5a5b7519cc   ext4       
/dev/sda7        599e1120-7253-4937-bc99-cd0d01e6ad18   ext4       
/dev/sda8        f29f3e50-2bc9-45de-9c68-80fd1f7abdec   swap       
/dev/sda9        3a09f0bd-e353-4dd5-8d8c-c1afc13c980b   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,noatime,errors=remount-ro)
/dev/sda9        /home                    ext4       (rw)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 9b151480-70a6-488d-9f0c-748a69f802ec
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 9b151480-70a6-488d-9f0c-748a69f802ec
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 9b151480-70a6-488d-9f0c-748a69f802ec
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=9b151480-70a6-488d-9f0c-748a69f802ec ro   quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 9b151480-70a6-488d-9f0c-748a69f802ec
	echo	'Loading Linux 2.6.35-30-generic ...'
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=9b151480-70a6-488d-9f0c-748a69f802ec ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 9b151480-70a6-488d-9f0c-748a69f802ec
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=9b151480-70a6-488d-9f0c-748a69f802ec ro   quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 9b151480-70a6-488d-9f0c-748a69f802ec
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=9b151480-70a6-488d-9f0c-748a69f802ec ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 9b151480-70a6-488d-9f0c-748a69f802ec
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 9b151480-70a6-488d-9f0c-748a69f802ec
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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=9b151480-70a6-488d-9f0c-748a69f802ec /               ext4    errors=remount-ro 0       1
# /data was on /dev/sda6 during installation
UUID=476d2c85-ab8b-4ef9-b082-ed5a5b7519cc /data           ext4    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=9c60ca0a-f777-4c3d-a0f9-c96384cd3fbb /home           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=81c543a6-e2d5-4417-826a-0c6be68e2983 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             2
            ?? = ??             boot/initrd.img-2.6.35-22-generic              2
            ?? = ??             boot/initrd.img-2.6.35-30-generic              2
            ?? = ??             boot/vmlinuz-2.6.35-22-generic                 1
            ?? = ??             boot/vmlinuz-2.6.35-30-generic                 1
            ?? = ??             initrd.img                                     2
            ?? = ??             initrd.img.old                                 2
            ?? = ??             vmlinuz                                        1
            ?? = ??             vmlinuz.old                                    1

=========================== sda7/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 599e1120-7253-4937-bc99-cd0d01e6ad18
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 599e1120-7253-4937-bc99-cd0d01e6ad18
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 599e1120-7253-4937-bc99-cd0d01e6ad18
insmod png
if background_image /usr/share/images/desktop-base/grub-splash-crunchbang.png ; then
  set color_normal=light-gray/black
  set color_highlight=black/white
else
  set menu_color_normal=light-gray/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'CrunchBang Linux, with Linux 2.6.32-5-amd64' --class debian --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 599e1120-7253-4937-bc99-cd0d01e6ad18
	echo	'Loading Linux 2.6.32-5-amd64 ...'
	linux	/boot/vmlinuz-2.6.32-5-amd64 root=UUID=599e1120-7253-4937-bc99-cd0d01e6ad18 ro  quiet splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-5-amd64
}
menuentry 'CrunchBang Linux, with Linux 2.6.32-5-amd64 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 599e1120-7253-4937-bc99-cd0d01e6ad18
	echo	'Loading Linux 2.6.32-5-amd64 ...'
	linux	/boot/vmlinuz-2.6.32-5-amd64 root=UUID=599e1120-7253-4937-bc99-cd0d01e6ad18 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-5-amd64
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=599e1120-7253-4937-bc99-cd0d01e6ad18 /               ext4    noatime,errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=3a09f0bd-e353-4dd5-8d8c-c1afc13c980b /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=f29f3e50-2bc9-45de-9c68-80fd1f7abdec none            swap    sw              0       0
#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/initrd.img-2.6.32-5-amd64                 2
            ?? = ??             boot/vmlinuz-2.6.32-5-amd64                    1
            ?? = ??             initrd.img                                     2
            ?? = ??             vmlinuz                                        1


```

---

### Post by varunendra on 2011-07-23
You may find very useful info on grub2, and maybe an easier solution in this thread: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I personally think the version of grub in crunchbang being older may be the cause why it is unable to detect Ubuntu 10.10. Accordingly, I'd suggest to reinstall newer grub from ubuntu 10.10 live cd, mounting /dev/sda2 (ubuntu 10.10 partition) as root directory for grub. You can do so as follows (mind the spaces in the commands. just copy-past them if you have doubts):

[LIST=1]
[*]Boot from Ubuntu 10.10 live cd
[*]mount sda1 to /mnt directory: ```
sudo mount /dev/sda1 /mnt
```
[*]reinstall grub2: ```
sudo grub-install --root-directory=/mnt /dev/sda
```
[*]reboot the computer. This time it should boot into ubuntu 10.10.
[*]update grub to include your crunchbang installation in its menu: ```
sudo update-grub
```
[/LIST]
In case of problems, please post back the errors you get. Let us know how it goes. Thanks.

---

### Post by leilei1 on 2011-07-23
Try doing a fsck on sda2. "fsck sda2"

---

### Post by garvinrick4 on 2011-07-23
I do not believe chrunch-bang distro has os-prober installed with grub2. Thats what
it looks like anyway, never used crunch-bang at all. verunendra's post will give grub to Ubuntu so will work of course.
Would like to see if installing os-prober in that disto and then updating grub will work.
EDIT: This won't work just saw os-prober in output of script nothing in it but there.

---

