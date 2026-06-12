---
title: "ubuntu &amp; andrioid grub problems."
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by rhcm123 on 2010-10-29
Hey all,

i just felt like trying out an install of android on my netbook to see how its going. i resized my ext4 partition and created a new one for android then installed it, done. however, i wasn't able to setup grub (lives in the ubuntu partition) to see the android partion. Im very bad with grub2 so i need some help.

These are the lines android supplies for grub:
```

default=0
timeout=6
root (hd0,2)
splashimage=/grub/android-x86.xpm.gz

title Android-x86 1.6-r2
      kernel /android-1.6-r2/kernel quiet root=/dev/ram0 androidboot_hardware=eeepc acpi_sleep=s3_bios,s3_mode SRC=/android-1.6-r2
      initrd /android-1.6-r2/initrd.img

title Android-x86 1.6-r2 (Debug mode)
      kernel /android-1.6-r2/kernel quiet root=/dev/ram0 androidboot_hardware=eeepc acpi_sleep=s3_bios,s3_mode DEBUG=1 SRC=/android-1.6-r2
      initrd /android-1.6-r2/initrd.img

```

i put these lines in /etc/grub.d/40_custom:
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Android-X86" {
	set root (hd0,2)
	splashimage=/grub/android-x86.xpm.gz
	kernel /android-1.6-r2/kernel quiet root=/dev/ram0 androidboot_hardware=eeepc acpi_sleep=s3_bios,s3_mode SRC=/android-1.6-r2
	initrd /android-1.6-r2/initrd.img
}
menuentry "Android-X86 DEBUG" {
        set root (hd0,2)
        splashimage=/grub/android-x86.xpm.gz
	kernel /android-1.6-r2/kernel root=/dev/ram0 androidboot_hardware=eeepc acpi_sleep=s3_bios,s3_mode DEBUG=1 SRC=/android-1.6-r2
	initrd /android-1.6-r2/initrd.img
}
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Android-X86" {
	set root (hd0,2)
	splashimage=/grub/android-x86.xpm.gz
	kernel /android-1.6-r2/kernel quiet root=/dev/ram0 androidboot_hardware=eeepc acpi_sleep=s3_bios,s3_mode SRC=/android-1.6-r2
	initrd /android-1.6-r2/initrd.img
}
menuentry "Android-X86 DEBUG" {
        set root (hd0,2)
        splashimage=/grub/android-x86.xpm.gz
	kernel /android-1.6-r2/kernel root=/dev/ram0 androidboot_hardware=eeepc acpi_sleep=s3_bios,s3_mode DEBUG=1 SRC=/android-1.6-r2
	initrd /android-1.6-r2/initrd.img
}

```

then i ran update-grub, but the new options didn't show up

where did i go wrong

---

### Post by rhcm123 on 2010-11-01
Bump

---

### Post by oldfred on 2010-11-02
Old grub counts partitions from 0, where grub2 counts starting at 1. 
root (hd0,2)
becomes
set root = (hd0,3)

Grub2 also seems to use linux in place of kernel.

Do not know about splash image - Is that still a valid keyword?

To see entire system:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by rhcm123 on 2010-11-09
sorry i was busy, i just got to this, and wasnt really thinking about my linux projects...
heres my result file:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   241,183,844   241,183,782  83 Linux
/dev/sda2         311,596,740   312,576,704       979,965   5 Extended
/dev/sda5         311,596,803   312,576,704       979,902  82 Linux swap / Solaris
/dev/sda3         241,183,845   311,596,739    70,412,895   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2e0177fc-6aa6-4ebd-889d-bdcfd908da46   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        34df9c9a-4dff-434d-aa12-7ff8a74851e4   ext2       Android-x86                   
/dev/sda5        7db34329-f084-441b-a0a4-b318fb61268c   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /media/DROID             ext2       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 2e0177fc-6aa6-4ebd-889d-bdcfd908da46
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 2e0177fc-6aa6-4ebd-889d-bdcfd908da46
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2e0177fc-6aa6-4ebd-889d-bdcfd908da46
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=2e0177fc-6aa6-4ebd-889d-bdcfd908da46 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2e0177fc-6aa6-4ebd-889d-bdcfd908da46
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=2e0177fc-6aa6-4ebd-889d-bdcfd908da46 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2e0177fc-6aa6-4ebd-889d-bdcfd908da46
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=2e0177fc-6aa6-4ebd-889d-bdcfd908da46 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2e0177fc-6aa6-4ebd-889d-bdcfd908da46
	echo	'Loading Linux 2.6.31-22-generic ...'
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=2e0177fc-6aa6-4ebd-889d-bdcfd908da46 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2e0177fc-6aa6-4ebd-889d-bdcfd908da46
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2e0177fc-6aa6-4ebd-889d-bdcfd908da46
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

### BEGIN /etc/grub.d/40_custom.bak ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom.bak ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2e0177fc-6aa6-4ebd-889d-bdcfd908da46 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7db34329-f084-441b-a0a4-b318fb61268c none            swap    sw              0       0
//192.168.1.193/share /media/share smbfs credentials=/home/ussr/.smb,user,auto 0	0
/dev/sda3	/media/DROID	ext2	defaults	0	0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   7.0GB: boot/grub/grub.cfg
   1.1GB: boot/initrd.img-2.6.31-22-generic
  11.0GB: boot/initrd.img-2.6.32-25-generic
   1.0GB: boot/vmlinuz-2.6.31-22-generic
    .9GB: boot/vmlinuz-2.6.32-25-generic
  11.0GB: initrd.img
   1.1GB: initrd.img.old
    .9GB: vmlinuz
   1.0GB: vmlinuz.old

============================= sda3/grub/menu.lst: =============================

default=0
timeout=6
root (hd0,2)
splashimage=/grub/android-x86.xpm.gz

title Android-x86 1.6-r2
	kernel /android-1.6-r2/kernel quiet root=/dev/ram0 androidboot_hardware=eeepc acpi_sleep=s3_bios,s3_mode SRC=/android-1.6-r2
	initrd /android-1.6-r2/initrd.img

title Android-x86 1.6-r2 (Debug mode)
	kernel /android-1.6-r2/kernel root=/dev/ram0 androidboot_hardware=eeepc acpi_sleep=s3_bios,s3_mode DEBUG=1 SRC=/android-1.6-r2
	initrd /android-1.6-r2/initrd.img


=================== sda3: Location of files loaded by Grub: ===================


 123.7GB: grub/menu.lst
 123.8GB: grub/stage2

```

---

### Post by rhcm123 on 2010-11-14
bump

---

### Post by oldfred on 2010-11-15
Besides converting the old grub menu to a grub2 40_custom entry, you can install old grub to the Android partition and chainboot it. You have to have grub in the partition for chainboot to work.

Did you try changing the set root = (hd0,3)? I do not see it in your boot script? The script also does not show the kernel & initrd, but may not. Confirm that they are really there.

menuentry "Chainload Other Systems Grub Menu on sda3" {
set root=(hd0,3)
chainloader +1
}

---

### Post by geazzy on 2011-04-25
i try and solved with [this ]("http://www.franklinstrube.com/blog/dual-booting-ubuntu-netbook-remix-and-android-x86-on-an-asus-eee-pc/"):D

---

