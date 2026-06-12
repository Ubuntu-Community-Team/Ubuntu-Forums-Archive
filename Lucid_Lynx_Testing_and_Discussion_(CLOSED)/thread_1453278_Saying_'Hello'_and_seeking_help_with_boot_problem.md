---
title: "Saying 'Hello' and seeking help with boot problem"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Usksider on 2010-04-13
Hello everyone, I'm new here and thought it polite to say "Hi" to one and all... I'm also in need of some help.

I'd been happily using 9.10 for some time - my first real venture into Linux - although I should admit I didn't understand/don't understand how it 'did' things; I kind of knew what I was doing with Windows, but allowed Ubuntu to lead me by the nose so to speak.

A week back I decided to be brave and installed the Lucid Lynx and that's when my problems started. I have a dual-boot system with Windows 7 installed first and Linux second. After I upgraded from 9.10 to 10.04 my computer wouldn't boot into Windows.

My first thought was to look at Grub and I followed advice given here to purge Grub2 and reinstall. It didn't work. :(

Looking around it was obvious that others have experienced the same problem and I've been trying to follow various threads and implement the solutions without success. It may be that I'm simply not doing the right things or that I'm even more confused that I think I am... :confused:

I'm sorry for dragging this topic up again and apologise if I should've posted this elsewhere.

I'm attaching a boot info script log - it really doesn't mean much to me, but I know some of you guys understand these things. On bended knee, I'm begging help... pretty please...

                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /grub/grub.cfg /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda5 and looks 
                       at sector 544367254 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /grub/core.img /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   307,227,059   307,226,997   7 HPFS/NTFS
/dev/sda2         307,227,060   976,768,064   669,541,005   f W95 Ext d (LBA)
/dev/sda5         522,674,838   958,630,679   435,955,842  83 Linux
/dev/sda6         958,630,743   976,768,064    18,137,322  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,125,385,379 1,125,385,317   7 HPFS/NTFS
/dev/sdb2       1,125,385,380 1,953,520,064   828,134,685   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        EEC8AA36C8A9FD49                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7b4f54b8-5154-4d6e-baa8-46cb683a4db4   ext2                                     
/dev/sda6        5ba4e3bf-aed1-4cd3-9d43-9ce7b465c12c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        28EAE8C2EAE88D7E                       ntfs       HD-HSU2                       
/dev/sdb2        C41A3AFB1A3AEA56                       ntfs       HD-HSU3                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext2       (rw,errors=remount-ro)
/dev/sda1        /windows                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2        /media/HD-HSU3_          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/HD-HSU2_          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


============================= sda1/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: grub/grub.cfg

=========================== sda5/boot/grub/menu.lst: ===========================

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
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

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
# kopt=root=UUID=7b4f54b8-5154-4d6e-baa8-46cb683a4db4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7b4f54b8-5154-4d6e-baa8-46cb683a4db4

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

title        Ubuntu lucid (development branch), kernel 2.6.32-20-generic-pae
uuid        7b4f54b8-5154-4d6e-baa8-46cb683a4db4
kernel        /boot/vmlinuz-2.6.32-20-generic-pae root=UUID=7b4f54b8-5154-4d6e-baa8-46cb683a4db4 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-20-generic-pae
quiet

title        Ubuntu lucid (development branch), kernel 2.6.32-20-generic-pae (recovery mode)
uuid        7b4f54b8-5154-4d6e-baa8-46cb683a4db4
kernel        /boot/vmlinuz-2.6.32-20-generic-pae root=UUID=7b4f54b8-5154-4d6e-baa8-46cb683a4db4 ro  single
initrd        /boot/initrd.img-2.6.32-20-generic-pae

title        Ubuntu lucid (development branch), kernel 2.6.32-19-generic-pae
uuid        7b4f54b8-5154-4d6e-baa8-46cb683a4db4
kernel        /boot/vmlinuz-2.6.32-19-generic-pae root=UUID=7b4f54b8-5154-4d6e-baa8-46cb683a4db4 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-19-generic-pae
quiet

title        Ubuntu lucid (development branch), kernel 2.6.32-19-generic-pae (recovery mode)
uuid        7b4f54b8-5154-4d6e-baa8-46cb683a4db4
kernel        /boot/vmlinuz-2.6.32-19-generic-pae root=UUID=7b4f54b8-5154-4d6e-baa8-46cb683a4db4 ro  single
initrd        /boot/initrd.img-2.6.32-19-generic-pae

title        Ubuntu lucid (development branch), kernel 2.6.31-20-generic-pae
uuid        7b4f54b8-5154-4d6e-baa8-46cb683a4db4
kernel        /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=7b4f54b8-5154-4d6e-baa8-46cb683a4db4 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic-pae
quiet

title        Ubuntu lucid (development branch), kernel 2.6.31-20-generic-pae (recovery mode)
uuid        7b4f54b8-5154-4d6e-baa8-46cb683a4db4
kernel        /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=7b4f54b8-5154-4d6e-baa8-46cb683a4db4 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic-pae

title        Chainload into GRUB 2
root        7b4f54b8-5154-4d6e-baa8-46cb683a4db4
kernel        /boot/grub/core.img

title        Ubuntu lucid (development branch), memtest86+
uuid        7b4f54b8-5154-4d6e-baa8-46cb683a4db4
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 7b4f54b8-5154-4d6e-baa8-46cb683a4db4
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 7b4f54b8-5154-4d6e-baa8-46cb683a4db4
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
menuentry "Ubuntu, with Linux 2.6.32-20-generic-pae" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7b4f54b8-5154-4d6e-baa8-46cb683a4db4
    linux    /boot/vmlinuz-2.6.32-20-generic-pae root=UUID=7b4f54b8-5154-4d6e-baa8-46cb683a4db4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-20-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-20-generic-pae (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7b4f54b8-5154-4d6e-baa8-46cb683a4db4
    echo    Loading Linux 2.6.32-20-generic-pae ...
    linux    /boot/vmlinuz-2.6.32-20-generic-pae root=UUID=7b4f54b8-5154-4d6e-baa8-46cb683a4db4 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-20-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic-pae" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7b4f54b8-5154-4d6e-baa8-46cb683a4db4
    linux    /boot/vmlinuz-2.6.32-19-generic-pae root=UUID=7b4f54b8-5154-4d6e-baa8-46cb683a4db4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-19-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic-pae (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7b4f54b8-5154-4d6e-baa8-46cb683a4db4
    echo    Loading Linux 2.6.32-19-generic-pae ...
    linux    /boot/vmlinuz-2.6.32-19-generic-pae root=UUID=7b4f54b8-5154-4d6e-baa8-46cb683a4db4 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-19-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic-pae" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7b4f54b8-5154-4d6e-baa8-46cb683a4db4
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=7b4f54b8-5154-4d6e-baa8-46cb683a4db4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic-pae (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7b4f54b8-5154-4d6e-baa8-46cb683a4db4
    echo    Loading Linux 2.6.31-20-generic-pae ...
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=7b4f54b8-5154-4d6e-baa8-46cb683a4db4 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7b4f54b8-5154-4d6e-baa8-46cb683a4db4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7b4f54b8-5154-4d6e-baa8-46cb683a4db4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set eec8aa36c8a9fd49
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=7b4f54b8-5154-4d6e-baa8-46cb683a4db4 /               ext2    errors=remount-ro 0       1
# /windows was on /dev/sda1 during installation
UUID=EEC8AA36C8A9FD49 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
UUID=5ba4e3bf-aed1-4cd3-9d43-9ce7b465c12c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 381.5GB: boot/grub/core.img
 381.4GB: boot/grub/grub.cfg
 278.6GB: boot/grub/menu.lst
 381.5GB: boot/grub/stage2
 381.3GB: boot/initrd.img-2.6.31-20-generic-pae
 381.4GB: boot/initrd.img-2.6.32-19-generic-pae
 381.3GB: boot/initrd.img-2.6.32-20-generic-pae
 381.3GB: boot/vmlinuz-2.6.31-20-generic-pae
 399.1GB: boot/vmlinuz-2.6.32-19-generic-pae
 381.4GB: boot/vmlinuz-2.6.32-20-generic-pae
 283.1GB: grub/core.img
 381.3GB: initrd.img
 381.4GB: initrd.img.old
 381.4GB: vmlinuz
 399.1GB: vmlinuz.old

```

---

### Post by lisati on 2010-04-13
Moved to Lucid Lynx Testing and Discussion

---

### Post by WitchCraft on 2010-04-13
I had this problems on earlier versions of Linux.

Take a look at the following entry from /boot/grub/menu.lst
> 
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#


You see the line:
```

root (hd0,1)

```

When multi-booting, grub used to mix up the device and hd numbers.

Try altering it to root (hd0,1) or (hd1,0) or (hd1,1) etc.
One will eventually work.

Note that you should change the entry that is not commented out (entry not beginning with #)

---

### Post by aviramof on 2010-04-13
Hello to you i too had many problems in the past with dual boot Microsoft Os's with Ubuntu 10.04 so i copy pasta here for you a solution that was given me a long time ago by vmc if i remember correctly and so far he had helped me a lot i'm hopping it would do the same for you

```
There really are two ways to fix that:

#1. Change the boot priority in BIOS.

#2. Install grub2 to the mbr of both drives by booting an Ubuntu Live CD and from the Live Desktop run:

Code:

sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt

Code:

sudo grub-install /dev/sda

Code:

sudo grub-install /dev/sdb

Code:

exit

Code:

sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt

Then if you ever decide to get rid of Ubuntu and want the Windows MBR back just boot your Ubuntu Live CD and run:

Code:

sudo apt-get install lilo

Code:

sudo lilo -M /dev/sdb mbr
```

i think that if you install grub 2 on bote sda and sdb or change the boot order in bios there is no way it wouldn't work properly and i can see " No boot loader is installed in the MBR of /dev/sdb" maybe this is your problem.


Good Luck:)

---

### Post by Usksider on 2010-04-13
> **WitchCraft said:**
> I had this problems on earlier versions of Linux.

Take a look at the following entry from /boot/grub/menu.lst


You see the line:
```

root (hd0,1)

```When multi-booting, grub used to mix up the device and hd numbers.

Try altering it to root (hd0,1) or (hd1,0) or (hd1,1) etc.
One will eventually work.

Note that you should change the entry that is not commented out (entry not beginning with #)


Thanks for this WitchCraft: I appreciate your time.

I've tried editing the splash screen menu for Windows boot (pressing 'E' to edit then Ctrl+x to boot) using every combination from 0,0 to 3,3 for Windows location with no luck.  :(

---

### Post by Usksider on 2010-04-13
Hi Aviramof

Thanks for your reply. I should have mentioned, my second drive sdb1/sdb2 is portable USB drive and used for data storage only.

I've tried mounting on sda as you suggest, but without success. I'll have to keep trawling...

---

### Post by ubername on 2010-04-13
Edit - see my last post  -- remove quotes from *set root='(hd0,1)'*

Hi

I notice something which might help:

You have both a menu.lst and a grub.cfg on sda5 /boot/grub.

I thought that Grub2 (which is the replacement for legacy grub) only uses grub.cfg. However I note that  the section

```
=================== sda5: Location of files loaded by Grub: ===================

381.5GB: boot/grub/core.img
381.4GB: boot/grub/grub.cfg
278.6GB: boot/grub/menu.lst

```
mentions menu.lst, so it is not as simple as it seems.

However, what you have been doing (editing the entry from the 'splash screen' (not technically it's proper name - I think it is called the grub menu, but I know what you mean!)) is the right thing. I am sure that you have been amending the grub.cfg entry because legacy grub did not use the 'ctrl-x' to boot approach.

Do you get any error messages when you select the entry "Windows 7 (loader) (on /dev/sda1)" from the menu? It would be useful to know exactly what happens when you select this option (Don't edit it - just select it from the grub menu)

I would suggest renaming the menu.lst file as a first step to make sure that it is not part of the problem

e.g.

```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.old
```



Also, go into synaptic package manager and find 'grub' and 'grub2'. If they are both installed, mark 'grub' for complete removal. Then run
```
sudo update-grub
```

Let us know how you get on.

---

### Post by ubername on 2010-04-13
I have noticed something else:

you have a /grub/grub.cfg on sda1, which is a windows partition - that is very odd and suggests that your install of grub2 went awry. I think your best approach would be to boot into ubuntu, un-install both grub and grub2 then reinstall grub2. When you reinstall grub2 make sure that you select to install it to the MBR of sda - Do not select a partition (i.e. sda1, sda5)

---

### Post by WitchCraft on 2010-04-13
If you use grub2 and not grub, you must use menu.cfg.
PS: you have a sda5, so there are min. 5 numbers to try, not 3.

---

### Post by ubername on 2010-04-13
I have noticed another thing:

You have single quotes in 
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set eec8aa36c8a9fd49
chainloader +1

I think it should be

set root=(hd0,1)

i.e. no quotes.Try that.

I also think hd0,1 is correct for windows being on the first partition of you first hd. I have the same setup.

BTW Witchcraft: it's grub.cfg not menu.cfg, and due to the way extended partitions are numbered there are not necessarily 'min. 5 numbers to try'

---

### Post by Usksider on 2010-04-13
> **ubername said:**
> Edit - see my last post  -- remove quotes from *set root='(hd0,1)'*

Hi

I notice something which might help:

You have both a menu.lst and a grub.cfg on sda5 /boot/grub.

I thought that Grub2 (which is the replacement for legacy grub) only uses grub.cfg. However I note that  the section

```
=================== sda5: Location of files loaded by Grub: ===================

381.5GB: boot/grub/core.img
381.4GB: boot/grub/grub.cfg
278.6GB: boot/grub/menu.lst

```mentions menu.lst, so it is not as simple as it seems.

However, what you have been doing (editing the entry from the 'splash screen' (not technically it's proper name - I think it is called the grub menu, but I know what you mean!)) is the right thing. I am sure that you have been amending the grub.cfg entry because legacy grub did not use the 'ctrl-x' to boot approach.

Do you get any error messages when you select the entry "Windows 7 (loader) (on /dev/sda1)" from the menu? It would be useful to know exactly what happens when you select this option (Don't edit it - just select it from the grub menu)

I would suggest renaming the menu.lst file as a first step to make sure that it is not part of the problem

e.g.

```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.old
```

Also, go into synaptic package manager and find 'grub' and 'grub2'. If they are both installed, mark 'grub' for complete removal. Then run
```
sudo update-grub
```Let us know how you get on.

Hi Ubername,

Grub menu screen... yes, that makes much more sense than 'splash' screen doesn't it? 

Selecting Windows 7 from the menu produces a blank screen with a flashing cursor at top left... no error message. I'd assumed Lucid had broken the Windows MBR somehow, so used the Win 7 DVD to try rebuilding the bootrec, mbr, etc. but that didn't help.

I've renamed the menu.lst as you suggest, but that hasn't helped either.

---

### Post by Usksider on 2010-04-13
> **ubername said:**
> I have noticed another thing:

You have single quotes in 
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set eec8aa36c8a9fd49
chainloader +1

I think it should be

set root=(hd0,1)

i.e. no quotes.Try that.

I also think hd0,1 is correct for windows being on the first partition of you first hd. I have the same setup.

BTW Witchcraft: it's grub.cfg not menu.cfg, and due to the way extended partitions are numbered there are not necessarily 'min. 5 numbers to try'

I'm about to show my stupidity here... how do I go about editing the grub.cfg file? I thought was supposed to be a no-go area? I guess I'm wrong about that.

---

### Post by ubername on 2010-04-13
Sorry - I meant you should try removing the quotes using 'e' and 'ctl-x' from the grub menu.

ALthough you can edit grub.cfg it would be much better to get it so that update-grub does the job. The fact that there are quotes there makes me think you have ended up with a dodgy package (poss. update-grub) so a remove / re-install of grub2 seems the way to go.

---

### Post by Usksider on 2010-04-13
> **ubername said:**
> I have noticed something else:

you have a /grub/grub.cfg on sda1, which is a windows partition - that is very odd and suggests that your install of grub2 went awry. I think your best approach would be to boot into ubuntu, un-install both grub and grub2 then reinstall grub2. When you reinstall grub2 make sure that you select to install it to the MBR of sda - Do not select a partition (i.e. sda1, sda5)

Done as suggested - no change.

---

### Post by Usksider on 2010-04-13
> **ubername said:**
> Sorry - I meant you should try removing the quotes using 'e' and 'ctl-x' from the grub menu.

ALthough you can edit grub.cfg it would be much better to get it so that update-grub does the job. The fact that there are quotes there makes me think you have ended up with a dodgy package (poss. update-grub) so a remove / re-install of grub2 seems the way to go.

Okay... Tried this too, but also no change. :(

---

### Post by ubername on 2010-04-13
Hmm. I was really hoping removing the quotes would do it. 

The fact that you are getting a blank screen with a flashing cursor when you select the Windows option seems to indicate that grub2 thinks it has successfully passed control to the Windows boot loader. When grub doesn't like the partition or the files located on the partition it has a range of error messages to indicate something is wrong.

Out of interest, when you reinstalled grub2 did it ask you where to install grub?

Have you tried booting from the 'recovery' ubuntu option and selecting the 'rebuild grub' option from there?

I'm afraid I don't know enough about Windows booting to help much beyond this - there may be some windows log files on your windows partition if the booting is getting far enough into Windows to log any errors there.

---

### Post by kansasnoob on 2010-04-13
OK first a quick review of what we have. Win7 is on sda1 and Lucid is on sda5.

The following indicates a problem with mixed legacy grub and grub2 files/directories:

```
sda5: __________________________________________________ _______________________

File system: ext2
Boot sector type: Grub
Boot sector info: Grub is installed in the boot sector of sda5 and looks
at sector 544367254 of the same hard drive for the
stage2 file, but no stage2 files can be found at this
location.
Operating System: Ubuntu lucid (development
branch)
Boot files/dirs: /boot/grub/**menu.lst** /boot/grub/**grub.cfg** /etc/fstab
/grub/core.img /boot/grub/core.img
```

However you've already made some changes so we'll get to that later.

Please read this all before beginning, and **you must have an Ubuntu Live CD!** It need not be Lucid, but you'll need a known working Ubuntu Live CD!

What I'd like you to do is restore a Windows "readable" mbr to /dev/sda and see if Win7 will boot then. Of course that will leave you unable to boot Lucid so I'll include instructions for restoring grub2 to the mbr also.

Of course if Windows won't boot after using Lilo to create a Windows readable mbr then we know we have other issues to deal with, and I'll include links to some info regarding that.

I would first like you to post some information from the command line while you're booted into your installed Lucid, so that's **step #1.** Post the output of (please use code tags):

```
grub-install -v && aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
```

```
ls /boot/grub
```

You need not wait for my reply before continuing with **step #2** where we'll use Lilo to create a Windows readable mbr. From Lucid run:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

Then just to be sure Lilo doesn't mess with the grub2 config at some point:

```
sudo apt-get remove lilo
```

Then just reboot and see if Windows will boot. If it does you can skip on to restoring the grub2 mbr and we'll then have to deal with getting grub2 starightened out :)

If Windows will not boot we know that it has problems :( So look at the following links for info on how to fix it:

[http://ubuntuforums.org/showpost.php?p=8929988&postcount=357](http://ubuntuforums.org/showpost.php?p=8929988&postcount=357)

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392) (this is really identical to the first link, just the MS version)

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If none of that get's Windows to boot with the Lilo mbr I'm stumped :confused:

But regardless you'll need to know how **to restore the grub2 mbr.** Using the Ubuntu Live CD run:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sda
```

If that shows any errors then:

```
grub-install --recheck /dev/sda
```

Then just exit and unmount:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Then you should be able to boot Lucid. So be sure and post the requested info and whether or not you got Windows booting with the Lilo mbr.

---

### Post by Usksider on 2010-04-13
> **ubername said:**
> Hmm. I was really hoping removing the quotes would do it. 

The fact that you are getting a blank screen with a flashing cursor when you select the Windows option seems to indicate that grub2 thinks it has successfully passed control to the Windows boot loader. When grub doesn't like the partition or the files located on the partition it has a range of error messages to indicate something is wrong.

Out of interest, when you reinstalled grub2 did it ask you where to install grub?

Have you tried booting from the 'recovery' ubuntu option and selecting the 'rebuild grub' option from there?

I'm afraid I don't know enough about Windows booting to help much beyond this - there may be some windows log files on your windows partition if the booting is getting far enough into Windows to log any errors there.

Being kind of new to this I may well have made things worse myself...

I've reinstalled Grub2 a couple of times, using different set-ups I've found on the web. Initially I told Grub2 the bootable partition was SDA05 (the Linux partition) and to install there.

When that didn't work I uninstalled Grub2 and reinstalled telling Grub2 there were bootable partitions at SDA01 and SDA05 (as indicated in a Grub tutorial) so installed on both.

That didn't work either despite repairing Windows bootrec, etc.

On this occasion when I reinstalled Grub2 I just told it install on SDA0 as you suggested.

I've tried rebuilding Grub from recovery previously without success, but will give it another go. When I tried before it wanted to chainload and came up with Error 11?

I'm thinking I may need to reinstall Windows 7 - I wouldn't bother if I could get a Linux version of Photoshop, but that seems like a dreamworld away at present. 

Thanks for all your help here - at least I'm learning about some Linux stuff, which is no bad thing. :cool:

---

### Post by cheapsaket on 2010-04-13
photoshop on linux/wine
[http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)

---

### Post by ubername on 2010-04-13
Usksider - sounds like you were almost there. Chainloading is good - that's how grub passes control to the windows 'booter'

Error 11 is an unrecognised device string (I think - I'll google some more - that was from my first hit) which I reckon has to do with the 'set root=...' line (I have lost faith in my hunch about the quotes by the way - I've just seen another post with quotes around the (hd0,1) part)

That said, if you are game for a rebuild, then Windows 7 first followed by Ubuntu is certainly the best way of getting to a clean set up

Just one more thought. You say you installed to sda0. If I recall, the install options ask for either the device itself (e.g. sda) or a partition on the device (e.g. sda1). I believe you should avoid anything with a number in it - i.e. select sda, NOT sda*n*. But perhaps you mis-typed.

---

### Post by alexsimps on 2010-04-13
I had the same problem yesterday with my vista boot loader and finally solved it. (as documented here [http://georgia.ubuntuforums.org/showthread.php?p=9107237](http://georgia.ubuntuforums.org/showthread.php?p=9107237)). Its maybe not the cleanest method but it seems simple enough(to me).  First i reinstalled my vista boot-loader which im pretty sure is roughly equivalent to a win 7 boot-loader. Then i reinstalled grub from my installed version of Ubuntu thanks to supergrubdisk live CD.
I im not sure what state your computer is in now but maybe it would be best to start from the start.

_*Materials:*_
I assume you have your win 7 Disk? 
Also obtain the newest version of the live CD of [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)  and burn.

Total= 2 Disks

_*Ok go....*_
(This first part is a slightly cleaned version of [http://georgia.ubuntuforums.org/showthread.php?p=9107237](http://georgia.ubuntuforums.org/showthread.php?p=9107237) Mostly quoted from someone with the handle of [tturrisi]("http://ubuntuforums.org/member.php?u=123008").)
 "
1.Put the Windows Vista/Win7 installation disc in the disc drive, and then  start the computer.
2.Press a key when you are prompted.
3.Select a language, a time, a currency, a keyboard or an input method,  and then click Next.
4.Click Repair your computer.
5.Click the operating system that you want to repair, and then click  Next. (if no Vista/(win7?) operating system is listed, click Next anyway)
6.In the System Recovery Options dialog box, click Command Prompt.
_Next:_
At the command prompt, type **diskpart**.
This will get you to the DiskPart prompt, which allows you to use a  variety of hard disk partitioning and formatting tools similar to FDISK  in older versions of Windows.
At the DiskPart prompt, type **list disk** to see all of your disks then **select disk #** where the # sign is  the number of the hard disk drive with Vista installed on it. If your  Vista drive is the only hard drive in your computer, it is Disk 0.
Then type **list partition**, Select the partition by typing **select partition #** where the #  sign is the partition that has Vista installed on it.
Type **active **and press ENTER. The Vista partition is now active.  Finally, type 'exit' to close DiskPart. 
_Now:_ 
Reboot the computer using the  Vista/Win7 disk and follow* steps 1-6 above.*  You can now repair the Vista  boot.
To fix the Master Boot Record enter:
[B]bootrec /fixmbr
[/B]followed by
[B] bootrec /rebuildbcd
[/B]followed by
** bootrec /fixboot**
If you get any errors here don't worry i got some when i did **bootrec /rebuildbcd **if i remember and it still worked.
Restart remove live cd and hope for best
"
Now your back to the win7 boot loader i would hope?
Next test it out i guess(boot win7 up).
_*Now to get the grub boot loader back:*_
The grub2 boot loader to be exact (not knowing this messed me up for a little bit). Restart using the supergrubdisk live cd, it will find your old grub menu and allow you to boot from it (its pretty intuitive).
Select your Ubuntu OS.
*Stopping here and updating everything would not likely hurt anything even if you have to restart as you can just use the live cd to get back.
Then once logged in open up the terminal, then type.
**sudo grub-install /dev/sda **(this installs grub to the first hard drive and to what it finds to be the active partition i believe; which will be the vista/win7 that you marked active in the first part).
(As gleaned from [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html))
After this successfully completes restart without the live cd an all should be good, at least it was for me.

[I]Good luck let us know how it goes.
[/I]Time to stop procrastinating and study...

---

### Post by Usksider on 2010-04-13
> **kansasnoob said:**
> OK first a quick review of what we have. Win7 is on sda1 and Lucid is on sda5.

The following indicates a problem with mixed legacy grub and grub2 files/directories:

```
sda5: __________________________________________________ _______________________

File system: ext2
Boot sector type: Grub
Boot sector info: Grub is installed in the boot sector of sda5 and looks
at sector 544367254 of the same hard drive for the
stage2 file, but no stage2 files can be found at this
location.
Operating System: Ubuntu lucid (development
branch)
Boot files/dirs: /boot/grub/**menu.lst** /boot/grub/**grub.cfg** /etc/fstab
/grub/core.img /boot/grub/core.img
```However you've already made some changes so we'll get to that later.

Please read this all before beginning, and **you must have an Ubuntu Live CD!** It need not be Lucid, but you'll need a known working Ubuntu Live CD!

What I'd like you to do is restore a Windows "readable" mbr to /dev/sda and see if Win7 will boot then. Of course that will leave you unable to boot Lucid so I'll include instructions for restoring grub2 to the mbr also.

Of course if Windows won't boot after using Lilo to create a Windows readable mbr then we know we have other issues to deal with, and I'll include links to some info regarding that.

I would first like you to post some information from the command line while you're booted into your installed Lucid, so that's **step #1.** Post the output of (please use code tags):

```
grub-install -v && aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
``````
ls /boot/grub
```You need not wait for my reply before continuing with **step #2** where we'll use Lilo to create a Windows readable mbr. From Lucid run:

```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```Then just to be sure Lilo doesn't mess with the grub2 config at some point:

```
sudo apt-get remove lilo
```Then just reboot and see if Windows will boot. If it does you can skip on to restoring the grub2 mbr and we'll then have to deal with getting grub2 starightened out :)

If Windows will not boot we know that it has problems :( So look at the following links for info on how to fix it:

[http://ubuntuforums.org/showpost.php?p=8929988&postcount=357](http://ubuntuforums.org/showpost.php?p=8929988&postcount=357)

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392) (this is really identical to the first link, just the MS version)

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If none of that get's Windows to boot with the Lilo mbr I'm stumped :confused:

But regardless you'll need to know how **to restore the grub2 mbr.** Using the Ubuntu Live CD run:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
``````
grub-install /dev/sda
```If that shows any errors then:

```
grub-install --recheck /dev/sda
```Then just exit and unmount:

```
exit
``````
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```Then you should be able to boot Lucid. So be sure and post the requested info and whether or not you got Windows booting with the Lilo mbr.

Hi there...

Here's the dump you asked for:

usky@usky-mesh:~$ grub-install -v && aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
grub-install (GNU GRUB 1.98-1ubuntu4)
Package: grub
State: not installed
Version: 0.97-29ubuntu60
Priority: optional
Package: grub-pc
State: installed
Automatically installed: yes
Version: 1.98-1ubuntu4
Package: grub-common
State: installed
Automatically installed: yes
Version: 1.98-1ubuntu4
Package: os-prober
State: installed
Automatically installed: yes
Version: 1.36
usky@usky-mesh:~$ 
usky@usky-mesh:~$ ls /boot/grub
050817-N-3488C-028.tga                  Lake_mapourika_NZ.tga
2006-02-15_Piping.tga                   linux16.mod
915resolution.mod                       linux.mod
acpi.mod                                lnxboot.img
Aesculus_hippocastanum_fruit.tga        load.cfg
affs.mod                                loadenv.mod
afs_be.mod                              locale
afs.mod                                 loopback.mod
aout.mod                                lsmmap.mod
Apollo_17_The_Last_Moon_Shot_Edit1.tga  ls.mod
ata.mod                                 lspci.mod
ata_pthru.mod                           lvm.mod
at_keyboard.mod                         mdraid.mod
B-1B_over_the_pacific_ocean.tga         memdisk.mod
befs_be.mod                             memrw.mod
befs.mod                                menu.lst~
biosdisk.mod                            menu.lst_backup_by_grub2_prerm
bitmap.mod                              menu.lst.old
bitmap_scale.mod                        minicmd.mod
blocklist.mod                           minix.mod
BonsaiTridentMaple.tga                  minix_stage1_5
boot.img                                mmap.mod
boot.mod                                moddep.lst
bsd.mod                                 Moraine_Lake_17092005.tga
bufio.mod                               msdospart.mod
cat.mod                                 multiboot2.mod
cdboot.img                              multiboot.mod
chain.mod                               normal.mod
charset.mod                             ntfscomp.mod
cmp.mod                                 ntfs.mod
command.lst                             ohci.mod
configfile.mod                          part_acorn.mod
core.img                                part_amiga.mod
cpio.mod                                part_apple.mod
cpuid.mod                               part_gpt.mod
crc.mod                                 partmap.lst
crypto.lst                              part_msdos.mod
crypto.mod                              part_sun.mod
datehook.mod                            parttool.lst
date.mod                                parttool.mod
datetime.mod                            password.mod
default                                 password_pbkdf2.mod
diskboot.img                            pbkdf2.mod
dm_nv.mod                               pci.mod
drivemap.mod                            Plasma-lamp.tga
e2fs_stage1_5                           play.mod
echo.mod                                png.mod
efiemu32.o                              probe.mod
efiemu64.o                              pxeboot.img
efiemu.mod                              pxecmd.mod
elf.mod                                 pxe.mod
example_functional_test.mod             raid5rec.mod
ext2.mod                                raid6rec.mod
extcmd.mod                              raid.mod
fat.mod                                 read.mod
fat_stage1_5                            reboot.mod
Flower_jtca001.tga                      reiserfs.mod
Fly-Angel.tga                           reiserfs_stage1_5
font.mod                                relocator.mod
fshelp.mod                              scsi.mod
fs.lst                                  search_fs_file.mod
functional_test.mod                     search_fs_uuid.mod
gcry_arcfour.mod                        search_label.mod
gcry_blowfish.mod                       search.mod
gcry_camellia.mod                       serial.mod
gcry_cast5.mod                          setjmp.mod
gcry_crc.mod                            setpci.mod
gcry_des.mod                            sfs.mod
gcry_md4.mod                            sh.mod
gcry_md5.mod                            sleep.mod
gcry_rfc2268.mod                        Sparkler.tga
gcry_rijndael.mod                       stage1
gcry_rmd160.mod                         stage2
gcry_seed.mod                           tar.mod
gcry_serpent.mod                        terminal.lst
gcry_sha1.mod                           terminal.mod
gcry_sha256.mod                         terminfo.mod
gcry_sha512.mod                         test.mod
gcry_tiger.mod                          tga.mod
gcry_twofish.mod                        trig.mod
gcry_whirlpool.mod                      true.mod
gettext.mod                             TulipStair_QueensHouse_Greenwich.tga
gfxmenu.mod                             udf.mod
gfxterm.mod                             ufs1.mod
Glasses_800_edit.tga                    ufs2.mod
gptsync.mod                             uhci.mod
grldr.img                               unicode.pf2
grub.cfg                                usb_keyboard.mod
grubenv                                 usb.mod
gzio.mod                                usbms.mod
halt.mod                                usbtest.mod
handler.lst                             vbeinfo.mod
handler.mod                             vbe.mod
hashsum.mod                             vbetest.mod
hdparm.mod                              vga.mod
hello.mod                               vga_text.mod
help.mod                                video_fb.mod
hexdump.mod                             video.lst
hfs.mod                                 video.mod
hfsplus.mod                             videotest.mod
Hortensia-1.tga                         Windbuchencom.tga
installed-version                       xfs.mod
iso9660.mod                             xfs_stage1_5
jfs.mod                                 xnu.mod
jfs_stage1_5                            xnu_uuid.mod
jpeg.mod                                zfsinfo.mod
kernel.img                              zfs.mod
keystatus.mod
usky@usky-mesh:~$ 

...and no, Windows still won't boot even after using lilo to create a new mbr. :(

---

### Post by Usksider on 2010-04-13
> **alexsimps said:**
> I had the same problem yesterday with my vista boot loader and finally solved it. (as documented here [http://georgia.ubuntuforums.org/showthread.php?p=9107237](http://georgia.ubuntuforums.org/showthread.php?p=9107237)). Its maybe not the cleanest method but it seems simple enough(to me).  First i reinstalled my vista boot-loader which im pretty sure is roughly equivalent to a win 7 boot-loader. Then i reinstalled grub from my installed version of Ubuntu thanks to supergrubdisk live CD.
I im not sure what state your computer is in now but maybe it would be best to start from the start.

After this successfully completes restart without the live cd an all should be good, at least it was for me.

[I]Good luck let us know how it goes.
[/I]Time to stop procrastinating and study...

Hi Alex

Tried all of this previously without any joy - everything tells me my Windows partition is good and all is otherwise okay, but I cannot get Windows to boot at all. :(

I've learned a huge amount about what works and what doesn't over the last couple of days, so all the time devoted is most certainly not wasted. :)

---

### Post by Usksider on 2010-04-13
> **cheapsaket said:**
> photoshop on linux/wine
[http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)

Excellent! Thank you so much... 

Looks like Windows 7 may be heading for the waste basket.... :lolflag:

---

### Post by Usksider on 2010-04-13
> **ubername said:**
> Usksider - sounds like you were almost there. Chainloading is good - that's how grub passes control to the windows 'booter'

Error 11 is an unrecognised device string (I think - I'll google some more - that was from my first hit) which I reckon has to do with the 'set root=...' line (I have lost faith in my hunch about the quotes by the way - I've just seen another post with quotes around the (hd0,1) part)

That said, if you are game for a rebuild, then Windows 7 first followed by Ubuntu is certainly the best way of getting to a clean set up

Just one more thought. You say you installed to sda0. If I recall, the install options ask for either the device itself (e.g. sda) or a partition on the device (e.g. sda1). I believe you should avoid anything with a number in it - i.e. select sda, NOT sda*n*. But perhaps you mis-typed.

My error Ubername... SDA, not SDA0

I have no idea now how I got to the stage where Grub was trying to chainload and the option appeared in the menu - this much for sure, I can't get back there now. My boot menu looks completely 'normal' now.

---

