---
title: "Grub2 finds windows 7 but won't boot"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by Micano on 2010-03-07
Hey

About a week ago I installed Ubuntu 9.10 in dual boot with Windows 7.  That worked fine, and I could load either one with grub. But yesterday I  decided to try the 10.04 beta, so I upgraded, and now Grub2 will find  Windows 7, but when I enter to boot with that, I just get a blank  screen, and nothing will happen unless I turn off my laptop. Ubuntu  works fine to boot.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 596619582 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 596494494 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 596493334 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda4 and 
                       looks at sector 596627558 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #4 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    30,715,903    30,713,856  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     30,715,904   343,290,936   312,575,033   7 HPFS/NTFS
/dev/sda3         343,292,985   595,786,589   252,493,605   f W95 Ext d (LBA)
/dev/sda5         343,293,048   595,777,216   252,484,169   7 HPFS/NTFS
/dev/sda4         595,786,590   625,137,344    29,350,755  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        D0DAAFB9DAAF9A6C                       ntfs       OS                            
/dev/sda3: PTTYPE="dos" 
/dev/sda4        6d1bba2b-6872-4846-9823-9dc8dc061d90   ext4                                     
/dev/sda5        5B8601CA50A3FA07                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda4/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6d1bba2b-6872-4846-9823-9dc8dc061d90

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

title        Ubuntu lucid (development branch), kernel 2.6.32-15-generic-pae
uuid        6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel        /boot/vmlinuz-2.6.32-15-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-15-generic-pae
quiet

title        Ubuntu lucid (development branch), kernel 2.6.32-15-generic-pae (recovery mode)
uuid        6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel        /boot/vmlinuz-2.6.32-15-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro  single
initrd        /boot/initrd.img-2.6.32-15-generic-pae

title        Ubuntu lucid (development branch), kernel 2.6.32-15-generic
uuid        6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel        /boot/vmlinuz-2.6.32-15-generic root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-15-generic
quiet

title        Ubuntu lucid (development branch), kernel 2.6.32-15-generic (recovery mode)
uuid        6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel        /boot/vmlinuz-2.6.32-15-generic root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro  single
initrd        /boot/initrd.img-2.6.32-15-generic

title        Chainload into GRUB 2
root        6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel        /boot/grub/core.img

title        Ubuntu lucid (development branch), memtest86+
uuid        6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root=(hd0,4)
search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
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
set root=(hd0,4)
search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
set locale_dir=($root)/boot/grub/locale
set lang=
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
menuentry "Ubuntu, with Linux 2.6.32-15-generic-pae" {
        recordfail
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
    linux    /boot/vmlinuz-2.6.32-15-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-15-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-15-generic-pae (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
    echo    Loading Linux 2.6.32-15-generic-pae ...
    linux    /boot/vmlinuz-2.6.32-15-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-15-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-15-generic" {
        recordfail
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
    linux    /boot/vmlinuz-2.6.32-15-generic root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-15-generic
}
menuentry "Ubuntu, with Linux 2.6.32-15-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
    echo    Loading Linux 2.6.32-15-generic ...
    linux    /boot/vmlinuz-2.6.32-15-generic root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-15-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 6d1bba2b-6872-4846-9823-9dc8dc061d90
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 3c98-ac5d
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set d0daafb9daaf9a6c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda4 :
UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 / ext4 errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda2 /media/OS ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /media/DATA ntfs-3g defaults,locale=en_US.UTF-8 0 0
/mnt/2048mb.swap none swap sw 0 0

=================== sda4: Location of files loaded by Grub: ===================


 305.4GB: boot/grub/core.img
 305.6GB: boot/grub/grub.cfg
 312.7GB: boot/grub/menu.lst
 305.4GB: boot/grub/stage2
 316.1GB: boot/initrd.img-2.6.32-15-generic
 316.3GB: boot/initrd.img-2.6.32-15-generic-pae
 317.5GB: boot/vmlinuz-2.6.32-15-generic
 317.6GB: boot/vmlinuz-2.6.32-15-generic-pae
 316.3GB: initrd.img
 316.1GB: initrd.img.old
 317.6GB: vmlinuz
 317.5GB: vmlinuz.old

```Here's what I get from running sudo update-grub
```

Found kernel: /boot/vmlinuz-2.6.32-15-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-15-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin

``````

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
# kopt=root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6d1bba2b-6872-4846-9823-9dc8dc061d90

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

title        Ubuntu lucid (development branch), kernel 2.6.32-15-generic-pae
uuid        6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel        /boot/vmlinuz-2.6.32-15-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-15-generic-pae
quiet

title        Ubuntu lucid (development branch), kernel 2.6.32-15-generic-pae (recovery mode)
uuid        6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel        /boot/vmlinuz-2.6.32-15-generic-pae root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro  single
initrd        /boot/initrd.img-2.6.32-15-generic-pae

title        Ubuntu lucid (development branch), kernel 2.6.32-15-generic
uuid        6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel        /boot/vmlinuz-2.6.32-15-generic root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-15-generic
quiet

title        Ubuntu lucid (development branch), kernel 2.6.32-15-generic (recovery mode)
uuid        6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel        /boot/vmlinuz-2.6.32-15-generic root=UUID=6d1bba2b-6872-4846-9823-9dc8dc061d90 ro  single
initrd        /boot/initrd.img-2.6.32-15-generic

title        Chainload into GRUB 2
root        6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel        /boot/grub/core.img

title        Ubuntu lucid (development branch), memtest86+
uuid        6d1bba2b-6872-4846-9823-9dc8dc061d90
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by oldfred on 2010-03-07
I chainboot a few things but I only put grub in a few partitions. 

You seem to have installed grub or grub2 into just about every partition. Your windows will not boot since you have grub in its boot sector or partition boot record. You will have to run windows repairs to fix that.

I am not sure if you are booting directly or chainboot into sda4? Having both old grub and new grub in the same partition often leads to issues.

Lets repair win7 first. Use your win7 disk but do not run fixboot unless you want to test direct booting of win7, if you do that you will have to reinstall grub to the MBR. At this point I am not sure which grub you restall. I have to review some more.

Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by meierfra. on 2010-03-07
> sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 596494494 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe
 
You installed Grub to the boot sector of the Windows 7 partition.  That erased some of the code necessary to "Window 7".

I suggest to use "testdisk" to restore the boot sector from the backup:

   ```
sudo apt-get install testdisk
```
(if apt-get cannot find the "testdisk" you need to enable the "universe" repository in "System->Administration->Software Sources" and run "sudo apt--get update" )
  
  ```
 sudo testdisk /dev/sda
```

At the first  press "enter" to "proceed".
At the next screen:  "intel"
 "advanced",
Select the Windows  partition /dev/sda2 and choose "boot" 
"BackupBS"
 type "Y" to confirm

The press "q" a few times to quit testdisk.

Reboot and see whether you can boot into Window 7.


Edit:   There is nothing wrong with your MBR, file system or BCD. So running all whose commands suggested by oldfred is unnecessary.

If you want, you can  use "bootrec /fixboot" from the Window 7 CD in place of Testdisk  to fix the boot sector.

---

### Post by Micano on 2010-03-07
> **meierfra. said:**
> You installed Grub to the boot sector of the Windows 7 partition.  That erased some of the code necessary to "Window 7".

I suggest to use "testdisk" to restore the boot sector from the backup:

   ```
sudo apt-get install testdisk
```
(if apt-get cannot find the "testdisk" you need to enable the "universe" repository in "System->Administration->Software Sources" and run "sudo apt--get update" )
  
  ```
 sudo testdisk /dev/sda
```

At the first  press "enter" to "proceed".
At the next screen:  "intel"
 "advanced",
Select the Windows  partition /dev/sda2 and choose "boot" 
"BackupBS"
 type "Y" to confirm

The press "q" a few times to quit testdisk.

Reboot and see whether you can boot into Window 7.


Edit:   There is nothing wrong with your MBR, file system or BCD. So running all whose commands suggested by oldfred is unnecessary.

If you want, you can  use "bootrec /fixboot" from the Window 7 CD in place of Testdisk  to fix the boot sector.

Thank you so much, meierfra.! It worked. Now is there anything else I have to do? Since grub seems to be installed in every partition or what oldfred was saying. And thanks oldfred as well for the fast replies. Amazingly fast answers. Thanks once again!

---

### Post by oldfred on 2010-03-07
Having all the grubs installed is not a problem as it is in space at the beginning of a partition that is not otherwise used. I do not know a way to uninstall, just to install. As long as your system boots ok then you should be fine. 
I would review why you have added so many grubs during your install processes to see when & where it is required and not just automatically install it.

---

### Post by Micano on 2010-03-07
> **oldfred said:**
> Having all the grubs installed is not a problem as it is in space at the beginning of a partition that is not otherwise used. I do not know a way to uninstall, just to install. As long as your system boots ok then you should be fine. 
I would review why you have added so many grubs during your install processes to see when & where it is required and not just automatically install it.

Okay thanks. I do not know either, really strange how it happened. All I did was to install Ubuntu 9.10, and then upgrade to 10.04. Well as long as it works I guess. Thanks guys!

---

### Post by zoso375 on 2010-03-27
Just wanted to say I had this same problem, and testdisk worked like a charm, so thanks for the fix! The problem repeats itself, though, on every update of Lucid. I have this solution bookmarked to run every time I update. Any ideas on a permanent fix?

---

### Post by oldfred on 2010-03-27
I have run this in Karmic just to see what it does, but I do not know about lucid yet. Did you originally install to the partition? This supposedly resets the default location that is stored.

sudo dpkg-reconfigure grub-pc

These were related comments from another thread where someone did this:
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/debconf/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda after grub-pc package updates to keep stage1 install in sync.

meierfra has also created a web page with the procedure on using testdisk to repair:
Restore PBR boot sector for windows from linux using testdisk
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by frmdstryr on 2010-05-02
Worked!!!

I had just updated from ubuntu 9.10 to 10.04 on my 64 bit box.  The grub listed windows but I got the 

no module name found 
press any key to continue

message.  Ubuntu still booted so i ran this and then it fixed the boot error!  Thanks.

---

### Post by RoyaleTee on 2010-05-11
Thanks meierfra. ! Totally worked. Thought I was going to drive myself crazy trying to figure that out. Great fix :)

---

### Post by bgmomof2 on 2010-07-01
[LEFT]I've been struggling with a similar problem with Win XP.  Will I be able to use the same process explained? Or can anyone point me to the necessary fix? [/LEFT]

---

### Post by oldfred on 2010-07-02
meierfra. explained it in his posts above and then he created a page that we have recommended to hundreds on this site to use to fix grub installed to the windows partition. I posted link above but here it is again:

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by bgmomof2 on 2010-07-02
Thanks so much oldfred~!  I needed the assurance that the fix described would work for WinXP also.  It did in fact work. :p

---

