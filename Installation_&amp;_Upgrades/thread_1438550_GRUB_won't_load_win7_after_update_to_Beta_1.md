---
title: "GRUB won't load win7 after update to Beta 1"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by Qvark on 2010-03-25
Hello! Just update ubuntu to beta 1. When I try to load win7 it just all a get is the blinking underscore in the top left corner. What did i do wrong? I tried to search but I am not sure what solutions I should try so if any kind soul would like to help me it would be really appriciated.

Regards
Qvark

>   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    [B]Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 4463423 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.[/B]
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 4463423 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 4465471 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 4465471 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   204,802,047   204,595,200   7 HPFS/NTFS
/dev/sda3         204,802,048   976,771,071   771,969,024   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   964,719,314   964,719,252  83 Linux
/dev/sdb2         964,719,315   976,768,064    12,048,750   5 Extended
/dev/sdb5         964,719,378   976,768,064    12,048,687  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3EDC3DDDDC3D8FDF                       ntfs       System Reserved               
/dev/sda2        0A4846B84846A1F5                       ntfs                                     
/dev/sda3        B6B42B2DB42AEF93                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        375218cc-bfe3-44ae-8d91-2c133f162bbb   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        a681bf90-fd1d-4d9f-b32f-9f7d930fd16b   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/sda1              fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /media/sda3              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /media/sda2              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=375218cc-bfe3-44ae-8d91-2c133f162bbb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=375218cc-bfe3-44ae-8d91-2c133f162bbb

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

title        Ubuntu lucid (development branch), kernel 2.6.32-17-generic
uuid        375218cc-bfe3-44ae-8d91-2c133f162bbb
kernel        /boot/vmlinuz-2.6.32-17-generic root=UUID=375218cc-bfe3-44ae-8d91-2c133f162bbb ro quiet splash 
initrd        /boot/initrd.img-2.6.32-17-generic

title        Ubuntu lucid (development branch), kernel 2.6.32-17-generic (recovery mode)
uuid        375218cc-bfe3-44ae-8d91-2c133f162bbb
kernel        /boot/vmlinuz-2.6.32-17-generic root=UUID=375218cc-bfe3-44ae-8d91-2c133f162bbb ro  single
initrd        /boot/initrd.img-2.6.32-17-generic

title        Ubuntu lucid (development branch), kernel 2.6.31-20-generic
uuid        375218cc-bfe3-44ae-8d91-2c133f162bbb
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=375218cc-bfe3-44ae-8d91-2c133f162bbb ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu lucid (development branch), kernel 2.6.31-20-generic (recovery mode)
uuid        375218cc-bfe3-44ae-8d91-2c133f162bbb
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=375218cc-bfe3-44ae-8d91-2c133f162bbb ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Chainload into GRUB 2
root        375218cc-bfe3-44ae-8d91-2c133f162bbb
kernel        /boot/grub/core.img

title        Ubuntu lucid (development branch), memtest86+
uuid        375218cc-bfe3-44ae-8d91-2c133f162bbb
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

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
search --no-floppy --fs-uuid --set 375218cc-bfe3-44ae-8d91-2c133f162bbb
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
search --no-floppy --fs-uuid --set 375218cc-bfe3-44ae-8d91-2c133f162bbb
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
menuentry "Ubuntu, with Linux 2.6.32-17-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 375218cc-bfe3-44ae-8d91-2c133f162bbb
    linux    /boot/vmlinuz-2.6.32-17-generic root=UUID=375218cc-bfe3-44ae-8d91-2c133f162bbb ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.32-17-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 375218cc-bfe3-44ae-8d91-2c133f162bbb
    echo    Loading Linux 2.6.32-17-generic ...
    linux    /boot/vmlinuz-2.6.32-17-generic root=UUID=375218cc-bfe3-44ae-8d91-2c133f162bbb ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-17-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 375218cc-bfe3-44ae-8d91-2c133f162bbb
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=375218cc-bfe3-44ae-8d91-2c133f162bbb ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 375218cc-bfe3-44ae-8d91-2c133f162bbb
    echo    Loading Linux 2.6.31-20-generic ...
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=375218cc-bfe3-44ae-8d91-2c133f162bbb ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 375218cc-bfe3-44ae-8d91-2c133f162bbb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 375218cc-bfe3-44ae-8d91-2c133f162bbb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3edc3ddddc3d8fdf
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
proc                                       /proc        proc  defaults                    0  0  
# / was on /dev/sdb1 during installation
UUID=375218cc-bfe3-44ae-8d91-2c133f162bbb  /            ext4  errors=remount-ro           0  1  
# swap was on /dev/sdb5 during installation
UUID=a681bf90-fd1d-4d9f-b32f-9f7d930fd16b  none         swap  sw                          0  0  
/dev/sda1                                  /media/sda1  ntfs  nls=iso8859-1,ro,umask=000  0  0  
/dev/sda2                                  /media/sda2  ntfs  nls=iso8859-1,umask=000     0  0  
/dev/sda3                                  /media/sda3  ntfs  nls=iso8859-1,umask=000     0  0  

=================== sdb1: Location of files loaded by Grub: ===================


   2.2GB: boot/grub/core.img
   2.6GB: boot/grub/grub.cfg
   2.2GB: boot/grub/menu.lst
  32.6GB: boot/initrd.img-2.6.31-20-generic
  31.3GB: boot/initrd.img-2.6.32-17-generic
   8.6GB: boot/vmlinuz-2.6.31-20-generic
  32.5GB: boot/vmlinuz-2.6.32-17-generic
  31.3GB: initrd.img
  32.6GB: initrd.img.old
  32.5GB: vmlinuz
   8.6GB: vmlinuz.old

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x98cbc748

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       12749   102297600    7  HPFS/NTFS
/dev/sda3           12749       60802   385984512    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001b61c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60051   482359626   83  Linux
/dev/sdb2           60052       60801     6024375    5  Extended
/dev/sdb5           60052       60801     6024343+  82  Linux swap / Solaris


---

### Post by Fxy on 2010-03-25
Don't know if this is any help, but take a look at this link...  [Windows MBR ]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/")  Haven't used windows 7 much so i don't know much about it yet :?

If your search the forums there is people that have had problems like this in the past with xp & vista, maybe the commands/methods that they used could work for you...

---

### Post by Jeff May on 2010-03-25
Qvark -

I posted something last night because I had a similar issue myself and have seen many related threads all over the place.  It appears that when upgrading a prior version of Ubuntu (in my case Karmic) to 10.04 beta1, Grub is installed on the first partition of the drive, overwriting the Windows 7 bootloader.  Depending on the way your machine is partitioned it seems to result in either the problem you are describing, or selecting your Windows install results in the Grub menu being reloaded over and over again.

See my [EARLIER POST]("http://ubuntuforums.org/showthread.php?t=1438399")  on this forum: [1438399 ]("http://ubuntuforums.org/showthread.php?t=1438399")

---

### Post by wkulecz on 2010-03-25
What is worse, the "advanced" button on the 10.04beta installer step 8 of 8 screen  offers a choice of where to install the boot loader but it doesn't honor it! :(

On my test system 10.04 is making the same mistake as 9.10 did -- making my SATA drive be sda instead of making the primary IDE drive the boot disk as set in the BIOS.

I think hiding the difference between SATA and IDE drives and lumping them all as sdx drives is a bad idea, as is ignoring the BIOS boot order setting!

Is there a better place to post this?  Some 10.04Beta specific forum perhaps?

There have been a lot of dual boot issues in 9.10, I predict things will be worse with 10.04 as lot of "users" only do LTS versions.  The change from grub to grub2 will be a rude surprise!  It wasn't smooth in 9.10, and 10.04Beta has certainly not fixed it!

I'm installing 10.04Beta to ext3 so I can use grub after 10.04 grub2 screws up :(

--wally.


EDIT:  the drop down box listing the drive options to install the boot loader doesn't work, but it appears I can edit the sda selection to sdb and click "OK".  Its installing now.  Will report back as to if it works or not.  My BIOS will boot from what the installer thinks is /dev/sdb.  I predict trouble!


FOLLOW UP:  The manual change to install grub2 from /dev/sda to /dev/sdb appears to work and the 10.04 system booted up fine.  However, this drive had grub 2 on it from my initial 9.10 tests so I realize I can't be 100% sure the change worked unless I can catch a change in the grub2 version number as it boots.

Video (1920x1200), sound, and wired network all work fine on initial boot up.  Firefox seems very slow on DNS look ups,  9.10 had this initially too, I think it was an IP6 issue that was fixed by a fairly early update.  Default fonts all seem very clear and readable.  Already seem to have found a bug when trying to change the default power options -- the "authenticate" screen wouldn't go away when I clicked the "Authenticate" button.

---

### Post by Qvark on 2010-03-25
Thank you for the fast answers! I will look in to the post you made.

---

