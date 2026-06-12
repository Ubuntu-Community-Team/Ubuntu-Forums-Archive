---
title: "Mandriva Won't Boot After Ubuntu Install"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by gdawg on 2010-08-08
Hi everyone, I have a triple-boot of Windows Vista, Ubuntu 10.4, and Mandriva 2010. After a re-installation of Ubuntu I have been unable to boot Mandriva (it doesn't appear on the boot menu). I could sure use some help with this. Following is some boot info that I downloaded:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Mandriva Linux release 2010.0 
                       (Official) for i586 Kernel 2.6.31.13-desktop-1mnb on a 
                       Dual-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2              98,304    21,069,823    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,069,824   274,523,138   253,453,315   7 HPFS/NTFS
/dev/sda4         274,524,158   625,137,344   350,613,187   5 Extended
/dev/sda5         424,903,248   616,895,999   191,992,752  83 Linux
/dev/sda6         616,896,063   625,137,344     8,241,282  82 Linux swap / Solaris
/dev/sda7         274,524,160   418,684,927   144,160,768  83 Linux
/dev/sda8         418,686,976   424,902,655     6,215,680  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D8-0216                              vfat       DellUtility                   
/dev/sda2        D2D27844D2782F3B                       ntfs       RECOVERY                      
/dev/sda3        128A33478A33269F                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        6dfd1df8-95e9-4769-83e0-755984ed4aad   ext4                                     
/dev/sda6        e3b2a6ec-ae10-462e-b967-5d926420663b   swap                                     
/dev/sda7        84c3195d-b758-49d4-985c-ece79f2f8c05   ext4                                     
/dev/sda8        ff7f2325-686d-4a9e-9081-27f77a45625f   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/menu.lst: ===========================

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,4)/boot/gfxmenu
default 0

title windows
root (hd0,2)
makeactive
chainloader +1

title linux
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad resume=UUID=e3b2a6ec-ae10-462e-b967-5d926420663b splash=silent vga=788
initrd (hd0,4)/boot/initrd.img

title linux-nonfb
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad resume=UUID=e3b2a6ec-ae10-462e-b967-5d926420663b
initrd (hd0,4)/boot/initrd.img

title failsafe
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad failsafe
initrd (hd0,4)/boot/initrd.img

title desktop 2.6.31.5-1mnb
kernel (hd0,4)/boot/vmlinuz-2.6.31.5-desktop-1mnb BOOT_IMAGE=desktop_2.6.31.5-1mnb root=UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad resume=UUID=e3b2a6ec-ae10-462e-b967-5d926420663b splash=silent vga=788
initrd (hd0,4)/boot/initrd-2.6.31.5-desktop-1mnb.img

title desktop 2.6.31.6-1mnb
kernel (hd0,4)/boot/vmlinuz-2.6.31.6-desktop-1mnb BOOT_IMAGE=desktop_2.6.31.6-1mnb root=UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad resume=UUID=e3b2a6ec-ae10-462e-b967-5d926420663b splash=silent vga=788
initrd (hd0,4)/boot/initrd-2.6.31.6-desktop-1mnb.img

title desktop 2.6.31.12-1mnb
kernel (hd0,4)/boot/vmlinuz-2.6.31.12-desktop-1mnb BOOT_IMAGE=desktop_2.6.31.12-1mnb root=UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad resume=UUID=e3b2a6ec-ae10-462e-b967-5d926420663b splash=silent vga=788
initrd (hd0,4)/boot/initrd-2.6.31.12-desktop-1mnb.img

title desktop 2.6.31.12-2mnb
kernel (hd0,4)/boot/vmlinuz-2.6.31.12-desktop-2mnb BOOT_IMAGE=desktop_2.6.31.12-2mnb root=UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad resume=UUID=e3b2a6ec-ae10-462e-b967-5d926420663b splash=silent vga=788
initrd (hd0,4)/boot/initrd-2.6.31.12-desktop-2mnb.img

title desktop 2.6.31.12-3mnb
kernel (hd0,4)/boot/vmlinuz-2.6.31.12-desktop-3mnb BOOT_IMAGE=desktop_2.6.31.12-3mnb root=UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad resume=UUID=e3b2a6ec-ae10-462e-b967-5d926420663b splash=silent vga=788
initrd (hd0,4)/boot/initrd-2.6.31.12-desktop-3mnb.img

title desktop 2.6.31.13-1mnb
kernel (hd0,4)/boot/vmlinuz-2.6.31.13-desktop-1mnb BOOT_IMAGE=desktop_2.6.31.13-1mnb root=UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad resume=UUID=e3b2a6ec-ae10-462e-b967-5d926420663b splash=silent vga=788
initrd (hd0,4)/boot/initrd-2.6.31.13-desktop-1mnb.img

=============================== sda5/etc/fstab: ===============================

# Entry for /dev/sda5 :
UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad / ext4 relatime 1 1
/dev/cdrom /media/cdrom auto umask=0,users,iocharset=utf8,noauto,ro,exec 0 0
# Entry for /dev/sda3 :
UUID=9E207B2B207B0A13 /media/windows ntfs-3g defaults,umask=000 0 0
none /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=e3b2a6ec-ae10-462e-b967-5d926420663b swap swap defaults 0 0

=================== sda5: Location of files loaded by Grub: ===================


 219.8GB: boot/grub/menu.lst
 219.8GB: boot/grub/stage2
 236.6GB: boot/initrd-2.6.31.12-desktop-1mnb.img
 219.1GB: boot/initrd-2.6.31.12-desktop-2mnb.img
 260.1GB: boot/initrd-2.6.31.12-desktop-3mnb.img
 242.6GB: boot/initrd-2.6.31.13-desktop-1mnb.img
 223.0GB: boot/initrd-2.6.31.5-desktop-1mnb.img
 222.5GB: boot/initrd-2.6.31.6-desktop-1mnb.img
 242.6GB: boot/initrd-desktop.img
 242.6GB: boot/initrd.img
 236.7GB: boot/vmlinuz
 232.7GB: boot/vmlinuz-2.6.31.12-desktop-1mnb
 230.4GB: boot/vmlinuz-2.6.31.12-desktop-2mnb
 230.5GB: boot/vmlinuz-2.6.31.12-desktop-3mnb
 236.7GB: boot/vmlinuz-2.6.31.13-desktop-1mnb
 220.0GB: boot/vmlinuz-2.6.31.5-desktop-1mnb
 222.5GB: boot/vmlinuz-2.6.31.6-desktop-1mnb
 236.7GB: boot/vmlinuz-desktop

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=84c3195d-b758-49d4-985c-ece79f2f8c05 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=84c3195d-b758-49d4-985c-ece79f2f8c05

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid        84c3195d-b758-49d4-985c-ece79f2f8c05
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=84c3195d-b758-49d4-985c-ece79f2f8c05 ro quiet splash
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid        84c3195d-b758-49d4-985c-ece79f2f8c05
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=84c3195d-b758-49d4-985c-ece79f2f8c05 ro single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
uuid        84c3195d-b758-49d4-985c-ece79f2f8c05
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=84c3195d-b758-49d4-985c-ece79f2f8c05 ro quiet splash
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid        84c3195d-b758-49d4-985c-ece79f2f8c05
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=84c3195d-b758-49d4-985c-ece79f2f8c05 ro single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic
uuid        84c3195d-b758-49d4-985c-ece79f2f8c05
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=84c3195d-b758-49d4-985c-ece79f2f8c05 ro quiet splash
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid        84c3195d-b758-49d4-985c-ece79f2f8c05
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=84c3195d-b758-49d4-985c-ece79f2f8c05 ro single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        84c3195d-b758-49d4-985c-ece79f2f8c05
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 84c3195d-b758-49d4-985c-ece79f2f8c05
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 84c3195d-b758-49d4-985c-ece79f2f8c05
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 84c3195d-b758-49d4-985c-ece79f2f8c05
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=84c3195d-b758-49d4-985c-ece79f2f8c05 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 84c3195d-b758-49d4-985c-ece79f2f8c05
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=84c3195d-b758-49d4-985c-ece79f2f8c05 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 84c3195d-b758-49d4-985c-ece79f2f8c05
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=84c3195d-b758-49d4-985c-ece79f2f8c05 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 84c3195d-b758-49d4-985c-ece79f2f8c05
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=84c3195d-b758-49d4-985c-ece79f2f8c05 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 84c3195d-b758-49d4-985c-ece79f2f8c05
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=84c3195d-b758-49d4-985c-ece79f2f8c05 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 84c3195d-b758-49d4-985c-ece79f2f8c05
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=84c3195d-b758-49d4-985c-ece79f2f8c05 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 84c3195d-b758-49d4-985c-ece79f2f8c05
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 84c3195d-b758-49d4-985c-ece79f2f8c05
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 128a33478a33269f
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "linux (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6dfd1df8-95e9-4769-83e0-755984ed4aad
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad resume=UUID=e3b2a6ec-ae10-462e-b967-5d926420663b splash=silent vga=788
    initrd (hd0,4)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6dfd1df8-95e9-4769-83e0-755984ed4aad
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad resume=UUID=e3b2a6ec-ae10-462e-b967-5d926420663b
    initrd (hd0,4)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6dfd1df8-95e9-4769-83e0-755984ed4aad
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad failsafe
    initrd (hd0,4)/boot/initrd.img
}
menuentry "desktop 2.6.31.5-1mnb (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6dfd1df8-95e9-4769-83e0-755984ed4aad
    linux /boot/vmlinuz-2.6.31.5-desktop-1mnb BOOT_IMAGE=desktop_2.6.31.5-1mnb root=UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad resume=UUID=e3b2a6ec-ae10-462e-b967-5d926420663b splash=silent vga=788
    initrd (hd0,4)/boot/initrd-2.6.31.5-desktop-1mnb.img
}
menuentry "desktop 2.6.31.6-1mnb (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6dfd1df8-95e9-4769-83e0-755984ed4aad
    linux /boot/vmlinuz-2.6.31.6-desktop-1mnb BOOT_IMAGE=desktop_2.6.31.6-1mnb root=UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad resume=UUID=e3b2a6ec-ae10-462e-b967-5d926420663b splash=silent vga=788
    initrd (hd0,4)/boot/initrd-2.6.31.6-desktop-1mnb.img
}
menuentry "desktop 2.6.31.12-1mnb (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6dfd1df8-95e9-4769-83e0-755984ed4aad
    linux /boot/vmlinuz-2.6.31.12-desktop-1mnb BOOT_IMAGE=desktop_2.6.31.12-1mnb root=UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad resume=UUID=e3b2a6ec-ae10-462e-b967-5d926420663b splash=silent vga=788
    initrd (hd0,4)/boot/initrd-2.6.31.12-desktop-1mnb.img
}
menuentry "desktop 2.6.31.12-2mnb (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6dfd1df8-95e9-4769-83e0-755984ed4aad
    linux /boot/vmlinuz-2.6.31.12-desktop-2mnb BOOT_IMAGE=desktop_2.6.31.12-2mnb root=UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad resume=UUID=e3b2a6ec-ae10-462e-b967-5d926420663b splash=silent vga=788
    initrd (hd0,4)/boot/initrd-2.6.31.12-desktop-2mnb.img
}
menuentry "desktop 2.6.31.12-3mnb (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6dfd1df8-95e9-4769-83e0-755984ed4aad
    linux /boot/vmlinuz-2.6.31.12-desktop-3mnb BOOT_IMAGE=desktop_2.6.31.12-3mnb root=UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad resume=UUID=e3b2a6ec-ae10-462e-b967-5d926420663b splash=silent vga=788
    initrd (hd0,4)/boot/initrd-2.6.31.12-desktop-3mnb.img
}
menuentry "desktop 2.6.31.13-1mnb (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6dfd1df8-95e9-4769-83e0-755984ed4aad
    linux /boot/vmlinuz-2.6.31.13-desktop-1mnb BOOT_IMAGE=desktop_2.6.31.13-1mnb root=UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad resume=UUID=e3b2a6ec-ae10-462e-b967-5d926420663b splash=silent vga=788
    initrd (hd0,4)/boot/initrd-2.6.31.13-desktop-1mnb.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=84c3195d-b758-49d4-985c-ece79f2f8c05 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=ff7f2325-686d-4a9e-9081-27f77a45625f none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 179.3GB: boot/grub/core.img
 192.3GB: boot/grub/grub.cfg
 212.0GB: boot/grub/menu.lst
 179.3GB: boot/initrd.img-2.6.32-21-generic
 179.4GB: boot/initrd.img-2.6.32-23-generic
 180.8GB: boot/initrd.img-2.6.32-24-generic
 179.3GB: boot/vmlinuz-2.6.32-21-generic
 179.3GB: boot/vmlinuz-2.6.32-23-generic
 180.6GB: boot/vmlinuz-2.6.32-24-generic
 180.8GB: initrd.img
 179.4GB: initrd.img.old
 180.6GB: vmlinuz
 179.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  5e 62 80 e0 a8 a1 94 73  2d de 61 01 99 73 7d 36  |^b.....s-.a..s}6|
00000010  8e ef 4d 51 fe f6 db 2d  12 26 8e d9 b2 40 87 36  |..MQ...-.&...@.6|
00000020  a3 2c 23 3f fa ef 45 b6  bb 33 7f bb ce 78 fc d9  |.,#?..E..3...x..|
00000030  53 69 ea fe ee 12 bf 0c  a5 c8 c9 2a ff 55 58 ff  |Si.........*.UX.|
00000040  93 61 e4 1d 60 56 9f 3a  a6 67 0e 9f ca 2f 9a 46  |.a..`V.:.g.../.F|
00000050  1d 42 8b c3 4b 7a 12 ef  dc 6d 8b 9a dc 07 fc 8c  |.B..Kz...m......|
00000060  07 cc 71 76 d5 2d 4a 98  88 dc 21 96 7f 77 f5 34  |..qv.-J...!..w.4|
00000070  7f 2e 7b e3 36 7e 10 f3  f2 bf fd 39 e3 ea 42 50  |..{.6~.....9..BP|
00000080  19 64 7d 6c 85 5f 77 e6  8e bb d9 f0 26 e6 e6 e4  |.d}l._w.....&...|
00000090  0a 21 18 58 e6 e3 a3 46  bd fb 43 bc cf 0e ff 61  |.!.X...F..C....a|
000000a0  08 0d 6b e4 0b 99 fb 7e  d5 fb e4 9a 54 44 24 d3  |..k....~....TD$.|
000000b0  26 ce 6c 9f 84 d2 d9 5d  73 7a 10 45 fb 67 f6 c2  |&.l....]sz.E.g..|
000000c0  cc b8 ee 14 b4 c9 fe 78  f0 d1 d6 dd 55 f2 f0 8d  |.......x....U...|
000000d0  a9 86 1f f1 1a 37 96 57  79 aa 5e 95 0f 3a 0c a4  |.....7.Wy.^..:..|
000000e0  4d 7b 33 3a a3 5e 0b 94  2a a4 af 83 d8 83 38 2e  |M{3:.^..*.....8.|
000000f0  8a de de fc 7a 70 e8 90  95 ff 16 11 46 69 ba af  |....zp......Fi..|
00000100  54 86 2b 7e 9e 9c 40 89  35 01 f1 fa 9b 70 00 e4  |T.+~..@.5....p..|
00000110  7e 97 f0 21 4f 0a 81 21  2b 7e 4d 70 fa 45 09 4e  |~..!O..!+~Mp.E.N|
00000120  dd 2b ca 4d 6f 1a 8c a3  30 63 17 84 05 16 82 98  |.+.Mo...0c......|
00000130  fd 09 cd e9 40 41 d9 bd  64 f8 5a b6 54 f6 2f 34  |....@A..d.Z.T./4|
00000140  27 00 71 ea 17 29 be d1  17 21 70 51 4a dc 9d 6a  |'.q..)...!pQJ..j|
00000150  bd db f7 9b d9 aa a7 dd  64 88 d7 27 f4 81 c9 17  |........d..'....|
00000160  66 13 ac be 9c 37 6a 94  38 fb cf 3e 6f c8 2a 5c  |f....7j.8..>o.*\|
00000170  70 55 1e eb 7a 51 c5 3e  24 d5 05 a5 3e 4a e1 40  |pU..zQ.>$...>J.@|
00000180  07 6f 41 d2 3a 1c 33 8b  63 b0 9f f6 52 19 02 d0  |.oA.:.3.c...R...|
00000190  db 62 3e 81 c0 9b 6a 8f  92 12 c1 f2 98 d6 15 f1  |.b>...j.........|
000001a0  17 7e 2c be bf 5c 9f 9f  3b 4c f8 b5 f3 40 c0 e2  |.~,..\..;L...@..|
000001b0  e0 82 b1 ff f9 d9 33 ff  b4 9a 51 08 a5 99 00 fe  |......3...Q.....|
000001c0  ff ff 83 fe ff ff 52 9a  f6 08 b0 93 71 0b 00 fe  |......R.....q...|
000001d0  ff ff 05 fe ff ff 02 2e  68 14 c1 c0 7d 00 00 00  |........h...}...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Any and all help will be appreciated.

---

### Post by flick on 2010-08-08
Assuming you can boot into your reinstalled Ubuntu, try updating GRUB :

sudo update-grub

then reboot and see if the GRUB menu shows Mandriva

---

### Post by oldfred on 2010-08-09
Grub2 numbers partitions differently. The os prober is copying the boot stanza from old grub and it then has the incorrect partition.

menuentry "linux (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6dfd1df8-95e9-4769-83e0-755984ed4aad
    linux /boot/vmlinuz BOOT_IMAGE=linux  root=UUID=6dfd1df8-95e9-4769-83e0-755984ed4aad  resume=UUID=e3b2a6ec-ae10-462e-b967-5d926420663b splash=silent vga=788
    initrd [COLOR=Red](hd0,4)[/COLOR]/boot/initrd.img
}

Change this to either nothing as it is not required once set root  is set or (hd0,5)

Copy into 40_custom and run the sudo update-grub. If it works you can then copy all the other stanzas and turn off the osprober so you do not have duplicate entries.

Paste above into this and edit:
gksudo gedit /etc/grub.d/40_custom
sudo update-grub

gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

