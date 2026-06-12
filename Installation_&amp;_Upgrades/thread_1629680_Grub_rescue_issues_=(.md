---
title: "Grub rescue issues =("
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by BJones007 on 2010-11-24
Hey guys I received this msg today after my idiot cousing selected the vista loader in the grubloader menu >  Loading grub.
error: no such partition
Entering rescue mode... 
grub rescue>  

I've read a few post on the forum about same and even tried running a few of the commands listed (ls hd0, msdos3/boot/grub or ls hd0, sda4) but I keep receiving the error msg stating that there is "no such partition" and I just can't seem to fix the problem.

I also tried the following command in terminal after booting Ubuntu from a usb drive ```
 sudo mount /dev/sda2/mnt 
``` but I got this error msg  
"mount: can't find /dev/sda2/mnt in /etc/fstab or /etc/mtab"  I also checked for the folders in the directory /etc/ but mtab and fstab were both missing. A little help

---

### Post by sikander3786 on 2010-11-24
First of all, we would like to see the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us exactly nearly everything about your boot setup.

And the command you are try needs a space so it should look like,

```
 sudo mount /dev/sda2 /mnt
```

If you are sure, you can re-install Grub2 following this.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

And if not, post the output of above mentioned script to let us figure out the problem for you.

Thanks

---

### Post by garvinrick4 on 2010-11-24
If you are running Windows 7 the Vista loader is a recovery partition for 7 and linux just reads it as Vista, Windows thing.
Notice on sda4 near bottom of menuentry it says Vista and it is the whole copy of Windows 7 in virgin state 
for my windows 7. Only booted into once to reinstall Windows 7 I do believe if memory is correct. 
### Give previous post his bootinfoscript will tell story!!
```
rick@rick-laptop:~$ grep menuentry /boot/grub/grub.cfg
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Windows 7 (loader) (on /dev/sda1)" {
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (on /dev/sda10)" {
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode) (on /dev/sda10)" {
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (on /dev/sda10)" {
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode) (on /dev/sda10)" {
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda11)" {
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda11)" {
menuentry "Ubuntu, with Linux 2.6.37-5-generic (on /dev/sda12)" {
menuentry "Ubuntu, with Linux 2.6.37-5-generic (recovery mode) (on /dev/sda12)" {
menuentry "Ubuntu, with Linux 2.6.37-3-generic (on /dev/sda12)" {
menuentry "Ubuntu, with Linux 2.6.37-3-generic (recovery mode) (on /dev/sda12)" {
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda13)" {
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda13)" {
menuentry "Ubuntu, with Linux 2.6.35-20-generic (on /dev/sda13)" {
menuentry "Ubuntu, with Linux 2.6.35-20-generic (recovery mode) (on /dev/sda13)" {
menuentry "Windows 7 (loader) (on /dev/sda2)" {
menuentry "Windows Vista (loader) (on /dev/sda4)" {
menuentry "Ubuntu, with Linux 2.6.37-5-generic (on /dev/sda5)" {
menuentry "Ubuntu, with Linux 2.6.37-5-generic (recovery mode) (on /dev/sda5)" {
menuentry "Ubuntu, with Linux 2.6.37-4-generic (on /dev/sda5)" {
menuentry "Ubuntu, with Linux 2.6.37-4-generic (recovery mode) (on /dev/sda5)" {
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" {
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" {
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" {
rick@rick-laptop:~$ 

```

---

### Post by aarons6 on 2010-11-24
something doesnt look right..

are you using grub or grub2?

can you boot back into linux?
if its grub you may need the make active and the chain load commands

---

### Post by BJones007 on 2010-11-24
> **aarons6 said:**
> something doesnt look right..

are you using grub or grub2?

can you boot back into linux?
if its grub you may need the make active and the chain load commands
I'm using Grub 2 and no I can't boot into any of my OS's

---

### Post by BJones007 on 2010-11-24
Here's the  bootinfoscript, I didn't know what exactly to copy and paste so I pasted everything >.< ```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #4 for /boot/burg.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 4007 MB, 4007657472 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     7,827,455     7,827,393   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    14,683,409    14,683,347  12 Compaq diagnostics
/dev/sdb2    *     14,684,160   164,159,579   149,475,420   7 HPFS/NTFS
/dev/sdb3         164,161,536   306,628,607   142,467,072  83 Linux
/dev/sdb4         306,630,654   312,580,095     5,949,442   5 Extended
/dev/sdb5         306,630,656   312,580,095     5,949,440  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C28-4354                              vfat       KINGSTON                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E66849FD6849CD4D                       ntfs       PQSERVICE                     
/dev/sdb2        D698D37898D35619                       ntfs       Windows                       
/dev/sdb3        77c14a19-9da9-4208-a701-4c941bff79b5   ext4                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        2ebf551b-79b4-4c7e-9ef5-6681621202d8   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 77c14a19-9da9-4208-a701-4c941bff79b5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 77c14a19-9da9-4208-a701-4c941bff79b5
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

### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 77c14a19-9da9-4208-a701-4c941bff79b5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 77c14a19-9da9-4208-a701-4c941bff79b5
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
menuentry 'Ubuntu 10.10 Maverick Meerkat' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 77c14a19-9da9-4208-a701-4c941bff79b5
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=77c14a19-9da9-4208-a701-4c941bff79b5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu 10.10 Maverick Meerkat (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 77c14a19-9da9-4208-a701-4c941bff79b5
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=77c14a19-9da9-4208-a701-4c941bff79b5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 77c14a19-9da9-4208-a701-4c941bff79b5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 77c14a19-9da9-4208-a701-4c941bff79b5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e66849fd6849cd4d
    chainloader +1
}
menuentry "Windows 7" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set d698d37898d35619
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
### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 77c14a19-9da9-4208-a701-4c941bff79b5
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=77c14a19-9da9-4208-a701-4c941bff79b5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 77c14a19-9da9-4208-a701-4c941bff79b5
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=77c14a19-9da9-4208-a701-4c941bff79b5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 77c14a19-9da9-4208-a701-4c941bff79b5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 77c14a19-9da9-4208-a701-4c941bff79b5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e66849fd6849cd4d
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set d698d37898d35619
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 77c14a19-9da9-4208-a701-4c941bff79b5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 77c14a19-9da9-4208-a701-4c941bff79b5
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
menuentry 'Ubuntu 10.10 Maverick Meerkat' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 77c14a19-9da9-4208-a701-4c941bff79b5
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=77c14a19-9da9-4208-a701-4c941bff79b5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu 10.10 Maverick Meerkat (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 77c14a19-9da9-4208-a701-4c941bff79b5
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=77c14a19-9da9-4208-a701-4c941bff79b5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 77c14a19-9da9-4208-a701-4c941bff79b5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 77c14a19-9da9-4208-a701-4c941bff79b5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e66849fd6849cd4d
    chainloader +1
}
menuentry "Windows 7" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set d698d37898d35619
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
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb4 during installation
UUID=77c14a19-9da9-4208-a701-4c941bff79b5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=2ebf551b-79b4-4c7e-9ef5-6681621202d8 none            swap    sw              0       0

=================== sdb3: Location of files loaded by Grub: ===================


 131.4GB: boot/grub/core.img
 114.4GB: boot/grub/grub.cfg
  94.6GB: boot/initrd.img-2.6.35-22-generic
 131.4GB: boot/vmlinuz-2.6.35-22-generic
  94.6GB: initrd.img
 131.4GB: vmlinuz 
```

---

### Post by sikander3786 on 2010-11-24
Yes you needed to paste the whole of that output :-)

The problem lies here

>  => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #4 for /boot/burg.

I hope you had tried to install BURG to bring some eye-candy to your Grub menu and it instead brought some pain :-)

However in my opinion, the best workaround would be to re-install Grub2 and later if you want, you can try installing/tweaking Burg again.

Boot from a Live CD and do these commands.

```
sudo mount /dev/sdb3 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

Reboot and you should be able to boot Ubuntu now. If you don't see Windows listed in the Grub menu, from your Ubuntu install,

```
sudo update-grub
```

And it should now add an entry for Windows as well.

Good Luck!

---

### Post by BJones007 on 2010-11-24
> **sikander3786 said:**
> Yes you needed to paste the whole of that output :-)

The problem lies here



I hope you had tried to install BURG to bring some eye-candy to your Grub menu and it instead brought some pain :-)

However in my opinion, the best workaround would be to re-install Grub2 and later if you want, you can try installing/tweaking Burg again.

Boot from a Live CD and do these commands.

```
sudo mount /dev/sdb3 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

Reboot and you should be able to boot Ubuntu now. If you don't see Windows listed in the Grub menu, from your Ubuntu install,

```
sudo update-grub
```

And it should now add an entry for Windows as well.

Good Luck!
Thanks dude. It actually worked. I'm now running ubuntu again.

About Burg though, is it the reason this problem arose?

---

### Post by sikander3786 on 2010-11-25
> 
About Burg though, is it the reason this problem arose?

I have never used that so can't comment on that. Might be you didn't configure it properly. You can try installing that again and can follow the above steps if it agains messes your boot ;-)

Happy Ubuntu-ing!

---

