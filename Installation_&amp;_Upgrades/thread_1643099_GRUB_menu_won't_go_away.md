---
title: "GRUB menu won't go away"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by djaun on 2010-12-11
Once upon a time I had Maverick Meerkat installed on two drives. Now I've used Disk Utility's "Format Drive" to erase it and remove the Master Boot Record partitioning on one of them.

Yet I still have to go through the GRUB menu each time I start up my computer, as if there are multiple bootable drives.

I've read that 'sudo grub-install /dev/sdb' might work, but that only seems to reset the bootloader, not remove it.

Any questions/suggestions are welcome.

---

### Post by sikander3786 on 2010-12-11
Do you mean you don't want to see the Grub menu by default?

If yes, please post the output of this command.

```
cat /etc/default/grub
```

While posting, click # icon in post menu and paste your text in between the generated code tags.

---

### Post by coffeecat on 2010-12-11
You still need the grub bootloader even if you only have one instance of Ubuntu on the machine. It is sensible to display the grub menu, so that you can select recovery mode if need be, but the grub menu can be hidden if you prefer. Have a look here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Boot into Ubuntu, download and run the script and post the RESULTS.txt file here, making sure to enclose them in code tags to make them readable. Press the # icon in the message toolbar for this. This will give us information about your setup, so that we can see what needs to be done.

---

### Post by djaun on 2010-12-12
It's true. I don't want to see the GRUB menu unless I take action on startup, like holding down the shift key. Here are the contents of /etc/default/grub:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

And here is the output from the boot info script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   112,351,231   112,349,184  83 Linux
/dev/sda2         112,353,278   117,229,567     4,876,290   5 Extended
/dev/sda5         112,353,280   117,229,567     4,876,288  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        16ec5d04-dcc7-4a9e-a286-ecc9b844801a   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f61a1461-68e5-41d7-bd6d-58404ad5bd10   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb         721ba8a9-d6c6-4810-9e7a-524d27425443   ext4       UserFiles                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 16ec5d04-dcc7-4a9e-a286-ecc9b844801a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 16ec5d04-dcc7-4a9e-a286-ecc9b844801a
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 16ec5d04-dcc7-4a9e-a286-ecc9b844801a
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=16ec5d04-dcc7-4a9e-a286-ecc9b844801a ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 16ec5d04-dcc7-4a9e-a286-ecc9b844801a
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=16ec5d04-dcc7-4a9e-a286-ecc9b844801a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 16ec5d04-dcc7-4a9e-a286-ecc9b844801a
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=16ec5d04-dcc7-4a9e-a286-ecc9b844801a ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 16ec5d04-dcc7-4a9e-a286-ecc9b844801a
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=16ec5d04-dcc7-4a9e-a286-ecc9b844801a ro single 
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 16ec5d04-dcc7-4a9e-a286-ecc9b844801a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 16ec5d04-dcc7-4a9e-a286-ecc9b844801a
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=16ec5d04-dcc7-4a9e-a286-ecc9b844801a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f61a1461-68e5-41d7-bd6d-58404ad5bd10 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  43.0GB: boot/grub/core.img
   6.7GB: boot/grub/grub.cfg
   7.3GB: boot/initrd.img-2.6.35-22-generic
   7.4GB: boot/initrd.img-2.6.35-23-generic
  43.2GB: boot/vmlinuz-2.6.35-22-generic
  43.2GB: boot/vmlinuz-2.6.35-23-generic
   7.4GB: initrd.img
   7.3GB: initrd.img.old
  43.2GB: vmlinuz
  43.2GB: vmlinuz.old
```

---

### Post by sikander3786 on 2010-12-12
Edit your /etc/default/grub by,

```
gksudo gedit /etc/default/grub
```

And uncomment this line,

```
#GRUB_HIDDEN_TIMEOUT=0
```

So that it looks like,

```
GRUB_HIDDEN_TIMEOUT=0
```

Save and close. Update Grub by,

```
sudo update-grub
```

Reboot!

---

### Post by djaun on 2010-12-12
Yep that did the trick. Thanks!

---

