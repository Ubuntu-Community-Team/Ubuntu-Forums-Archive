---
title: "Grub 2"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by Zhivargo on 2011-02-06
Hey sorry cant find a solution to this: 

following instructions to add Win 7 in Grub, i managed to add an entry but then system hangs...

# 
#! /bin/sh -e
echo "Adding Windows" >&2
cat << EOF
menuentry "Windows 7" {
set root=(hd0,3)
chainloader +1
}
EOF
#


fdisk -l 


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      194560   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              25      128410  1031248897    5  Extended
**/dev/sda3          128410      192151   512000000    7  HPFS/NTFS**
Partition 3 does not end on cylinder boundary.
/dev/sda5              25        6104    48827392   83  Linux
/dev/sda6            6104      127680   976561152   83  Linux
/dev/sda7          127680      128410     5858304   82  Linux swap / Solaris

so correct me if im wrong but the root should point to (hd0,3) in Grub2?? 
its giving me headaches!

---

### Post by dino99 on 2011-02-06
your problem:  Partition 3 does not end on cylinder boundary

so first fix it: chkdsk on winblow or fsck on linux, if you cant, then use a formatting tool

---

### Post by oldfred on 2011-02-06
With LBA cylinders have not been used for 10+ years. The new partitioning with win or gparted use different rounding that is more compatible with SSDs & new 4k drives. It may leave small amounts of space on a drive. Older partitions also had some space left but it was less than 1K so you did not see it due to rounding, now it is slightly over 1K so you may see it.

Post this:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by kansasnoob on 2011-02-06
> Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

@ oldfred, I like that explanation. I've been trying to find the right words to describe how to do that. It makes all the difference in the world to those of us who read these things. As an example, just a snippet of fdisk -lu without and then with:

>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    84646484    42323211   83  Linux


```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    84646484    42323211   83  Linux

```

I'm old, and I'm lazy, make it easy for me to read :D

---

### Post by oldfred on 2011-02-06
kansas,

I keep changing my explanation to try to make it more clear to new users. They just do not seem to understand highlighting & the # in the edit panel. Maybe they do not understand what edit panel is or that they just paste anyway. I only get half to do it correctly even with my expanded explanation.:icon_frown:

I too need it easy to read.

---

### Post by presence1960 on 2011-02-06
> **kansasnoob said:**
> @ oldfred, I like that explanation. I've been trying to find the right words to describe how to do that. It makes all the difference in the world to those of us who read these things. As an example, just a snippet of fdisk -lu without and then with:



```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    84646484    42323211   83  Linux

```

I'm old, and I'm lazy, make it easy for me to read :D

:lolflag:

---

### Post by Zhivargo on 2011-02-07
thanks for your help guys! 
@oldfred: 

```
your script is awesome!
```

---

### Post by Zhivargo on 2011-02-07
i made a new partition and mapped it to the cylinder block, but i still get the same message with fdisk. ??? !!! are you sure this is essential to boot ntfs drives? 

do i do this? 

```

sudo ntfs-3g /dev/$part /mnt/$mountpoint -o force

```

---

### Post by Zhivargo on 2011-02-07
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 46082 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       391,167       389,120  83 Linux
/dev/sda2             393,214 2,062,891,007 2,062,497,794   5 Extended
/dev/sda5             393,216    98,047,999    97,654,784  83 Linux
/dev/sda6          98,050,048 2,051,172,351 1,953,122,304  83 Linux
/dev/sda7       2,051,174,400 2,062,891,007    11,716,608  82 Linux swap / Solaris
/dev/sda3       2,062,891,008 3,086,891,007 1,024,000,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        18a21fa6-9604-45e0-b163-2fbd236cfbca   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        39CA80726F3EFF7F                       ntfs                                     
/dev/sda5        09237179-aed5-4889-9ce2-bdb39f2ca6b3   ext4                                     
/dev/sda6        f2e4d2a1-4eae-48c6-a329-9422ea25367d   ext4                                     
/dev/sda7        96f160d0-8664-457b-8f26-9a3a239ec7f4   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /boot                    ext3       (rw,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)


============================= sda1/grub/grub.cfg: =============================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 09237179-aed5-4889-9ce2-bdb39f2ca6b3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 18a21fa6-9604-45e0-b163-2fbd236cfbca
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 18a21fa6-9604-45e0-b163-2fbd236cfbca
	linux	/vmlinuz-2.6.35-25-generic root=UUID=09237179-aed5-4889-9ce2-bdb39f2ca6b3 ro   quiet splash
	initrd	/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 18a21fa6-9604-45e0-b163-2fbd236cfbca
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/vmlinuz-2.6.35-25-generic root=UUID=09237179-aed5-4889-9ce2-bdb39f2ca6b3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 18a21fa6-9604-45e0-b163-2fbd236cfbca
	linux	/vmlinuz-2.6.35-22-generic root=UUID=09237179-aed5-4889-9ce2-bdb39f2ca6b3 ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 18a21fa6-9604-45e0-b163-2fbd236cfbca
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=09237179-aed5-4889-9ce2-bdb39f2ca6b3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows 7" {
set root=(hd0,3)
chainloader (hd0,3)+1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 18a21fa6-9604-45e0-b163-2fbd236cfbca
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 18a21fa6-9604-45e0-b163-2fbd236cfbca
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 39ca80726f3eff7f
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

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: initrd.img-2.6.35-25-generic
    .0GB: vmlinuz-2.6.35-22-generic
    .0GB: vmlinuz-2.6.35-25-generic

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=09237179-aed5-4889-9ce2-bdb39f2ca6b3 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=18a21fa6-9604-45e0-b163-2fbd236cfbca /boot           ext3    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=f2e4d2a1-4eae-48c6-a329-9422ea25367d /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=96f160d0-8664-457b-8f26-9a3a239ec7f4 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


    .2GB: initrd.img
    .2GB: initrd.img.old
    .2GB: vmlinuz
    .2GB: vmlinuz.old

```

---

### Post by oldfred on 2011-02-07
I do not see anything in boot script that looks like it would prevent you from booting windows.

Grub does not use boot flag, but windows does. If you revert to a windows boot loader or want to do repairs on windows you will need to move the boot flag to sda3.

set boot flag on for sda3 (off on others)
sudo sfdisk -A3 /dev/sda

You also have a copy of grub2 in the partition boot sector of sda1, but the boot sector is not normally used by grub2. (Boot sector is used by windows.)

Grub2's osprober has added its standard boot stanza, does that work?

---

