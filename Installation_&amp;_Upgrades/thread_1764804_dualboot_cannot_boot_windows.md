---
title: "dualboot: cannot boot windows"
date: 2011-05-22
forum: Installation &amp; Upgrades
---

### Post by cremersstijn on 2011-05-22
Hello!

I have a dualboot with windows 7 and ubuntu 11.4 (actually i have a triple boot with windows 7 and ubuntu 11.4 32 bit and 64 bit).

But i cannot boot windows 7 anymore...

What can i do to make this work again...?

---

### Post by cayphed on 2011-05-22
Get startup manager from the software centre, it'll let you see what distro's you have installed and let you chose which one is to be delfault ect...

---

### Post by cremersstijn on 2011-05-22
I can see it in the boot menu...
When i click on it...it just returns to the same boot menu...

---

### Post by sikander3786 on 2011-05-22
We need some more information on that.

We need you to boot Ubuntu and then download and run bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Once run, it would generate a Results.txt file on your desktop. Please copy/paste all data from that file in your post here.

While posting, click the # icon in post menu and paste your text in between the generated [code] tags for readability purposes.

---

### Post by cremersstijn on 2011-05-22
here it is...

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 374437352 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos7)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   348,988,079   348,781,232   7 NTFS / exFAT / HPFS
/dev/sda3         348,989,438   625,141,759   276,152,322   5 Extended
/dev/sda5         481,781,760   619,208,703   137,426,944  83 Linux
/dev/sda6         619,210,752   625,141,759     5,931,008  82 Linux swap / Solaris
/dev/sda7         348,989,440   481,781,759   132,792,320  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3AEC4511EC44C8B9                       ntfs       System Reserved
/dev/sda2        9830468B30467074                       ntfs       
/dev/sda5        34b3c16e-91b0-4f31-90a8-113ef80c6f39   ext4       
/dev/sda6        21709a68-3359-437e-b12f-52860a076fd7   swap       
/dev/sda7        5c97f9e2-98eb-4f09-ac4a-f7ece017730d   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="11"
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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=34b3c16e-91b0-4f31-90a8-113ef80c6f39 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=34b3c16e-91b0-4f31-90a8-113ef80c6f39 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=34b3c16e-91b0-4f31-90a8-113ef80c6f39 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=34b3c16e-91b0-4f31-90a8-113ef80c6f39 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=34b3c16e-91b0-4f31-90a8-113ef80c6f39 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=34b3c16e-91b0-4f31-90a8-113ef80c6f39 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=34b3c16e-91b0-4f31-90a8-113ef80c6f39 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
	echo	'Loading Linux 2.6.32-31-generic ...'
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=34b3c16e-91b0-4f31-90a8-113ef80c6f39 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-31-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 3AEC4511EC44C8B9
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=5c97f9e2-98eb-4f09-ac4a-f7ece017730d ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=5c97f9e2-98eb-4f09-ac4a-f7ece017730d ro single
	initrd /boot/initrd.img-2.6.38-8-generic
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=34b3c16e-91b0-4f31-90a8-113ef80c6f39 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sdb6 during installation
UUID=21709a68-3359-437e-b12f-52860a076fd7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 243.862667084 = 261.845544960  boot/grub/core.img                             1
 268.090713501 = 287.860211712  boot/grub/grub.cfg                             1
 263.442382812 = 282.869104640  boot/initrd.img-2.6.32-31-generic              2
 270.242630005 = 290.170814464  boot/initrd.img-2.6.35-28-generic              2
 270.262695312 = 290.192359424  boot/initrd.img-2.6.38-8-generic               2
 269.129974365 = 288.976109568  boot/initrd.img-2.6.38-8-generic-pae           2
 244.324985504 = 262.341955584  boot/vmlinuz-2.6.32-31-generic                 1
 244.559337616 = 262.593589248  boot/vmlinuz-2.6.35-28-generic                 1
 264.462219238 = 283.964145664  boot/vmlinuz-2.6.38-8-generic                  1
 264.540466309 = 284.048162816  boot/vmlinuz-2.6.38-8-generic-pae              1
 269.129974365 = 288.976109568  initrd.img                                     2
 270.262695312 = 290.192359424  initrd.img.old                                 2
 264.540466309 = 284.048162816  vmlinuz                                        1
 264.462219238 = 283.964145664  vmlinuz.old                                    1

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
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
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
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=5c97f9e2-98eb-4f09-ac4a-f7ece017730d ro  splash vga=788  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=5c97f9e2-98eb-4f09-ac4a-f7ece017730d ro single  splash vga=788
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
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 3AEC4511EC44C8B9
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
	linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=34b3c16e-91b0-4f31-90a8-113ef80c6f39 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
	linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=34b3c16e-91b0-4f31-90a8-113ef80c6f39 ro single
	initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=34b3c16e-91b0-4f31-90a8-113ef80c6f39 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=34b3c16e-91b0-4f31-90a8-113ef80c6f39 ro single
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=34b3c16e-91b0-4f31-90a8-113ef80c6f39 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=34b3c16e-91b0-4f31-90a8-113ef80c6f39 ro single
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-31-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
	linux /boot/vmlinuz-2.6.32-31-generic root=UUID=34b3c16e-91b0-4f31-90a8-113ef80c6f39 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.32-31-generic
}
menuentry "Ubuntu, with Linux 2.6.32-31-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 34b3c16e-91b0-4f31-90a8-113ef80c6f39
	linux /boot/vmlinuz-2.6.32-31-generic root=UUID=34b3c16e-91b0-4f31-90a8-113ef80c6f39 ro single
	initrd /boot/initrd.img-2.6.32-31-generic
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=5c97f9e2-98eb-4f09-ac4a-f7ece017730d /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda6 during installation
UUID=21709a68-3359-437e-b12f-52860a076fd7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 178.545669556 = 191.711952896  boot/grub/core.img                             1
 171.515041351 = 184.162873344  boot/grub/grub.cfg                             1
 169.192382812 = 181.668937728  boot/initrd.img-2.6.38-8-generic               2
 178.543949127 = 191.710105600  boot/vmlinuz-2.6.38-8-generic                  1
 169.192382812 = 181.668937728  initrd.img                                     2
 178.543949127 = 191.710105600  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  56 38 7b 6c 8e 4b cd bf  c3 36 01 70 43 8d a5 ff  |V8{l.K...6.pC...|
00000010  fb d0 44 09 00 06 05 68  d3 7d 69 80 08 b5 ed 1a  |..D....h.}i.....|
00000020  7d ad 30 01 1b ed 97 b7  b9 97 ff c3 37 b2 77 77  |}.0.........7.ww|
00000030  30 ff f9 1c dc b6 51 c9  0c 0e ba ec c5 1d fb d0  |0.....Q.........|
00000040  cd 97 bc 7c 5a 2b 0f 47  a7 e0 68 b3 71 d8 ac c9  |...|Z+.G..h.q...|
00000050  b9 fa 93 84 98 88 f6 2e  2d 0f a5 35 d4 5c 48 1d  |........-..5.\H.|
00000060  97 45 62 63 d5 28 2c 78  ea 14 07 1e 5a d9 36 e7  |.Ebc.(,x....Z.6.|
00000070  68 2e f3 45 b6 14 ec 42  73 79 12 13 46 c6 42 59  |h..E...Bsy..F.BY|
00000080  3c 9a 86 7e b5 6c 11 af  3e 73 42 b7 cf a1 40 b1  |<..~.l..>sB...@.|
00000090  55 69 78 f9 70 bc 9e a8  5d 73 c4 37 d5 d1 0b 52  |Uix.p...]s.7...R|
000000a0  38 4b 3c 2e 36 c3 eb ef  1e 5e 07 ba 8e 45 56 e2  |8K<.6....^...EV.|
000000b0  65 f7 35 96 f5 8a c4 bd  0f ac df c6 eb 29 ce ce  |e.5..........)..|
000000c0  e3 a2 63 cb 95 8b 8b 0f  1d 85 39 d9 e2 d3 b4 a4  |..c.......9.....|
000000d0  fb 1c 30 60 be 88 8e 39  b9 bd f6 eb ef eb 98 c6  |..0`...9........|
000000e0  20 a0 05 c9 33 b6 c9 1a  93 73 73 b8 99 52 84 56  | ...3....ss..R.V|
000000f0  94 66 e6 da 7c aa 47 fd  fd ce 3c ff 46 a1 d7 ec  |.f..|.G...<.F...|
00000100  a0 7e 26 1d 22 31 33 6d  cc 3c 8c 39 2d 09 4b fc  |.~&."13m.<.9-.K.|
00000110  f1 a8 8f 5c a3 56 5e bb  f1 42 36 8b 0e 75 12 9a  |...\.V^..B6..u..|
00000120  31 2d 21 94 1e da e1 cb  75 36 97 50 8f ce 1c 93  |1-!.....u6.P....|
00000130  d4 9b 8b 20 61 a2 71 fa  fa b6 ee cf 47 eb 8f 2c  |... a.q.....G..,|
00000140  bd b2 f3 66 b4 31 58 98  9f 72 0a 52 a9 b2 fd bc  |...f.1X..r.R....|
00000150  a3 59 46 11 79 5e 0b 2b  58 4f 8e 90 21 7e ae aa  |.YF.y^.+XO..!~..|
00000160  c5 0e e2 1a 03 27 86 8d  c4 9d fb 57 4a a9 76 8c  |.....'.....WJ.v.|
00000170  ba bd 4b 29 50 ce ef e9  16 27 42 13 92 13 1c d3  |..K)P....'B.....|
00000180  b3 b3 c3 d6 d2 9d fb 0b  0e 17 b8 ea c7 5f b2 f7  |............._..|
00000190  e9 2b ef b6 59 6a 35 60  00 00 92 48 a9 b7 23 91  |.+..Yj5`...H..#.|
000001a0  34 93 6e c9 fe 38 85 84  0b 06 d5 c2 23 79 9b 7b  |4.n..8......#y.{|
000001b0  91 49 b9 74 31 01 52 bd  2f ec b6 09 32 d2 00 fe  |.I.t1.R./...2...|
000001c0  ff ff 83 fe ff ff 02 40  ea 07 00 f8 30 08 00 fe  |.......@....0...|
000001d0  ff ff 05 fe ff ff 92 3a  1b 10 70 85 5a 00 00 00  |.......:..p.Z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error


```

---

### Post by sikander3786 on 2011-05-22
From the output you posted above, looks like you are missing /bootmgr and some other files for Windows 7 which are needed for a successful boot. Normally, the files are:

```
/bootmgr /Boot/BCD /Windows/System32/winload.exe
```

Whereas all you've got is,

```
sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        [COLOR="Red"]/Windows/System32/winload.exe[/COLOR]
```

So the best workaround from here would be to repair Windows 7 startup first which would result in removal of Grub. Once you are able to boot Windows 7 successfully independent of Grub, you'll need to re-install Grub for dual-booting.

You'll need Windows 7 repair/install discs. If you don't have one, you can download a recovery image here. Its legit.

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

For instructions on how to repair Windows 7 startup, (you'll need to apply it 3 times at least before you actually start booting Windows 7 successfully)

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)

If that doesn't help in your case, you might need to try the Bootrec.exe tool from command-line.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Once able to boot Windows 7 successfully, boot an Ubuntu 11.04 Live CD/USB and go to Terminal and execute these commands:

```
sudo mount /dev/sda5 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sd[COLOR="Red"]a[/COLOR]
```

Note for the second command, it is just sda without an integer.

Reboot and hopefully you'll see the Grub menu for dual booting. If not, you might need to run this command from HDD booted Ubuntu Terminal:

```
sudo update-grub
```

Good Luck!

---

### Post by kansasnoob on 2011-05-22
> **sikander3786 said:**
> From the output you posted above, looks like you are missing /bootmgr and some other files for Windows 7 which are needed for a successful boot. Normally, the files are:

```
/bootmgr /Boot/BCD /Windows/System32/winload.exe
```

Whereas all you've got is,

```
sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        [COLOR="Red"]/Windows/System32/winload.exe[/COLOR]
```

So the best workaround from here would be to repair Windows 7 startup first which would result in removal of Grub. Once you are able to boot Windows 7 successfully independent of Grub, you'll need to re-install Grub for dual-booting.

You'll need Windows 7 repair/install discs. If you don't have one, you can download a recovery image here. Its legit.

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

For instructions on how to repair Windows 7 startup, (you'll need to apply it 3 times at least before you actually start booting Windows 7 successfully)

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)

If that doesn't help in your case, you might need to try the Bootrec.exe tool from command-line.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Once able to boot Windows 7 successfully, boot an Ubuntu 11.04 Live CD/USB and go to Terminal and execute these commands:

```
sudo mount /dev/sda5 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sd[COLOR="Red"]a[/COLOR]
```

Note for the second command, it is just sda without an integer.

Reboot and hopefully you'll see the Grub menu for dual booting. If not, you might need to run this command from HDD booted Ubuntu Terminal:

```
sudo update-grub
```

Good Luck!

I think actually those other boot files are in sda1:

> sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   [B][COLOR="Red"]Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 374437352 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos7)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.[/COLOR][/B]
    Operating System:  
    Boot files:        **/bootmgr /Boot/BCD**

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        **/Windows/System32/winload.exe**

But the problem highlighted in red is this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by sikander3786 on 2011-05-23
Thanks for pointing out kansasnoob, I guess I overlooked the output of boot script. Apologies to the OP. You can follow kansasnoob's link which seems to be a better/appropriate solution to your problem...

---

### Post by kansasnoob on 2011-05-23
> **sikander3786 said:**
> Thanks for pointing out kansasnoob, I guess I overlooked the output of boot script. Apologies to the OP. You can follow kansasnoob's link which seems to be a better/appropriate solution to your problem...

No big deal. It's easy to overlook certain things, I hate to think how many times I've overlooked something :)

---

### Post by cremersstijn on 2011-05-29
When i use testdisk from [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector), i cannot see 'BackupBS'. The article says i must do a fixboot from the windows CD.

But when i need to do this, i first want to remove one of my two ubuntu installs ([http://ubuntuforums.org/showthread.php?p=10848385#post10848385](http://ubuntuforums.org/showthread.php?p=10848385#post10848385)). Can i do this without a problem? And how to do this? (just format partition?)

Thanks

---

### Post by cremersstijn on 2011-06-02
anyone a suggestion on my last question?

---

### Post by bulldog on 2011-06-02
> **cremersstijn said:**
> anyone a suggestion on my last question?

I didn't read the wiki you're folowing,but it seems to me your primary goal should be to get windows booting again.
So go for that,and if it boots again,you can remove,delete or format any ubuntu install as you like.

Just stumbled over this one,maybe it's of some help to you:

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by mstojnev on 2011-06-03
Hi,
I am new to linux
I installed Ubuntu 11.4 and i want to have dual - boot machine.
On Machine was installed only windows7. Since I install Ubuntu I do not see Grub(or any other) boot loader. When I start computer it automatically boot Ubuntu without prompting to choose OS.

How can I set grub2 to ask me this?
Thanks

here is my partition configuration

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 68347 of the same hard drive for 
                       core.img. core.img is at this location and looks for 
                       (,msdos1)/grub on this drive.
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63        96,389        96,327  83 Linux
/dev/sda2              96,451   488,392,064   488,295,614   f W95 Extended (LBA)
/dev/sda5              96,453    41,062,139    40,965,687  83 Linux
/dev/sda6          41,062,203   102,494,699    61,432,497   7 NTFS / exFAT / HPFS
/dev/sda7         102,494,763   488,392,064   385,897,302   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        270debb2-66db-4ec4-845d-96ee3a40db28   ext3       
/dev/sda5        e35ac242-c2ed-408f-9726-97dbc8e88542   ext4       
/dev/sda6        C81C63B51C639D66                       ntfs       VISTA
/dev/sda7        2C6C72B86C727D00                       ntfs       data
/dev/sdb1        F3B3469AD79D3E90                       ntfs       wd

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot                    ext3       (rw,commit=0)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


============================= sda1/grub/menu.lst: ==============================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e35ac242-c2ed-408f-9726-97dbc8e88542 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=270debb2-66db-4ec4-845d-96ee3a40db28

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 11.04, kernel 2.6.38-8-generic
uuid        270debb2-66db-4ec4-845d-96ee3a40db28
kernel        /vmlinuz-2.6.38-8-generic root=UUID=e35ac242-c2ed-408f-9726-97dbc8e88542 ro quiet splash 
initrd        /initrd.img-2.6.38-8-generic

title        Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid        270debb2-66db-4ec4-845d-96ee3a40db28
kernel        /vmlinuz-2.6.38-8-generic root=UUID=e35ac242-c2ed-408f-9726-97dbc8e88542 ro  single
initrd        /initrd.img-2.6.38-8-generic

title        Chainload into GRUB 2
root        270debb2-66db-4ec4-845d-96ee3a40db28
kernel        /boot/grub/core.img

title        Ubuntu 11.04, memtest86+
uuid        270debb2-66db-4ec4-845d-96ee3a40db28
kernel        /memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

============================= sda1/grub/grub.cfg: ==============================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root e35ac242-c2ed-408f-9726-97dbc8e88542
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 270debb2-66db-4ec4-845d-96ee3a40db28
set locale_dir=($root)/grub/locale
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
    search --no-floppy --fs-uuid --set=root 270debb2-66db-4ec4-845d-96ee3a40db28
    linux    /vmlinuz-2.6.38-8-generic root=UUID=e35ac242-c2ed-408f-9726-97dbc8e88542 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 270debb2-66db-4ec4-845d-96ee3a40db28
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=e35ac242-c2ed-408f-9726-97dbc8e88542 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 270debb2-66db-4ec4-845d-96ee3a40db28
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 270debb2-66db-4ec4-845d-96ee3a40db28
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
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.032615185 = 0.035020288    grub/core.img                                  2
   0.032619953 = 0.035025408    grub/grub.cfg                                  1
   0.030309200 = 0.032544256    grub/menu.lst                                  1
   0.025645733 = 0.027536896    initrd.img-2.6.38-8-generic                   56
   0.008783817 = 0.009431552    vmlinuz-2.6.38-8-generic                      21

=========================== sda5/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e35ac242-c2ed-408f-9726-97dbc8e88542 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=270debb2-66db-4ec4-845d-96ee3a40db28

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 11.04, kernel 2.6.38-8-generic
uuid        270debb2-66db-4ec4-845d-96ee3a40db28
kernel        /vmlinuz-2.6.38-8-generic root=UUID=e35ac242-c2ed-408f-9726-97dbc8e88542 ro quiet splash 
initrd        /initrd.img-2.6.38-8-generic

title        Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid        270debb2-66db-4ec4-845d-96ee3a40db28
kernel        /vmlinuz-2.6.38-8-generic root=UUID=e35ac242-c2ed-408f-9726-97dbc8e88542 ro  single
initrd        /initrd.img-2.6.38-8-generic

title        Chainload into GRUB 2
root        270debb2-66db-4ec4-845d-96ee3a40db28
kernel        /boot/grub/core.img

title        Ubuntu 11.04, memtest86+
uuid        270debb2-66db-4ec4-845d-96ee3a40db28
kernel        /memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root e35ac242-c2ed-408f-9726-97dbc8e88542
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 270debb2-66db-4ec4-845d-96ee3a40db28
set locale_dir=($root)/grub/locale
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
    search --no-floppy --fs-uuid --set=root 270debb2-66db-4ec4-845d-96ee3a40db28
    linux    /vmlinuz-2.6.38-8-generic root=UUID=e35ac242-c2ed-408f-9726-97dbc8e88542 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 270debb2-66db-4ec4-845d-96ee3a40db28
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=e35ac242-c2ed-408f-9726-97dbc8e88542 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 270debb2-66db-4ec4-845d-96ee3a40db28
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 270debb2-66db-4ec4-845d-96ee3a40db28
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext3    defaults        0       2
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.078577518 = 0.084371968    boot/grub/core.img                             2
   0.078582287 = 0.084377088    boot/grub/grub.cfg                             1
   0.076271534 = 0.081895936    boot/grub/menu.lst                             1
   0.071608067 = 0.076888576    boot/initrd.img-2.6.38-8-generic              56
   0.054746151 = 0.058783232    boot/vmlinuz-2.6.38-8-generic                 21
   0.071608067 = 0.076888576    initrd.img                                    56
   0.054746151 = 0.058783232    vmlinuz                                       21

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by oldfred on 2011-06-03
@mstojnev Welcome to the forum

Your issues are different, as most booting issues are. Please start a new thread and repost boot script. You have a variety of issues. Some easy to fix, others maybe not so easy.

---

### Post by mstojnev on 2011-06-03
Thanks for suggestion, Oldfred
I started a new thread : [http://ubuntuforums.org/showthread.php?p=10899297#post10899297](http://ubuntuforums.org/showthread.php?p=10899297#post10899297)
Best regards,
Marjan

> **oldfred said:**
> @mstojnev Welcome to the forum

Your issues are different, as most booting issues are. Please start a new thread and repost boot script. You have a variety of issues. Some easy to fix, others maybe not so easy.

---

### Post by cremersstijn on 2011-10-17
Hi!
I got the same problem again...

So i repaired windows using the windows repair disk.

And then i tried to repair grub, using the following commands:
```
 
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sd[COLOR=Red]a[/COLOR]

```But this ended in a "grub rescue screen" when booting.

So which sda should i mount? How can i know this?

This is the result of the "boot info script":
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........:...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 7702 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   348,988,079   348,781,232   7 NTFS / exFAT / HPFS
/dev/sda3         348,989,438   625,141,759   276,152,322   5 Extended
/dev/sda5         619,210,752   625,141,759     5,931,008  82 Linux swap / Solaris
/dev/sda6         348,989,440   481,781,759   132,792,320  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1008 MB, 1008730112 bytes
16 heads, 32 sectors/track, 3848 cylinders, total 1970176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     1,970,175     1,970,144   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3AEC4511EC44C8B9                       ntfs       System Reserved
/dev/sda2        9830468B30467074                       ntfs       
/dev/sda5        21709a68-3359-437e-b12f-52860a076fd7   swap       
/dev/sda6        5c97f9e2-98eb-4f09-ac4a-f7ece017730d   ext4       
/dev/sdb1        16DE-0B13                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
  set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=5c97f9e2-98eb-4f09-ac4a-f7ece017730d ro  splash vga=788  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=5c97f9e2-98eb-4f09-ac4a-f7ece017730d ro recovery nomodeset  splash vga=788
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=5c97f9e2-98eb-4f09-ac4a-f7ece017730d ro  splash vga=788  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=5c97f9e2-98eb-4f09-ac4a-f7ece017730d ro recovery nomodeset  splash vga=788
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=5c97f9e2-98eb-4f09-ac4a-f7ece017730d ro  splash vga=788  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=5c97f9e2-98eb-4f09-ac4a-f7ece017730d ro recovery nomodeset  splash vga=788
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5c97f9e2-98eb-4f09-ac4a-f7ece017730d ro  splash vga=788  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=5c97f9e2-98eb-4f09-ac4a-f7ece017730d ro recovery nomodeset  splash vga=788
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 5c97f9e2-98eb-4f09-ac4a-f7ece017730d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 3AEC4511EC44C8B9
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
# / was on /dev/sda7 during installation
UUID=5c97f9e2-98eb-4f09-ac4a-f7ece017730d /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda6 during installation
UUID=21709a68-3359-437e-b12f-52860a076fd7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-10-generic              2
               =                boot/initrd.img-2.6.38-11-generic              2
               =                boot/initrd.img-2.6.38-8-generic               2
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-2.6.38-10-generic                 2
               =                boot/vmlinuz-2.6.38-11-generic                 1
               =                boot/vmlinuz-2.6.38-8-generic                  1
               =                boot/vmlinuz-3.0.0-12-generic                  2
               =                initrd.img.old                                 2
               =                vmlinuz                                        2
               =                vmlinuz.old                                    1

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
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  56 38 7b 6c 8e 4b cd bf  c3 36 01 70 43 8d a5 ff  |V8{l.K...6.pC...|
00000010  fb d0 44 09 00 06 05 68  d3 7d 69 80 08 b5 ed 1a  |..D....h.}i.....|
00000020  7d ad 30 01 1b ed 97 b7  b9 97 ff c3 37 b2 77 77  |}.0.........7.ww|
00000030  30 ff f9 1c dc b6 51 c9  0c 0e ba ec c5 1d fb d0  |0.....Q.........|
00000040  cd 97 bc 7c 5a 2b 0f 47  a7 e0 68 b3 71 d8 ac c9  |...|Z+.G..h.q...|
00000050  b9 fa 93 84 98 88 f6 2e  2d 0f a5 35 d4 5c 48 1d  |........-..5.\H.|
00000060  97 45 62 63 d5 28 2c 78  ea 14 07 1e 5a d9 36 e7  |.Ebc.(,x....Z.6.|
00000070  68 2e f3 45 b6 14 ec 42  73 79 12 13 46 c6 42 59  |h..E...Bsy..F.BY|
00000080  3c 9a 86 7e b5 6c 11 af  3e 73 42 b7 cf a1 40 b1  |<..~.l..>sB...@.|
00000090  55 69 78 f9 70 bc 9e a8  5d 73 c4 37 d5 d1 0b 52  |Uix.p...]s.7...R|
000000a0  38 4b 3c 2e 36 c3 eb ef  1e 5e 07 ba 8e 45 56 e2  |8K<.6....^...EV.|
000000b0  65 f7 35 96 f5 8a c4 bd  0f ac df c6 eb 29 ce ce  |e.5..........)..|
000000c0  e3 a2 63 cb 95 8b 8b 0f  1d 85 39 d9 e2 d3 b4 a4  |..c.......9.....|
000000d0  fb 1c 30 60 be 88 8e 39  b9 bd f6 eb ef eb 98 c6  |..0`...9........|
000000e0  20 a0 05 c9 33 b6 c9 1a  93 73 73 b8 99 52 84 56  | ...3....ss..R.V|
000000f0  94 66 e6 da 7c aa 47 fd  fd ce 3c ff 46 a1 d7 ec  |.f..|.G...<.F...|
00000100  a0 7e 26 1d 22 31 33 6d  cc 3c 8c 39 2d 09 4b fc  |.~&."13m.<.9-.K.|
00000110  f1 a8 8f 5c a3 56 5e bb  f1 42 36 8b 0e 75 12 9a  |...\.V^..B6..u..|
00000120  31 2d 21 94 1e da e1 cb  75 36 97 50 8f ce 1c 93  |1-!.....u6.P....|
00000130  d4 9b 8b 20 61 a2 71 fa  fa b6 ee cf 47 eb 8f 2c  |... a.q.....G..,|
00000140  bd b2 f3 66 b4 31 58 98  9f 72 0a 52 a9 b2 fd bc  |...f.1X..r.R....|
00000150  a3 59 46 11 79 5e 0b 2b  58 4f 8e 90 21 7e ae aa  |.YF.y^.+XO..!~..|
00000160  c5 0e e2 1a 03 27 86 8d  c4 9d fb 57 4a a9 76 8c  |.....'.....WJ.v.|
00000170  ba bd 4b 29 50 ce ef e9  16 27 42 13 92 13 1c d3  |..K)P....'B.....|
00000180  b3 b3 c3 d6 d2 9d fb 0b  0e 17 b8 ea c7 5f b2 f7  |............._..|
00000190  e9 2b ef b6 59 6a 35 60  00 00 92 48 a9 b7 23 91  |.+..Yj5`...H..#.|
000001a0  34 93 6e c9 fe 38 85 84  0b 06 d5 c2 23 79 9b 7b  |4.n..8......#y.{|
000001b0  91 49 b9 74 31 01 52 bd  2f ec b6 09 32 d2 00 fe  |.I.t1.R./...2...|
000001c0  ff ff 82 fe ff ff 02 40  1b 10 00 80 5a 00 00 fe  |.......@....Z...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 40 ea 07 00 00  |...........@....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
./boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by oldfred on 2011-10-17
Your command installed part of grub into the Windows boot partition. Windows is not case sensitive so a /boot & /Boot become the same & it is confused.

You have to mount your Ubuntu install partition so the bit of grub2 in the MBR knows where to go for the rest of its boot. Your install is in sda6 so use that not sda1.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda6 if not correct:
sudo fdisk -l
#confirm that linux is sda6
[COLOR=Red]sudo mount /dev/sda6 /mnt[/COLOR]
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root.
[COLOR=Red]sudo grub-install --boot-directory=/mnt/boot /dev/sda[/COLOR]

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

From Ubuntu delete /boot in sda1 that has grub in it, but be careful not to delete /Boot as that has Windows BCD which is essential for Windows booting.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

### Post by cremersstijn on 2011-10-17
Thanks man!

---

