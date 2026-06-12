---
title: "Only partial list of kernels in grub"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by circum on 2010-08-26
I have Ubuntu 8.04 (32-bits) installed on /dev/sda and Ubuntu 10.04 (64-bits) installed on /dev/sdc (this is an update from 8.04 64-bits originally installed on /dev/sdc).

There is a grub on each of these two disks. Both are the old grub (prior to version 2). Here is the top kernel listing from /dev/sda:

title		Ubuntu 10.04 LTS, kernel 2.6.32-24-generic (grub sur unite1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro quiet splash locale=fr_FR
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

and here is the top kernel listing from /dev/sdc:

title		Ubuntu 10.04 LTS, kernel 2.6.32-24-generic (menu sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro quiet splash locale=fr_FR
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

My problem is that the top entry I see when I boot refers to kernel 2.6.32-22 and does NOT have a comment in parentheses (that I use to indicate where the menu.lst information is from). So I cannot boot with the most recent kernel and I don't know where grub gets the menu it show upon boot.

My question: where is the list that is shown at boot time from?

Thanks for your help!


Benoît Gauthier

---

### Post by oldfred on 2010-08-26
Post this and tell us which drive you have set in BIOS to boot from.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by circum on 2010-08-26
The BIOS is set to boot from PM-WDC-WD1600A (/dev/sda), then 4M-WDC-WD3200A, then 3M-WDC-WD3200A, then SM-WDC-WD3200A.

Here is the output from the script.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 541261887 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disque /dev/sda: 160.0 Go, 160041885696 octets
255 têtes, 63 secteurs/piste, 19457 cylindres, total 312581808 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   299,805,029   299,804,967  83 Linux
/dev/sda2         299,805,030   312,576,704    12,771,675   5 Extended
/dev/sda5         299,805,093   312,576,704    12,771,612  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disque /dev/sdb: 320.1 Go, 320072933376 octets
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disque /dev/sdc: 320.1 Go, 320072933376 octets
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   599,738,579   599,738,517  83 Linux
/dev/sdc2         599,738,580   625,137,344    25,398,765   5 Extended
/dev/sdc5         599,738,643   625,137,344    25,398,702  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disque /dev/sdd: 320.1 Go, 320072933376 octets
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   625,137,344   625,137,282  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07c66880-011f-4496-94ea-d4f6495d3d31   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        33721118-6385-4932-bd12-b18f80fc7594   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6f17fe10-87b9-4ee5-99dd-4e2869a60242   ext3                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        761c3d13-cc55-4117-934f-693766e122b6   ext3                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        89df6c37-ccda-463a-9e33-9cdde62e3de4   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        69552655-b097-44db-8c07-7628e93d6054   ext3                                     
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext3       (rw,errors=remount-ro)
/dev/sdb1        /mnt/unite2              ext3       (rw,errors=remount-ro)
/dev/sdd1        /mnt/unite4              ext3       (rw,errors=remount-ro)
/dev/sda1        /mnt/unite1              ext3       (rw,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-24-generic (grub sur unite1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro quiet splash locale=fr_FR
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-24-generic (recovery) (grub sur unite1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (grub sur unite1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode) (grub sur unite1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (grub sur unite1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode) (grub sur unite1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+ (grub sur unite1)
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=07c66880-011f-4496-94ea-d4f6495d3d31 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=33721118-6385-4932-bd12-b18f80fc7594 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
# second 320 gig
/dev/sdb1	/mnt/unite2	ext3	defaults,errors=remount-ro	0	1
# troisième 320 gig
/dev/sdc1	/mnt/unite3	ext3	defaults,errors=remount-ro	0	1
# troisième 320 gig
/dev/sdd1	/mnt/unite4	ext3	defaults,errors=remount-ro	0	1

=================== sda1: Location of files loaded by Grub: ===================


 116.6GB: boot/grub/menu.lst
 116.5GB: boot/grub/stage2
 116.5GB: boot/initrd.img-2.6.22-14-generic
  56.9GB: boot/initrd.img-2.6.22-14-generic.bak
 116.5GB: boot/initrd.img-2.6.24-22-generic
 116.6GB: boot/initrd.img-2.6.24-22-generic.bak
   3.0GB: boot/vmlinuz-2.6.22-14-generic
 116.5GB: boot/vmlinuz-2.6.24-22-generic
 116.5GB: initrd.img
 116.5GB: vmlinuz

=========================== sdc1/boot/grub/menu.lst: ===========================

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
# defoptions=quiet splash locale=fr_FR

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-24-generic (menu sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro quiet splash locale=fr_FR
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-24-generic (recovery) (menu sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (menu sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro quiet splash locale=fr_FR
initrd		/boot/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery) (menu sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (menu sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro quiet splash locale=fr_FR
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery) (menu sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.24-28-generic (menu sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro quiet splash locale=fr_FR
initrd		/boot/initrd.img-2.6.24-28-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.24-28-generic (recovery) (menu sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single
initrd		/boot/initrd.img-2.6.24-28-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title           Ubuntu 8.04.1, kernel 2.6.24-22-generic (menu sdc1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-22-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro quiet splash
initrd          /boot/initrd.img-2.6.24-22-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery) (menu sdc1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-22-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro single
initrd          /boot/initrd.img-2.6.24-22-generic

#title           Ubuntu 8.04.1, kernel 2.6.22-14-generic (menu sdc1)
#root            (hd0,0)
#kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro quiet splash
#initrd          /boot/initrd.img-2.6.22-14-generic
#quiet
#
#title           Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery) (menu sdc1)
#root            (hd0,0)
#kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro single
#initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 8.04.1, memtest86+ (unite3)
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	linux	/boot/vmlinuz-2.6.24-28-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.24-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	echo	'Loading Linux 2.6.24-28-generic ...'
	linux	/boot/vmlinuz-2.6.24-28-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.24-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	linux	/boot/vmlinuz-2.6.24-27-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.24-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	echo	'Loading Linux 2.6.24-27-generic ...'
	linux	/boot/vmlinuz-2.6.24-27-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.24-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#
# /dev/sdc1 - Ubuntu 64 bits
UUID=761c3d13-cc55-4117-934f-693766e122b6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc5
UUID=89df6c37-ccda-463a-9e33-9cdde62e3de4 none            swap    sw              0      0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
	#
# Ubuntu 32 bits
/dev/sda1	/mnt/unite1	ext3	defaults,errors=remount-ro	0	1
#
# disque Windows sur VMWare
/dev/sdb1	/mnt/unite2	ext3	defaults,errors=remount-ro	0	1
#
# disque de données
/dev/sdd1	/mnt/unite4	ext3	defaults,errors=remount-ro	0	1

=================== sdc1: Location of files loaded by Grub: ===================


 277.1GB: boot/grub/core.img
 277.0GB: boot/grub/grub.cfg
 277.1GB: boot/grub/menu.lst
 277.0GB: boot/initrd.img-2.6.24-28-generic
 277.0GB: boot/initrd.img-2.6.24-28-generic.bak
 277.1GB: boot/initrd.img-2.6.32-22-generic
 277.1GB: boot/initrd.img-2.6.32-23-generic
 277.0GB: boot/initrd.img-2.6.32-24-generic
 277.0GB: boot/vmlinuz-2.6.24-28-generic
 277.1GB: boot/vmlinuz-2.6.32-22-generic
 277.0GB: boot/vmlinuz-2.6.32-23-generic
 277.1GB: boot/vmlinuz-2.6.32-24-generic
 277.0GB: initrd.img
 277.1GB: initrd.img.old
 277.1GB: vmlinuz
 277.0GB: vmlinuz.old

```

---

### Post by oldfred on 2010-08-26
Script only shows grub2 in the MBR of sda and booting thru first partition. Either grub or the script often mis identify the drive number so I think you are booting the install in sdc.

I prefer to have each install's boot loader in the MBR of the drive the install is in. That way each drive can boot on its own.

If you are booted into 10.04.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdc"  then just run:
sudo grub-install /dev/sdc
If that returns any errors run:
sudo grub-install --recheck /dev/sdc
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

After the sudo update-grub it should find all your other installs. Because they use grub legacy the procedure to install them is different if you want their boot loading in their drives.

#reset grub legacy boot
sudo grub
find /boot/grub/stage1 #you will get a response such as  (hd0,0)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition  or root (hd0,0)
setup (hd0)

---

### Post by circum on 2010-08-27
Fabulous! After following your lead, I now have a complete list of kernels upon boot. Thanks!

There is one other task at hand, though. The current grub install still sees a 32-bit Ubuntu 8.04 install on /dev/sda even though I deleted /dev/sda5, resized /dev/sda1 to the whole disk, and turned off the boot flag. The file listing on /mnt/unite1 (which is a mount of /dev/sda1) is empty. Still, the system is able to boot using 32-bit Ubuntu 8.04! Quite resilient, isn't it? I don't know where the boot is performed.

My question: how can I eradicate all trace of the 32-bit Ubuntu 8.04 install and reclaim /dev/sda1 for other purposes while automatically booting from /dev/sdc. I have pasted the updated boot_info_script055 RESULTS.txt file below. Thanks again for all your useful help.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 541261887 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disque /dev/sda: 160.0 Go, 160041885696 octets
255 têtes, 63 secteurs/piste, 19457 cylindres, total 312581808 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   312,576,704   312,576,642  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disque /dev/sdb: 320.1 Go, 320072933376 octets
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disque /dev/sdc: 320.1 Go, 320072933376 octets
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   599,738,579   599,738,517  83 Linux
/dev/sdc2         599,738,580   625,137,344    25,398,765   5 Extended
/dev/sdc5         599,738,643   625,137,344    25,398,702  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disque /dev/sdd: 320.1 Go, 320072933376 octets
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   625,137,344   625,137,282  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07c66880-011f-4496-94ea-d4f6495d3d31   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6f17fe10-87b9-4ee5-99dd-4e2869a60242   ext3                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        761c3d13-cc55-4117-934f-693766e122b6   ext3                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        89df6c37-ccda-463a-9e33-9cdde62e3de4   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        69552655-b097-44db-8c07-7628e93d6054   ext3                                     
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext3       (rw,errors=remount-ro)
/dev/sda1        /mnt/unite1              ext3       (rw,errors=remount-ro)
/dev/sdb1        /mnt/unite2              ext3       (rw,errors=remount-ro)
/dev/sdd1        /mnt/unite4              ext3       (rw,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-24-generic (grub sur unite1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro quiet splash locale=fr_FR
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-24-generic (recovery) (grub sur unite1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (grub sur unite1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode) (grub sur unite1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (grub sur unite1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode) (grub sur unite1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+ (grub sur unite1)
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=07c66880-011f-4496-94ea-d4f6495d3d31 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=33721118-6385-4932-bd12-b18f80fc7594 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
# second 320 gig
/dev/sdb1	/mnt/unite2	ext3	defaults,errors=remount-ro	0	1
# troisième 320 gig
/dev/sdc1	/mnt/unite3	ext3	defaults,errors=remount-ro	0	1
# troisième 320 gig
/dev/sdd1	/mnt/unite4	ext3	defaults,errors=remount-ro	0	1

=================== sda1: Location of files loaded by Grub: ===================


 116.6GB: boot/grub/menu.lst
 116.5GB: boot/grub/stage2
 116.5GB: boot/initrd.img-2.6.22-14-generic
  56.9GB: boot/initrd.img-2.6.22-14-generic.bak
 116.5GB: boot/initrd.img-2.6.24-22-generic
 116.6GB: boot/initrd.img-2.6.24-22-generic.bak
   3.0GB: boot/vmlinuz-2.6.22-14-generic
 116.5GB: boot/vmlinuz-2.6.24-22-generic
 116.5GB: initrd.img
 116.5GB: vmlinuz

=========================== sdc1/boot/grub/menu.lst: ===========================

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
# defoptions=quiet splash locale=fr_FR

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-24-generic (menu sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro quiet splash locale=fr_FR
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-24-generic (recovery) (menu sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (menu sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro quiet splash locale=fr_FR
initrd		/boot/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery) (menu sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (menu sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro quiet splash locale=fr_FR
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery) (menu sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.24-28-generic (menu sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro quiet splash locale=fr_FR
initrd		/boot/initrd.img-2.6.24-28-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.24-28-generic (recovery) (menu sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-28-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single
initrd		/boot/initrd.img-2.6.24-28-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title           Ubuntu 8.04.1, kernel 2.6.24-22-generic (menu sdc1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-22-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro quiet splash
initrd          /boot/initrd.img-2.6.24-22-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery) (menu sdc1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-22-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro single
initrd          /boot/initrd.img-2.6.24-22-generic

#title           Ubuntu 8.04.1, kernel 2.6.22-14-generic (menu sdc1)
#root            (hd0,0)
#kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro quiet splash
#initrd          /boot/initrd.img-2.6.22-14-generic
#quiet
#
#title           Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery) (menu sdc1)
#root            (hd0,0)
#kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro single
#initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 8.04.1, memtest86+ (unite3)
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
set locale_dir=($root)/boot/grub/locale
set lang=fr
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
menuentry 'Ubuntu, avec Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-24-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	echo	'Chargement de Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single 
	echo	'Chargement du disque mémoire initial...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-23-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	echo	'Chargement de Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single 
	echo	'Chargement du disque mémoire initial...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-22-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	echo	'Chargement de Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single 
	echo	'Chargement du disque mémoire initial...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, avec Linux 2.6.24-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	linux	/boot/vmlinuz-2.6.24-28-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.24-28-generic
}
menuentry 'Ubuntu, avec Linux 2.6.24-28-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	echo	'Chargement de Linux 2.6.24-28-generic ...'
	linux	/boot/vmlinuz-2.6.24-28-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single 
	echo	'Chargement du disque mémoire initial...'
	initrd	/boot/initrd.img-2.6.24-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 8.04.1, kernel 2.6.24-22-generic (grub sur unite1) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 07c66880-011f-4496-94ea-d4f6495d3d31
	linux /boot/vmlinuz-2.6.24-22-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro quiet splash
	initrd /boot/initrd.img-2.6.24-22-generic
}
menuentry "Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode) (grub sur unite1) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 07c66880-011f-4496-94ea-d4f6495d3d31
	linux /boot/vmlinuz-2.6.24-22-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro single
	initrd /boot/initrd.img-2.6.24-22-generic
}
menuentry "Ubuntu 8.04.1, kernel 2.6.22-14-generic (grub sur unite1) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 07c66880-011f-4496-94ea-d4f6495d3d31
	linux /boot/vmlinuz-2.6.22-14-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro quiet splash
	initrd /boot/initrd.img-2.6.22-14-generic
}
menuentry "Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode) (grub sur unite1) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 07c66880-011f-4496-94ea-d4f6495d3d31
	linux /boot/vmlinuz-2.6.22-14-generic root=UUID=07c66880-011f-4496-94ea-d4f6495d3d31 ro single
	initrd /boot/initrd.img-2.6.22-14-generic
}
menuentry "Ubuntu 8.04.1, memtest86+ (grub sur unite1) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 07c66880-011f-4496-94ea-d4f6495d3d31
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#
# /dev/sdc1 - Ubuntu 64 bits
UUID=761c3d13-cc55-4117-934f-693766e122b6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc5
UUID=89df6c37-ccda-463a-9e33-9cdde62e3de4 none            swap    sw              0      0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
	#
# Ubuntu 32 bits
/dev/sda1	/mnt/unite1	ext3	defaults,errors=remount-ro	0	1
#
# disque Windows sur VMWare
/dev/sdb1	/mnt/unite2	ext3	defaults,errors=remount-ro	0	1
#
# disque de données
/dev/sdd1	/mnt/unite4	ext3	defaults,errors=remount-ro	0	1

=================== sdc1: Location of files loaded by Grub: ===================


 277.0GB: boot/grub/core.img
 277.0GB: boot/grub/grub.cfg
 277.1GB: boot/grub/menu.lst
 277.0GB: boot/grub/stage2
 277.0GB: boot/initrd.img-2.6.24-28-generic
 277.0GB: boot/initrd.img-2.6.24-28-generic.bak
 277.1GB: boot/initrd.img-2.6.32-22-generic
 277.1GB: boot/initrd.img-2.6.32-23-generic
 277.0GB: boot/initrd.img-2.6.32-24-generic
 277.0GB: boot/vmlinuz-2.6.24-28-generic
 277.1GB: boot/vmlinuz-2.6.32-22-generic
 277.0GB: boot/vmlinuz-2.6.32-23-generic
 277.1GB: boot/vmlinuz-2.6.32-24-generic
 277.0GB: initrd.img
 277.1GB: initrd.img.old
 277.1GB: vmlinuz
 277.0GB: vmlinuz.old

```

---

### Post by circum on 2010-08-27
Correction: /dev/sda1 still contains the 32-bits Ubuntu 8.04 installation. I would like to wipe out /dev/sda1 to reuse the disk for other purposes (still in the same computer). It is easy to delete all files and then run "update-grub" on /dev/sdc1, I guess, to inform grub that there are no more kernels there.

Is that all there is to it? If I do that, will the BIOS simply cascade to the third disk, in search for a bootable disk?

All help is welcome. Thanks in advance.


Benoît Gauthier

---

### Post by oldfred on 2010-08-27
It might be better to set BIOS to boot sdc first. You can erase everything in sda and the MBR will still have your grub2 and let you boot with that if you still want to boot from sda.

You can just delete all the files in sda1 or use gparted to reformat it. I like to have a separate /data partition for my data so /home says small and is easier to back up.

You still show a menu.lst in your sdc1 install. Before some users had issues with old grub and grub2 conflicting. Perhaps in all the fixes to grub2 that is not an issue but you may also want to remove old grub.

---

### Post by circum on 2010-08-27
Great! This discussion has been very illuminating and informative. I have solved a thorny (for me!) grub issue and my system is cleaner now.

Thank you very much for your help. I hope I can do the same for you some day.

---

### Post by oldfred on 2010-08-27
Glad you got it working.

---

### Post by circum on 2010-09-01
New kernel update this morning (2.6.24-28). Upon reboot, two problems: first, no list of kernels was shown by grub (at all) and, second, /boot/grub/grub.cfg does not reference the new kernel. I ran update-grub and the new kernel is still not referenced in grub.cfg. What's happening?

Benoît

---

### Post by oldfred on 2010-09-01
Did you boot the same drive? And did grub update that drive or revert back and update grub in sda? But you still should get the current system.

If not booting sda this may help grub remember where to reinstall.

to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

You hold down shift from BIOS until menu appears if you are not getting a menu for grub2, It was escape for grub legacy.

---

### Post by circum on 2010-09-01
I did not change the boot order in the BIOS, so the system goes to /dev/sda first but that drive contains nothing but an MBR (I reformatted it in ext4 whereas it was ext3 before, so it is really wiped out). I guess I could play with the BIOS boot order to place /dev/sdc first.

As for sudo dpkg-reconfigure grub-pc, it already shows /dev/sdc as the one and only grub install device. Why then didn't the kernel update get reflected in grub.cfg?


Benoît

---

### Post by oldfred on 2010-09-01
You showed this in your boot script results:

Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

The menu.lst is from grub legacy and grub.cfg is grub2. Maybe it is confused.

Can you boot?

# uninstall both grub legacy & grub2 reinstall grub2 and to sdc
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sdc
grub-install --recheck /dev/sdc

sudo dpkg-reconfigure grub-pc

---

### Post by circum on 2010-09-01
As per your suggestion, I have uninstalled all grubs and reinstalled version 2. I have also put /dev/sdc in first boot position in the BIOS (I think).

Same behaviour: no grub menu and 2.6.32-24 whereas there is a 2.6.24-28 (that's twenty-eight) kernel available.

I have run boot_info_script055.sh again. The output is pasted below.

[ code]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 541261887 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disque /dev/sda: 160.0 Go, 160041885696 octets
255 têtes, 63 secteurs/piste, 19457 cylindres, total 312581808 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   312,576,704   312,576,642  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disque /dev/sdb: 320.1 Go, 320072933376 octets
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disque /dev/sdc: 320.1 Go, 320072933376 octets
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   599,738,579   599,738,517  83 Linux
/dev/sdc2         599,738,580   625,137,344    25,398,765   5 Extended
/dev/sdc5         599,738,643   625,137,344    25,398,702  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disque /dev/sdd: 320.1 Go, 320072933376 octets
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   625,137,344   625,137,282  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        b1230be7-26e4-4b1b-bb92-b64b9ce7c05c   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6f17fe10-87b9-4ee5-99dd-4e2869a60242   ext3                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        761c3d13-cc55-4117-934f-693766e122b6   ext3                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        89df6c37-ccda-463a-9e33-9cdde62e3de4   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        69552655-b097-44db-8c07-7628e93d6054   ext3                                     
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext3       (rw,errors=remount-ro)
/dev/sda1        /mnt/unite1              ext4       (rw,errors=remount-ro)
/dev/sdb1        /mnt/unite2              ext3       (rw,errors=remount-ro)
/dev/sdd1        /mnt/unite4              ext3       (rw,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
set locale_dir=($root)/boot/grub/locale
set lang=fr
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
menuentry 'Ubuntu, avec Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-24-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	echo	'Chargement de Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single 
	echo	'Chargement du disque mémoire initial...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-23-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	echo	'Chargement de Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single 
	echo	'Chargement du disque mémoire initial...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-22-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	echo	'Chargement de Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single 
	echo	'Chargement du disque mémoire initial...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, avec Linux 2.6.24-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	linux	/boot/vmlinuz-2.6.24-28-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.24-28-generic
}
menuentry 'Ubuntu, avec Linux 2.6.24-28-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	echo	'Chargement de Linux 2.6.24-28-generic ...'
	linux	/boot/vmlinuz-2.6.24-28-generic root=UUID=761c3d13-cc55-4117-934f-693766e122b6 ro single 
	echo	'Chargement du disque mémoire initial...'
	initrd	/boot/initrd.img-2.6.24-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 761c3d13-cc55-4117-934f-693766e122b6
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

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#
# /dev/sdc1 - Ubuntu 64 bits
UUID=761c3d13-cc55-4117-934f-693766e122b6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc5
UUID=89df6c37-ccda-463a-9e33-9cdde62e3de4 none            swap    sw              0      0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
	#
# Ubuntu 32 bits
/dev/sda1	/mnt/unite1	ext4	defaults,errors=remount-ro	0	1
#
# disque Windows sur VMWare
/dev/sdb1	/mnt/unite2	ext3	defaults,errors=remount-ro	0	1
#
# disque de données
/dev/sdd1	/mnt/unite4	ext3	defaults,errors=remount-ro	0	1

=================== sdc1: Location of files loaded by Grub: ===================


 277.1GB: boot/grub/core.img
 277.1GB: boot/grub/grub.cfg
 277.0GB: boot/initrd.img-2.6.24-28-generic
 277.0GB: boot/initrd.img-2.6.24-28-generic.bak
 277.1GB: boot/initrd.img-2.6.32-22-generic
 277.1GB: boot/initrd.img-2.6.32-23-generic
 277.0GB: boot/initrd.img-2.6.32-24-generic
 277.0GB: boot/vmlinuz-2.6.24-28-generic
 277.1GB: boot/vmlinuz-2.6.32-22-generic
 277.0GB: boot/vmlinuz-2.6.32-23-generic
 277.1GB: boot/vmlinuz-2.6.32-24-generic
 277.0GB: initrd.img
 277.1GB: initrd.img.old
 277.1GB: vmlinuz
 277.0GB: vmlinuz.old[ /code]

---

### Post by oldfred on 2010-09-01
I think you are mixing up the numbering.

 2.6.32-24 This is newer than the one below as it is .32

2.6.24-28 This is older as it is .24

The -24 and -28 are updates within the .32 and .24 versions.

---

### Post by circum on 2010-09-01
I am mixing them up, am I not. Thanks for pointing this out gently. Must be due to my advanced age.

That leaves the issue of not seeing the grub menu when booting. Why do you think this happens?


Benoît

---

### Post by oldfred on 2010-09-01
If you only have Ubuntu on your system it assumes you do not need a menu and tries to speed up booting by not giving you a menu and directly booting the 'only' system.

You can hold down shift key from BIOS boot until menu appears if you want recovery, memory test or edit a boot menu item.

---

### Post by circum on 2010-09-01
Interesting, I did not know that. Great! Thanks very much for all your help. Really appreciated.

Benoît

---

