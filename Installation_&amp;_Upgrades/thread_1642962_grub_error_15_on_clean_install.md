---
title: "grub error 15 on clean install"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by pickarooney on 2010-12-11
I reformatted my root partition and boot partitions and installed ,averick but zhen I boot I get a grub 15 error. I might have made a mistake on the partitioning screen zhen I selected /dev/dsa6 for the GRUB bootloader - this is my dedicated /boot partition - and don't know how to fix it now

my current fstab is
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=94e510c4-b762-460f-9a65-27e68887966d /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=c3111ca5-13cc-4042-bcc4-9a31aef7622c /boot           ext3    defaults        0       2
# /home was on /dev/sda4 during installation
UUID=6aca9cac-5354-4183-bf88-68e9e62bed9a /home           ext3    defaults        0       2
# /media/backup was on /dev/sdc2 during installation
UUID=D6F8-0339  /media/backup   vfat    utf8,umask=007,gid=46 0       1
# /media/bigbastard was on /dev/sdb1 during installation
UUID=403e1522-05cc-4cd7-9d16-0a00e8b2409b /media/bigbastard ext3    defaults        0       2
# /media/supersize was on /dev/sdc1 during installation
UUID=a138972b-a839-4285-b048-77660796538f /media/supersize ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=fad2fdc5-26da-4080-ba6b-048f80f7cec9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

I can't access my home folder to see the copy of fstab from before the reinstall.

By mounting all partitions one by one I can see now that everything has moved around so that

sda is the bigbastard drive - 500GB - that was sdb previously
sdb is supersize/basckup and was sdc before
the paritions on sda have moved to sdc

I have no idea hot to put everything back

help please!

---

### Post by pickarooney on 2010-12-11
RESULTS.txt from the boot script gives this

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Lilo is installed in the MBR of /dev/sdb
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 377063 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sdc4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   204,796,619   204,796,557  83 Linux
/dev/sdb2         204,796,620   398,283,479   193,486,860   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     2,040,254     2,040,192  83 Linux
/dev/sdc2         384,708,616   390,716,864     6,008,249   5 Extended
/dev/sdc5         384,708,618   390,716,864     6,008,247  82 Linux swap / Solaris
/dev/sdc3           2,040,255    83,955,689    81,915,435  83 Linux
/dev/sdc4          83,955,690   384,708,554   300,752,865  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        403e1522-05cc-4cd7-9d16-0a00e8b2409b   ext3       magnum                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        a138972b-a839-4285-b048-77660796538f   ext3       supersize                     
/dev/sdb2        D6F8-0339                              vfat                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        c3111ca5-13cc-4042-bcc4-9a31aef7622c   ext3                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc3        94e510c4-b762-460f-9a65-27e68887966d   ext3                                     
/dev/sdc4        6aca9cac-5354-4183-bf88-68e9e62bed9a   ext3                                     
/dev/sdc5        fad2fdc5-26da-4080-ba6b-048f80f7cec9   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda1: Location of files loaded by Grub: ===================


 441.3GB: boot/grub/core.img

============================= sdc1/grub/grub.cfg: =============================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 94e510c4-b762-460f-9a65-27e68887966d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c3111ca5-13cc-4042-bcc4-9a31aef7622c
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c3111ca5-13cc-4042-bcc4-9a31aef7622c
	linux	/vmlinuz-2.6.35-22-generic root=UUID=94e510c4-b762-460f-9a65-27e68887966d ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c3111ca5-13cc-4042-bcc4-9a31aef7622c
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=94e510c4-b762-460f-9a65-27e68887966d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c3111ca5-13cc-4042-bcc4-9a31aef7622c
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c3111ca5-13cc-4042-bcc4-9a31aef7622c
	linux16	/memtest86+.bin console=ttyS0,115200n8
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

=================== sdc1: Location of files loaded by Grub: ===================


    .1GB: grub/core.img
    .2GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic
    .1GB: vmlinuz-2.6.35-22-generic

=============================== sdc3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc3 during installation
/dev/sdc3 /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sdc1 during installation
/dev/sdc1 /boot           ext3    defaults        0       2
# /home was on /dev/sdc4 during installation
/dev/sdc4 /home           ext3    defaults        0       2
# /media/backup was on /dev/sdb2 during installation
/dev/sdb2 /media/backup   vfat    utf8,umask=007,gid=46 0       1
# /media/bigbastard was on /dev/sda1 during installation
/dev/sda1 /media/bigbastard ext3    defaults        0       2
# /media/supersize was on /dev/sdb1 during installation
/dev/sdb1/media/supersize ext3    defaults        0       2
# swap was on /dev/sdc5 during installation
UUID=fad2fdc5-26da-4080-ba6b-048f80f7cec9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


```

So I need to get grub out of the 500gb drive and onto the 200gb drive where / and /home are

---

### Post by Rubi1200 on 2010-12-11
I don't understand why you are complicating matters for yourself by using a /boot partition or why you have 3 different bootloaders; GRUB2, GRUB-legacy, and lilo.

Wouldn't it be easier to pick one and use that for all drives?

In any event, to answer the question I would say you need to reinstall the bootloader to the boot partition of the 200GB drive (it is currently installed on sda).

This is just my take on the situation and you should probably wait to see what others have to say.

---

### Post by pickarooney on 2010-12-11
I've always had a /boot partition and it has never been a problem.
I zould gladly get rid of the old GRUB1 and LILO if I knew how - ubuntu's installer created the mess by swapping all my drive letters around

hoz do I reinstall the bootloader to the /boot partition of sda?

---

### Post by pickarooney on 2010-12-11
I tried to purge the grubs but somehow ended up with 2 GRUB2s and a LILO. I'm totally lost now

When I booted up I no longer had an error 15 but the grub> prompt

---

### Post by Rubi1200 on 2010-12-11
For those concerned:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Lilo is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 377063 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sdc4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   204,796,619   204,796,557  83 Linux
/dev/sdb2         204,796,620   398,283,479   193,486,860   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     2,040,254     2,040,192  83 Linux
/dev/sdc2         384,708,616   390,716,864     6,008,249   5 Extended
/dev/sdc5         384,708,618   390,716,864     6,008,247  82 Linux swap / Solaris
/dev/sdc3           2,040,255    83,955,689    81,915,435  83 Linux
/dev/sdc4          83,955,690   384,708,554   300,752,865  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        403e1522-05cc-4cd7-9d16-0a00e8b2409b   ext3       magnum                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        a138972b-a839-4285-b048-77660796538f   ext3       supersize                     
/dev/sdb2        D6F8-0339                              vfat                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        c3111ca5-13cc-4042-bcc4-9a31aef7622c   ext3                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc3        94e510c4-b762-460f-9a65-27e68887966d   ext3                                     
/dev/sdc4        6aca9cac-5354-4183-bf88-68e9e62bed9a   ext3                                     
/dev/sdc5        fad2fdc5-26da-4080-ba6b-048f80f7cec9   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda1: Location of files loaded by Grub: ===================


 441.3GB: boot/grub/core.img

============================= sdc1/grub/grub.cfg: =============================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 94e510c4-b762-460f-9a65-27e68887966d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c3111ca5-13cc-4042-bcc4-9a31aef7622c
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c3111ca5-13cc-4042-bcc4-9a31aef7622c
    linux    /vmlinuz-2.6.35-22-generic root=UUID=94e510c4-b762-460f-9a65-27e68887966d ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c3111ca5-13cc-4042-bcc4-9a31aef7622c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=94e510c4-b762-460f-9a65-27e68887966d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c3111ca5-13cc-4042-bcc4-9a31aef7622c
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c3111ca5-13cc-4042-bcc4-9a31aef7622c
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=================== sdc1: Location of files loaded by Grub: ===================


    .1GB: grub/core.img
    .2GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic
    .1GB: vmlinuz-2.6.35-22-generic

=============================== sdc3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc3 during installation
/dev/sdc3 /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sdc1 during installation
/dev/sdc1 /boot           ext3    defaults        0       2
# /home was on /dev/sdc4 during installation
/dev/sdc4 /home           ext3    defaults        0       2
# /media/backup was on /dev/sdb2 during installation
/dev/sdb2 /media/backup   vfat    utf8,umask=007,gid=46 0       1
# /media/bigbastard was on /dev/sda1 during installation
/dev/sda1 /media/bigbastard ext3    defaults        0       2
# /media/supersize was on /dev/sdb1 during installation
/dev/sdb1/media/supersize ext3    defaults        0       2
# swap was on /dev/sdc5 during installation
UUID=fad2fdc5-26da-4080-ba6b-048f80f7cec9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc3: Location of files loaded by Grub: ===================


  10.9GB: boot/grub/core.img
```

---

### Post by pickarooney on 2010-12-11
I could format and reinstall but I might still end up with the unwanted GRUB in the 500GB drive and I still won't know where to set the new boot area to.

At this stage I don't care if there's a /boot or not, I just want to get the system to boot properly however that is.

I tried two more things but they made no difference:
1. copied the files from **/boot/**grub to **/**boot/grub (i.e. from the 1GB partition to the 48GB partition on the 200GB drive

2. I ran grub-install and moved it to the /boot partition 

```

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Lilo is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

```

---

### Post by drs305 on 2010-12-11
Ok.... here we go. I will assume sdc1 is /boot, sdc3 is /  are what you want to restore, and that sdc is always connected when you boot. If either of these assumptions is incorrect let us know before running any of the following commands. We are going to remove all Grub files and replace with Grub 2.

Boot the LiveCD and run the following commands (# after the command explains what it does). We are following the chroot section of this guide. Especially when purging and installing grub, you may wish to refer to the guide for explanations of the options you will be shown:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")


Mount the sdc partitions:
```
sudo mount /dev/sdc3 /mnt/temp
sudo mount /dev/sdc1 /mnt/temp/boot
sudo mount /dev/sdc4 /mnt/temp/home
```

If you get an error about a mountpoint not existing, make it (sudo mkdir /mnt/temp/xxxx.

Mount special folders to prepare to chroot. The first command mounts /dev, /dev/pts, /proc and /sys to /mnt/temp/*. The second may help connect to the Internet, the third chroots into your sdc installation. ENTER after each command.
```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  # May be required to connect to the Internet.
sudo chroot /mnt/temp
```

You should now be at a root prompt.
```
apt-get update  # Checks Internet connection. If no Internet connection, do not proceed!
apt-get purge grub grub-pc grub-common  # Remove all Grub files, OK to remove bootloader.
apt-get install grub-common grub-pc  # Restore all grub files
update-grub 

```

I think your fstab is correct, but if you want to review it now would be the time (it should be in the *etc* folder.

```
exit  # Leave chroot
```

Unmount:
```
for i in /dev/pts /dev /proc /sys /boot /home / ; do sudo umount /mnt/temp$i ; done
```

Reboot. Make sure the BIOS points to sdc as the first drive.

---

### Post by pickarooney on 2010-12-11
Going good as far as here:
**apt-get install grub-common grub-pc**
the blue screen in the terminal says 

'The following linux command was extracted from /etc/default/grub or the 'kopt' parameter in GRUB's legacy menu.lst. Please verify that it is correct and modify it if ncecessary.

Linux command line
[                                                 ]
OK'

The command line is completely blank.

If I continue without typing anything I get to the following after a couple of steps:
**GRUB install devices**
I have five choices - sda, sdb, sdc, sdc1 and sdc3

Should I choose sdc or sdc3?

---

### Post by drs305 on 2010-12-11
> **pickarooney said:**
> Going good as far as here:
**apt-get install grub-common grub-pc**
the blue screen in the terminal says 

'The following linux command was extracted from /etc/default/grub or the 'kopt' parameter in GRUB's legacy menu.lst. Please verify that it is correct and modify it if ncecessary.

Linux command line
[                                                 ]
OK'

The command line is completely blank.

If I continue without typing anything I get to the following after a couple of steps:
**GRUB install devices**
I have five choices - sda, sdb, sdc, sdc1 and sdc3

Should I choose sdc or sdc3?

You are probably past that point, but for the blank line just tab to OK.

For the device, choose sdc. You choose sdc because you want it in the MBR and not installed to a paritition.

It's explained in more detail in the link I provided.

---

### Post by pickarooney on 2010-12-11
Thanks. I'd read the linked page about 4 times but I just kept getting more and more confused. I think I have everything now so I'll reboot and see you in 5...

---

### Post by pickarooney on 2010-12-11
This time I rebooted, got a GRUB menu and when I selected the first entry the screen went blank except for a flashing underscore After about 3 minutes my monitor switched itself off with a 'no signal' message. I tried a couple of times but always with the same result.

The BIOS is set to boot from the 200GB HD where / and /boot are located

---

### Post by drs305 on 2010-12-11
> **pickarooney said:**
> This time I rebooted, got a GRUB menu and when I selected the first entry the screen went blank except for a flashing underscore After about 3 minutes my monitor switched itself off with a 'no signal' message. I tried a couple of times but always with the same result.

The BIOS is set to boot from the 200GB HD where / and /boot are located

The flashing underscore is actually not bad news. Let me explain.

The blinking cursor after the Grub menu means that the MBR properly transferred control to Grub, which presented the menu. The blinking cursor also means that Grub2 successfully passed control over to the kernel.

What you have now is most likely a video driver problem (often nvidia). To remedy this situation, reboot to the Grub2 menu. Highlight the first entry and then press "e".

You will now be able to edit the entry. Use the cursor keys to move to the end of the "linux" line. You will probably see "quiet splash"

Add **nomodeset** to the end of the line, then press CTRL-x to boot.

Hopefully this will get you to the Desktop. From there, select System, Administration, Additional Drivers. If you will see a video driver for your card install it and you should be set.

If you don't find the driver and have to reboot, you will need to repeat the procedure since it isn't stored. You can leave the nomodeset option permanent by editing /etc/default/grub and adding it to the same entry with "quiet splash". Run "sudo update-grub" after making the change.

---

### Post by pickarooney on 2010-12-11
OK, here goes again!

---

### Post by pickarooney on 2010-12-11
That did the trick! Huge thanks for the help :)

---

### Post by drs305 on 2010-12-11
> **pickarooney said:**
> That did the trick! Huge thanks for the help :)

Excellent!

Edit Too Late>

If you have no other issues regarding this thread, would you please mark it SOLVED via the 'Thread Tools' link at the top right of the first post.

Happy (X)Ubuntu-ing.

---

