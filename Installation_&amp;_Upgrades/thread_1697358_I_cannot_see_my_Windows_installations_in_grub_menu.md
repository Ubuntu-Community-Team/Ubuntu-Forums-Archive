---
title: "I cannot see my Windows installations in grub menu"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by cubabit on 2011-02-28
I upgraded Ununtu from 10.04 to 10.10 Maverick and the Windows 7 partition disappeared from my grub menu. It used to work OK in Lucid.

I have tried **update-grub** but it does not find the Windows install.

```

pete@pete-vaio:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-25-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

Here is my output from boot info script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

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

/dev/sda1               2,048    22,245,375    22,243,328  27 Hidden HPFS/NTFS
/dev/sda2    *     22,245,376    22,450,175       204,800   7 HPFS/NTFS
/dev/sda3          22,450,176   586,145,488   563,695,313   7 HPFS/NTFS
/dev/sda4         586,145,790   976,773,119   390,627,330   5 Extended
/dev/sda5         965,054,464   976,773,119    11,718,656  82 Linux swap / Solaris
/dev/sda6         906,461,184   965,054,463    58,593,280  83 Linux
/dev/sda7         586,145,792   906,459,135   320,313,344  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B03442BF34428874                       ntfs       Recovery                      
/dev/sda2        16B44083B4406779                       ntfs       System Reserved               
/dev/sda3        4E3E42333E4213FD                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        aadc116c-2fa6-4851-b99e-dcbd5f98daa3   swap                                     
/dev/sda6        a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3   ext3                                     
/dev/sda7        6f4fb68e-1304-4b95-b602-945b74c69d1c   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext3       (rw,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1600x900
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=keep
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3 ro acpi_backlight=vendor acpi_sleep=nonvs  quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=keep
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3
	echo	'Loading Linux 2.6.35-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3 ro single acpi_backlight=vendor acpi_sleep=nonvs
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=keep
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3 ro acpi_backlight=vendor acpi_sleep=nonvs  quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=keep
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3 ro single acpi_backlight=vendor acpi_sleep=nonvs
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=keep
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3 ro acpi_backlight=vendor acpi_sleep=nonvs  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=keep
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3 ro single acpi_backlight=vendor acpi_sleep=nonvs
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=keep
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3 ro acpi_backlight=vendor acpi_sleep=nonvs  quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=keep
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3 ro single acpi_backlight=vendor acpi_sleep=nonvs
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=keep
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3 ro acpi_backlight=vendor acpi_sleep=nonvs  quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=keep
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3 ro single acpi_backlight=vendor acpi_sleep=nonvs
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=a9a87fbd-6352-4b79-a6a3-b08e7f1cc9f3 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=6f4fb68e-1304-4b95-b602-945b74c69d1c /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=aadc116c-2fa6-4851-b99e-dcbd5f98daa3 none            swap    sw              0       0

sshfs#peter@192.168.1.64:/shares/internal/PUBLIC    /mnt/mybook    fuse    comment=sshfs,noauto,users,exec,uid=1000,gid=1000,allow_other,reconnect,transform_symlinks,BatchMode=yes 0 0

=================== sda6: Location of files loaded by Grub: ===================


 485.7GB: boot/grub/core.img
 485.7GB: boot/grub/grub.cfg
 485.8GB: boot/initrd.img-2.6.32-23-generic
 485.8GB: boot/initrd.img-2.6.32-27-generic
 485.8GB: boot/initrd.img-2.6.35-24-generic
 485.7GB: boot/initrd.img-2.6.35-25-generic
 485.8GB: boot/initrd.img-2.6.35-25-generic-pae
 485.7GB: boot/vmlinuz-2.6.32-23-generic
 485.8GB: boot/vmlinuz-2.6.32-27-generic
 485.8GB: boot/vmlinuz-2.6.35-24-generic
 485.7GB: boot/vmlinuz-2.6.35-25-generic
 485.8GB: boot/vmlinuz-2.6.35-25-generic-pae
 485.8GB: initrd.img
 485.7GB: initrd.img.old
 485.8GB: vmlinuz
 485.7GB: vmlinuz.old
```

---

### Post by Quackers on 2011-02-28
Can you go into synaptic and check something please?
In the search box enter os-prober and when it comes up in the main window does it have a green box next to it? If not please install it and run sudo update-grub again.

---

### Post by cubabit on 2011-03-01
Ah yes, I knew I forgot something. Yes - os-prober is installed. here's the output:

```
pete@pete-vaio:~$ sudo os-prober 
/dev/sda1:Windows Vista (loader):Windows:chain
/dev/sda2:Windows 7 (loader):Windows1:chain
```

It was installed when I run **update-grub** before, but just to confirm, I ran it again and it does not pick up the Windows installation.

---

### Post by cubabit on 2011-03-01
Just in case you ask here is my /etc/default/grub:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=2
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_FORCE_HIDDEN_MENU=true
export GRUB_FORCE_HIDDEN_MENU
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor acpi_sleep=nonvs"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1600x900
GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

