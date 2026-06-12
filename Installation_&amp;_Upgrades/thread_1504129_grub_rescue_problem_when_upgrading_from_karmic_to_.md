---
title: "grub rescue problem when upgrading from karmic to lucid"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by jolyont on 2010-06-07
Hi Folks, 
I had a nicely working karmic 64bit/windows XP install, but the "upgrade" button to 10.04 has finally got the better of me.  Now, when the PC boots up, the following failure occurs:
Memory Check
PCI device listing
Verifying DMI Pool Data .............
error: no such device:e9eb88c2-67f2-47a7-bf9d-50b77b2d3480
grub rescue>_

Some more information.  
linux is on sdb1

when I type "ls" I get: "(hd0)  (hd1) (fd0)"
however, I've not managed to get "ls (hd1,1)" or similar to do anything, the best I get is "error: no such partition".

the command "find /boot/grub/grub.conf" results in the error "Unknown command 'find'"

I've tried swapping the boot order in the bios from hd0 to hd1 but that has made no difference.

There is no grub loader, no linux, no windows, no operating system of anykind, just the "grub rescue>" prompt.

help!

---

### Post by PPrincipeza on 2010-06-07
Hello.

Try to run the following command from the GRUB menu:

```
grub> find /boot/grub/grub.conf
```The output should bring a (hd1,X), where X stands for the partition where GRUB has been found. If that's the case, you might boot the partition with:

```
grub> configfile (hd1,X)/boot/grub/grub.conf
```If you're able to boot Ubuntu, you may need to run /sbin/grub-install as root (or using sudo). Check the manpages of grub-install for further info on re-configuring GRUB.

HTH.
--
PPrincipeza

---

### Post by kansasnoob on 2010-06-07
> **jolyont said:**
> Hi Folks, 
I had a nicely working karmic/windows XP install, but the "upgrade" button to 10.04 has finally got the better of me.
Now, when the PC boots up, I get as far as:
"error: no such device :e9eb88c2 etc etc etc
grub rescue>"

linux is on sdb1
when I type ls I get:
(hd0)  (hd1) (fd0)
however, I've not managed to get ls (hd1,1) or similar to do anything, the best I get is "error: no such partition".

I've tried swapping the boot order in the bios from hd0 to hd1 but that has made no difference.

help!

Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kansasnoob on 2010-06-07
> **PPrincipeza said:**
> Hello.

Try to run the following command from the GRUB menu:

```
grub> find /boot/grub/grub.conf
```The output should bring a (hd1,X), where X stands for the partition where GRUB has been found. If that's the case, you might boot the partition with:

```
grub> configfile (hd1,X)/boot/grub/grub.conf
```If you're able to boot Ubuntu, you may need to run /sbin/grub-install as root (or using sudo). Check the manpages of grub-install for further info on re-configuring GRUB.

HTH.
--
PPrincipeza

What "/boot/grub/grub.conf"?

No such file exists in Debian or Ubuntu's grub 2 AFAIK :confused:

---

### Post by PPrincipeza on 2010-06-07
Sorry, I was thinking Fedora/Red Hat when I wrote the thing.

It'd be /boot/grub/stage1 or /boot/grub/menu.lst instead of /boot/grub/grub.conf in Ubuntu, I guess.

--
PPrincipeza

---

### Post by kansasnoob on 2010-06-08
> **PPrincipeza said:**
> Sorry, I was thinking Fedora/Red Hat when I wrote the thing.

It'd be /boot/grub/stage1 or /boot/grub/menu.lst instead of /boot/grub/grub.conf in Ubuntu, I guess.

--
PPrincipeza

Actually, no. That error is probably related to something like this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

But I'd really need to see the output requested to properly troubleshoot it.

---

### Post by jolyont on 2010-06-09
I can't get into linux to get myself a terminal window to get the output from the Boot info script.  

The problem is getting past the "grub rescue >_" prompt.

I get that horrible feeling that I'm doing a clean install from a bootable CD/ USB stick.  :-(

---

### Post by efflandt on 2010-06-09
Download and run the boot info script from an Ubuntu CD, or put the script and its output on USB memory.

---

### Post by spaceface3122 on 2010-06-11
I'm having the same problem as the guy who started the thread.  Here is the output that I get when running the bootscript.  I think what happened was I went with the recommended setting when asked by the installer where to put grub.  After thinking about it I think the recommendation was to put it on all the sda and sdb partitions.  My fault for not reading anything about the upgrade problems.  

However no one has really answered the question of what I do now after I have this information.  Do I need to mount?  Honestly I have no important information on Ubuntu I just want to get windows working right again.  SO in other words if there is a way to just uninstall or downgrade back to 9.10 easily I'm fine with that.

Thanks




```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 11190104 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 11197120 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 11204128 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 11189496 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb5 and 
                       looks at sector 11330440 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf5b4f5b4

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,414,019   268,413,957   7 HPFS/NTFS
/dev/sda2         268,414,020   411,778,079   143,364,060   7 HPFS/NTFS
/dev/sda3         411,778,080   488,392,064    76,613,985   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8ac7f727

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048 1,722,682,079 1,722,680,032   7 HPFS/NTFS
/dev/sdb2       1,722,682,080 1,953,520,064   230,837,985   5 Extended
/dev/sdb5       1,722,682,143 1,944,057,779   221,375,637  83 Linux
/dev/sdb6       1,944,057,843 1,953,520,064     9,462,222  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       e844ab77-8883-48b3-a0cb-151c9d218a4a   ext4                                     
/dev/sda1        6E8CC5BA8CC57CD9                       ntfs       C drive on XP                 
/dev/sda2        9A30874830872A79                       ntfs       D Drive on XP                 
/dev/sda3        5C748E47748E23BC                       ntfs       New Volume                    
/dev/sdb1        FC9ED7DB9ED78C90                       ntfs                                     
/dev/sdb5        19b199fb-d3d5-4cf6-8566-e713250b0fe1   ext4                                     
/dev/sdb6        b6df60fa-bc9d-46d3-ae39-788c547cfdc4   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTIN 

======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 6e8cc5ba8cc57cd9
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 6e8cc5ba8cc57cd9
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6e8cc5ba8cc57cd9
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6e8cc5ba8cc57cd9
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6e8cc5ba8cc57cd9
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6e8cc5ba8cc57cd9
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-19-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 6e8cc5ba8cc57cd9
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set fc9ed7db9ed78c90
    chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic-pae (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 19b199fb-d3d5-4cf6-8566-e713250b0fe1
    linux /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=19b199fb-d3d5-4cf6-8566-e713250b0fe1 ro quiet splash
    initrd /boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic-pae (recovery mode) (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 19b199fb-d3d5-4cf6-8566-e713250b0fe1
    linux /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=19b199fb-d3d5-4cf6-8566-e713250b0fe1 ro single
    initrd /boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Chainload into GRUB 2 (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 19b199fb-d3d5-4cf6-8566-e713250b0fe1
    linux /boot/grub/core.img 
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 19b199fb-d3d5-4cf6-8566-e713250b0fe1
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


   5.8GB: boot/grub/core.img
   5.7GB: boot/grub/grub.cfg
   4.9GB: boot/initrd.img-2.6.31-19-generic
   5.8GB: boot/initrd.img-2.6.32-22-generic
   3.9GB: boot/vmlinuz-2.6.31-19-generic
   1.0GB: boot/vmlinuz-2.6.32-22-generic
   5.8GB: initrd.img
   4.9GB: initrd.img.old
   1.0GB: vmlinuz
   3.9GB: vmlinuz.old

=========================== sdb5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

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
# kopt=root=UUID=19b199fb-d3d5-4cf6-8566-e713250b0fe1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=19b199fb-d3d5-4cf6-8566-e713250b0fe1

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

title        Ubuntu 9.10, kernel 2.6.31-15-generic-pae
uuid        19b199fb-d3d5-4cf6-8566-e713250b0fe1
kernel        /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=19b199fb-d3d5-4cf6-8566-e713250b0fe1 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic-pae

title        Ubuntu 9.10, kernel 2.6.31-15-generic-pae (recovery mode)
uuid        19b199fb-d3d5-4cf6-8566-e713250b0fe1
kernel        /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=19b199fb-d3d5-4cf6-8566-e713250b0fe1 ro  single
initrd        /boot/initrd.img-2.6.31-15-generic-pae

title        Chainload into GRUB 2
root        19b199fb-d3d5-4cf6-8566-e713250b0fe1
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        19b199fb-d3d5-4cf6-8566-e713250b0fe1
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root=(hd1,5)
search --no-floppy --fs-uuid --set 19b199fb-d3d5-4cf6-8566-e713250b0fe1
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
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 19b199fb-d3d5-4cf6-8566-e713250b0fe1
    linux    /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=19b199fb-d3d5-4cf6-8566-e713250b0fe1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 19b199fb-d3d5-4cf6-8566-e713250b0fe1
    linux    /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=19b199fb-d3d5-4cf6-8566-e713250b0fe1 ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6e8cc5ba8cc57cd9
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set fc9ed7db9ed78c90
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=19b199fb-d3d5-4cf6-8566-e713250b0fe1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=b6df60fa-bc9d-46d3-ae39-788c547cfdc4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 885.4GB: boot/grub/core.img
 885.4GB: boot/grub/grub.cfg
 897.1GB: boot/grub/menu.lst
 882.8GB: boot/initrd.img-2.6.31-15-generic-pae
 882.5GB: boot/vmlinuz-2.6.31-15-generic-pae
 882.8GB: initrd.img
 882.5GB: vmlinuz
```

---

### Post by bcbc on 2010-06-11
> **spaceface3122 said:**
> I'm having the same problem as the guy who started the thread.  Here is the output that I get when running the bootscript.  I think what happened was I went with the recommended setting when asked by the installer where to put grub.  After thinking about it I think the recommendation was to put it on all the sda and sdb partitions.  My fault for not reading anything about the upgrade problems.  

However no one has really answered the question of what I do now after I have this information.  Do I need to mount?  Honestly I have no important information on Ubuntu I just want to get windows working right again.  SO in other words if there is a way to just uninstall or downgrade back to 9.10 easily I'm fine with that.

Thanks

You need to install and run testdisk and copy over the backup bootsector over each windows partition that you installed grub2 to. Try each ntfs partition and if it says the backup is different then repace the bootsector with it. You'll need an ubuntu install cd that you can run in live mode (try without and changes).
This link describes what to do - use testdisk - it is the best method. If you try and repair it yourself you may overwrite the backup boot sector. Only if testdisk fails, use the traditional windows repair method as this has been known to fail for reasons unknown.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Then, you need to install the windows bootloader to the hard drive MBRs. You can do this with any windows disk, or you can do it from a live cd as well. (lilo used in this way is equivalent to the windows bootloader - it boots partition marked active - I've done this on my own computer, you'll get a few warnings when you install it that you can ignore)

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
sudo lilo -M /dev/sdb mbr
```Your wubi will probably still work, after repairs, but I don't blame you if you want to uninstall it after this and go back to 9.10

If you are unsure about any steps above, check back here. If you do something different you may make it worse.

---

### Post by spaceface3122 on 2010-06-11
It won't let me install testdisk for some reason in the "try ubuntu without changes" boot.  Any suggestions?  I tried to repair from my Vista 64 ultimate disc.  It originally found a problem with my booting and "fixed" it but I still couldn't boot from the hard drive.  I also restored my C drive windows partition to early yesterday morning.  That didn't do anything either I ran the boot script again and it was saying the same things as before.

Should I make a disc with 10.04 installed and try fixing/updating anything with that.  Or will it not matter?



```
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$ sudo testdisk
sudo: testdisk: command not found
ubuntu@ubuntu:~$ 


```

---

### Post by bcbc on 2010-06-11
> **spaceface3122 said:**
> It won't let me install testdisk for some reason in the "try ubuntu without changes" boot.  Any suggestions?  I tried to repair from my Vista 64 ultimate disc.  It originally found a problem with my booting and "fixed" it but I still couldn't boot from the hard drive.  I also restored my C drive windows partition to early yesterday morning.  That didn't do anything either I ran the boot script again and it was saying the same things as before.

Should I make a disc with 10.04 installed and try fixing/updating anything with that.  Or will it not matter?



```
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$ sudo testdisk
sudo: testdisk: command not found
ubuntu@ubuntu:~$ 


```
Sorry meant to say you need to enable the universe repository. Click on System, Administration, Software sources
Then on the first tab check the second entry (Community maintained... (universe))

EDIT: PS in response to your other comments, any time you try various other fixes, it makes it more difficult (for us to help). e.g. you tried the windows fix and it failed, but what did it do to your backup bootsector? If it overwrote it in the process, then you might have a bigger problem on your hands.

---

### Post by spaceface3122 on 2010-06-12
Followed the directions given and I am booting into Windows right now.  Thanks a lot bcbc I let you know if there are any other problems but as of right now everything looks good ...Thanks again.

---

### Post by bcbc on 2010-06-12
> **spaceface3122 said:**
> Followed the directions given and I am booting into Windows right now.  Thanks a lot bcbc I let you know if there are any other problems but as of right now everything looks good ...Thanks again.

Great, you're welcome :)

---

### Post by Clydeuk on 2010-07-03
Ok, I have problems also. After several failed attempts at chainloading Kubuntu 10.04 from NTLDR I currently have a system that will not boot. I finally installed GRUB2 to the MBR of the first hard drive (/dev/sda), now all I get is a grub rescue prompt. Nothing I try here works. Easy fix to get XP back I know, just FixMbr etc.
 
Now, if I boot from the second hard drive by changing the BIOS settings, I get Grub2 and Kubuntu, the listing is also there for XP. So, my previous installation of Grub on the MBR of /dev/sdb is still working. I could not however successfully chain load this from NTLDR when that was working fine, despite doing all the "dd if=" etc. It created my file ok, the file contained what looked like a boot sector (i.e. not all zero's) but I was either left with a flashing cursor, or a grub rescue prompt.
 
Here is my output from the Boot Infor Script....it is quite long, bear in mind I was running a Live CD to get this, I also had a flash drive connected and without realising it was already mounted, mounted it again, so there are a few duplicate entries. The first part about drive sda can be more or less ignored, as this is where the broken Grub loader resides, and will be gone after I replace the MBR. However the sdb entries are giving me a working Linux, so surely there must be a way to get this MBR into a file that NTLDR can handle.
 
-------
 
                Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /grub.
 => Syslinux is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub 2 in the file /ubuntu.lnx looks at sector 1 of 
                       the same hard drive for core.img, but core.img can not 
                       be found at this location.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
sdb1: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sdb2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sdb5: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sdc1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sda1    *             63    78,140,159    78,140,097   7 HPFS/NTFS

Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sdb1               2,048    33,202,175    33,200,128  83 Linux
/dev/sdb2          33,204,222    35,155,967     1,951,746   5 Extended
/dev/sdb5          33,204,224    35,155,967     1,951,744  82 Linux swap / Solaris

Drive: sdc ___________________ _____________________________________________________
Disk /dev/sdc: 4007 MB, 4007657472 bytes
5 heads, 32 sectors/track, 48921 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sdc1    *          8,064     7,827,455     7,819,392   b W95 FAT32

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/loop0                                              squashfs                                 
/dev/sda1        620417D70417AD53                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1acdcc88-3416-4781-b214-8fa3f897db3b   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        555f3168-80b3-416f-ac9f-8cf5eb5de3bb   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        F63F-A69A                              vfat                                     
/dev/sdc: PTTYPE="dos" 
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /mnt/linux               ext4       (rw)
/dev/sdc1        /mnt/flash               vfat       (rw)

================================ sda1/boot.ini: ================================
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
C:\ubuntu.lnx="Kubuntu Linux"
=========================== sdb1/boot/grub/grub.cfg: ===========================
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 1acdcc88-3416-4781-b214-8fa3f897db3b
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 1acdcc88-3416-4781-b214-8fa3f897db3b
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd1,1)'
 search --no-floppy --fs-uuid --set 1acdcc88-3416-4781-b214-8fa3f897db3b
 linux /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=1acdcc88-3416-4781-b214-8fa3f897db3b ro   quiet splash
 initrd /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd1,1)'
 search --no-floppy --fs-uuid --set 1acdcc88-3416-4781-b214-8fa3f897db3b
 echo 'Loading Linux 2.6.32-23-generic-pae ...'
 linux /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=1acdcc88-3416-4781-b214-8fa3f897db3b ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.32-23-generic-pae
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod ext2
 set root='(hd1,1)'
 search --no-floppy --fs-uuid --set 1acdcc88-3416-4781-b214-8fa3f897db3b
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod ext2
 set root='(hd1,1)'
 search --no-floppy --fs-uuid --set 1acdcc88-3416-4781-b214-8fa3f897db3b
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
 insmod ntfs
 set root='(hd0,1)'
 search --no-floppy --fs-uuid --set 620417d70417ad53
 drivemap -s (hd0) ${root}
 chainloader +1
}
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
=============================== sdb1/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=555f3168-80b3-416f-ac9f-8cf5eb5de3bb none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
=================== sdb1: Location of files loaded by Grub: ===================

   5.3GB: boot/grub/core.img
   9.1GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.32-23-generic-pae
   5.2GB: boot/vmlinuz-2.6.32-23-generic-pae
    .6GB: initrd.img
   5.2GB: vmlinuz
=========================== sdc1/boot/grub/menu.lst: ===========================
# By default, boot the first entry.
default 0
# Boot automatically after 30 secs.
timeout 30
splashimage=/boot/grub/bt4.xpm.gz
foreground e3e3e3
background 303030
title                Start BackTrack FrameBuffer (1024x768)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x317
initrd                /boot/initrd.gz
title                Start BackTrack FrameBuffer (800x600)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x314
initrd                /boot/initrd800.gz
title                Start BackTrack Forensics (no swap)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317
initrd                /boot/initrdfr.gz
title                Start BackTrack in Safe Graphical Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper xforcevesa rw quiet 
initrd                /boot/initrd.gz
title                Start Persistent Live CD
kernel                /boot/vmlinuz BOOT=casper boot=casper persistent rw quiet 
initrd                /boot/initrd.gz
title                Start BackTrack in Text Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent textonly rw quiet
initrd                /boot/initrd.gz
title                Start BackTrack Graphical Mode from RAM
kernel                /boot/vmlinuz BOOT=casper boot=casper toram nopersistent rw quiet 
initrd                /boot/initrd.gz
title                Memory Test
kernel                /boot/memtest86+.bin
title                Boot the First Hard Disk
root                (hd0)
chainloader +1
=================== sdc1: Location of files loaded by Grub: ===================

    ??GB: boot/grub/menu.lst
    ??GB: boot/initrd800.gz
    ??GB: boot/initrdfr.gz
    ??GB: boot/initrd.gz
    ??GB: boot/vmlinuz
 
----------
 
I'd rather use NTLDR since I am not the only user of this computer and don't want the frighten the other users with an unfamiliar boot screen, I also don't as yet know how to configure Grub2 to my liking, wheras fiddling around with boot.ini is easy to fix if a  mistake is made.

---

### Post by Clydeuk on 2010-07-03
Well blow me down, it looks like after doing that printout I finally have it working, my last reinstall of Kubuntu must have done the trick, as after repairing XP's MBR I can now boot into Kubuntu. Now all I need to do is learn how to adjust Grub2 so that the timeout is lower or non existent. If I set a timeout to 0, will I still be able to access Grub boot options, since the memtest and recovery options that are listed could be useful?

---

