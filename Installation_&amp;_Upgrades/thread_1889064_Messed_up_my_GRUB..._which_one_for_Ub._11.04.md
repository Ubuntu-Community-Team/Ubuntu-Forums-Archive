---
title: "Messed up my GRUB... which one for Ub. 11.04?"
date: 2011-11-30
forum: Installation &amp; Upgrades
---

### Post by gears on 2011-11-30
I have a dual-boot Ubuntu 11.04-XP, and after I did my 11.04 fresh install, some time ago, the new grub did not see the XP OS. As a matter of fact grub did not even display anything and went right to Ubuntu.

I now want to use XP again (old work stuff tweaks), and foolishly installed a 0.99 grub, ignoring the dependency warning.

Which grub package should I pick with Synaptic to reinstall a new "new" GRUB. regular 32-bit? 
There seem to be a few offerings, and want to install the correct one.

---

### Post by drs305 on 2011-11-30
Boot either a 11.04 or 11.10 LiveCD. This will ensure you install the 1.99 version of Grub 2.

If you aren't familiar with how to install it via a LiveCD and chroot procedure, click the "Chroot" link in my signature line. You will probably want to purge/reinstall if Grub legacy really is installed on the system. 

If you are able to run it without booting the LiveCD, you don't have to chroot and can just run the purge/reinstall portion of the guide. Just make sure you have an Internet connection before purging anything.

---

### Post by gears on 2011-11-30
The boot info file seems to say I have Grub2:
-------------------------------
=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of the same hard drive for core.img. core.img is at this location and looks for (,msdos1)/grub on this drive.

 => Windows is installed in the MBR of /dev/sdb.
-----------------------------

I will try the boot repair graphical tool now.

---

### Post by gears on 2011-11-30
Grub2 is back working... and still isn't seeing the WinXP OS though.


(with a little video resolution dance before getting there)

---

### Post by drs305 on 2011-11-30
> **gears said:**
> ... and still isn't seeing the WinXP OS though.

Have you run the following since you booted back into Ubuntu:
```
sudo update-grub
```
Watch the terminal output to see if Grub finds Windows.

If you download/run the boot info script and post the contents of RESULTS.txt we may be able to figure out why Windows isn't being found.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by gears on 2011-11-30
Here is the boot info script output:
                 

```
 Boot Info Script 0.60    from 17 May 2011
============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732 root 
    set 
    prefix=($root)/grub--------------------------------------------------------
    ------------------------.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 737599 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63     4,096,574     4,096,512  83 Linux
/dev/sda2           4,096,575    39,873,329    35,776,755  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    84,180,599    84,180,537   7 NTFS / exFAT / HPFS
/dev/sdb2          84,180,600    88,662,734     4,482,135  83 Linux
/dev/sdb3          88,662,796   312,576,704   223,913,909   5 Extended
/dev/sdb5          88,662,798   167,196,671    78,533,874  83 Linux
/dev/sdb6         308,030,373   312,576,704     4,546,332  82 Linux swap / Solaris
/dev/sdb7         167,204,583   308,030,309   140,825,727  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732   ext3       
/dev/sda2        f4466e28-f129-4b3c-b6d9-f3cfd312548e   ext3       
/dev/sdb1        64049E4B049E205A                       ntfs       WinDrive
/dev/sdb2        830ffb11-2245-4c31-85f4-21145af1c5f3   ext3       
/dev/sdb5        47e08b5f-b45d-41f7-a456-1c5fa847ebe5   ext3       
/dev/sdb6        7ed3dc43-5702-4c84-8c05-44e6852f0f3d   swap       
/dev/sdb7        23f400cf-de59-43ef-8c84-ee9b3a9d9208   ext3       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot                    ext3       (rw,commit=0)
/dev/sdb5        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sdb7        /home                    ext3       (rw,commit=0)


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
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 47e08b5f-b45d-41f7-a456-1c5fa847ebe5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
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
menuentry 'Ubuntu, with Linux 2.6.38-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	linux	/vmlinuz-2.6.38-13-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	echo	'Loading Linux 2.6.38-13-generic ...'
	linux	/vmlinuz-2.6.38-13-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	linux	/vmlinuz-2.6.38-12-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	echo	'Loading Linux 2.6.38-12-generic ...'
	linux	/vmlinuz-2.6.38-12-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	linux	/vmlinuz-2.6.38-11-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/vmlinuz-2.6.38-11-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	linux	/vmlinuz-2.6.38-10-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/vmlinuz-2.6.38-10-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	linux	/vmlinuz-2.6.38-8-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/vmlinuz-2.6.38-8-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	linux16	/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.367244244 = 0.394325504    grub/core.img                                  1
   0.351607800 = 0.377536000    grub/grub.cfg                                  1
   0.081851482 = 0.087887360    initrd.img-2.6.38-10-generic                   5
   0.105830669 = 0.113634816    initrd.img-2.6.38-11-generic                   5
   0.093078136 = 0.099941888    initrd.img-2.6.38-12-generic                   7
   0.136874676 = 0.146968064    initrd.img-2.6.38-13-generic                  11
   0.131614208 = 0.141319680    initrd.img-2.6.38-8-generic                    6
   0.043319225 = 0.046513664    vmlinuz-2.6.38-10-generic                      3
   0.050342083 = 0.054054400    vmlinuz-2.6.38-11-generic                      3
   0.090194225 = 0.096845312    vmlinuz-2.6.38-12-generic                      3
   0.113627911 = 0.122007040    vmlinuz-2.6.38-13-generic                      3
   0.069861889 = 0.075013632    vmlinuz-2.6.38-8-generic                       3

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 47e08b5f-b45d-41f7-a456-1c5fa847ebe5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
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
menuentry 'Ubuntu, with Linux 2.6.38-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	linux	/vmlinuz-2.6.38-13-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	echo	'Loading Linux 2.6.38-13-generic ...'
	linux	/vmlinuz-2.6.38-13-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	linux	/vmlinuz-2.6.38-12-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	echo	'Loading Linux 2.6.38-12-generic ...'
	linux	/vmlinuz-2.6.38-12-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	linux	/vmlinuz-2.6.38-11-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/vmlinuz-2.6.38-11-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	linux	/vmlinuz-2.6.38-10-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/vmlinuz-2.6.38-10-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	linux	/vmlinuz-2.6.38-8-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/vmlinuz-2.6.38-8-generic root=UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 64d17e6f-08d7-4a8f-9a0a-0d3d08ecd732
	linux16	/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=============================== sdb5/etc/fstab: ================================

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
UUID=47e08b5f-b45d-41f7-a456-1c5fa847ebe5 /               ext3    errors=remount-ro 0       1
/dev/sda1       /boot           ext3    defaults        0       2
# /home was on /dev/sdb7 during installation
UUID=23f400cf-de59-43ef-8c84-ee9b3a9d9208 /home           ext3    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=7ed3dc43-5702-4c84-8c05-44e6852f0f3d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  42.644930840 = 45.789645824   boot/grub/core.img                             1
  42.629294395 = 45.772856320   boot/grub/grub.cfg                             1
  42.359538078 = 45.483207680   boot/initrd.img-2.6.38-10-generic              5
  42.383517265 = 45.508955136   boot/initrd.img-2.6.38-11-generic              5
  42.370764732 = 45.495262208   boot/initrd.img-2.6.38-12-generic              7
  42.414561272 = 45.542288384   boot/initrd.img-2.6.38-13-generic             11
  42.409300804 = 45.536640000   boot/initrd.img-2.6.38-8-generic               6
  42.321005821 = 45.441833984   boot/vmlinuz-2.6.38-10-generic                 3
  42.328028679 = 45.449374720   boot/vmlinuz-2.6.38-11-generic                 3
  42.367880821 = 45.492165632   boot/vmlinuz-2.6.38-12-generic                 3
  42.391314507 = 45.517327360   boot/vmlinuz-2.6.38-13-generic                 3
  42.347548485 = 45.470333952   boot/vmlinuz-2.6.38-8-generic                  3
  42.414561272 = 45.542288384   initrd.img                                    11
  42.370764732 = 45.495262208   initrd.img.old                                 7
  42.391314507 = 45.517327360   vmlinuz                                        3
  42.367880821 = 45.492165632   vmlinuz.old                                    3

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error


```

---

### Post by drs305 on 2011-11-30
The boot info script found what could be your Windows installation on sdb1:
> 
sdb1: 
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        

However, the script did not locate any of the Windows boot files/folders. Normally for XP there should be /boot.ini, /ntldr /NTDETECT.COM

Windows isn't in the menu because Grub needs to find those items before it will build a menu entry. 

More importantly, if the script is correct you won't be able to boot XP until you restore the boot files. I don't use Windows but here is a link to a post by forum member *oldfred* which provides some information on repairing Windows:
[http://ubuntuforums.org/showpost.php?p=11031000&postcount=11]("http://ubuntuforums.org/showpost.php?p=11031000&postcount=11")

The repair will overwrite the Grub information in the MBR. It's best to get Windows working independently first, and then you can reinstall Grub back to the MBR once you get Windows working.

---

### Post by gears on 2011-12-01
Thanks

Some of oldfred's instructions, as you suggest scare me a bit (especially at 5 a.m,!):

[INDENT]FIXBOOT C:
BOOTCFG /rebuild # rebuilds boot.ini
chkdsk c: /r[/INDENT]

It seems that he writes with two separate drives in mind, whereas I have my 11.04 and XP are on same drive.

---

### Post by drs305 on 2011-12-01
The commands use "C" drive (which would be sdb in linux terms), but you will have to determine how the Windows drive is designated and change the drive letter if necessary. To remove the chance of error, you could always unplug your Ubuntu drive before making the repair.

The Windows repair commands generally do two things - sometimes only one of them is necessary but in your case you will need both. 

First, the MBR must point to the Windows bootloader folder/files. For the Windows bootloader, the correct partition must have the boot flag, which is how the Windows partition is found. The fixmbr repair directs the system to the Windows boot files.

The second repair makes sure the proper files exist for Windows to actually boot the system. (boot.ini, etc) 

The repair commands don't touch the contents of non-Windows partitions. They will wipe out the Grub information in the MBR of the Windows drive*. Generally we recommend getting Windows working independently. The repair does not touch the partition Grub files, so once Windows is working only the MBR instructions have to be altered to regain Grub control of the boot.

* Since Windows and Ubuntu are on different drives, you can keep Windows in the sd**b** drive's MBR and keep Grub on the MBR of sd**a**. If BIOS boots the sda drive first, you would see the Grub menu. If you change the BIOS to boot sdb first, you would see the Windows boot menu.

Should you lose Grub at boot and already have the BIOS booting the correct drive, you can reinstall Grub to the sda drive by booting the LiveCD and running the following commands:
```
sudo mount /dev/sda1 /mnt # Mountsyour Ubuntu partition
sudo grub-install --root-directory=/mnt /dev/sda # Writes Grub info to MBR of sda drive

```

Make sure the BIOS is set to boot the Ubuntu drive first.

Of course you can have Grub installed to both drives if desired - you just won't have a Windows fallback option to access Windows if Grub stops working.

---

### Post by gears on 2011-12-07
Thanks drs.

I got my Grub to show the Windows OS, and the "link' works!


Minor problem: Ubuntu works fine,but the Win side launches and quits after the splash screen, which is not a Linux problem (while the docs on the Win side are seen by Ubuntu, and are functional. 
I will study my Windows problem separately, and probably run another repair cycle.

---

