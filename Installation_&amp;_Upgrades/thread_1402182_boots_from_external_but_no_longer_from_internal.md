---
title: "boots from external but no longer from internal"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by jimfl on 2010-02-08
I have Ubuntu 9.10 running as a dual boot with Vista on my internal hard drive. I just added an external hard drive on which I installed 9.10 also. I set the boot order to 1) CD, 2) removable drive, 3) internal drive. This worked fine and booted from the new external drive.

However, when I shut down and disconnected the external drive, I got this message at my next startup:
Grub loading.
error: no such disk
grub rescue>

What do I need to do so that the system will boot from the internal hard drive when the external is not connected?

Thanks!

---

### Post by raymondh on 2010-02-08
> **jimfl said:**
> I have Ubuntu 9.10 running as a dual boot with Vista on my internal hard drive. I just added an external hard drive on which I installed 9.10 also. I set the boot order to 1) CD, 2) removable drive, 3) internal drive. This worked fine and booted from the new external drive.

However, when I shut down and disconnected the external drive, I got this message at my next startup:
Grub loading.
error: no such disk
grub rescue>

What do I need to do so that the system will boot from the internal hard drive when the external is not connected?

Thanks!

Hi,

Let's see how your system is set-up.  Kindly download and run the bootinfoscript and paste the results.txt back here.  To make it easier for the forum to read, highlight the results.txt file and click on the # sign amongst the tools above in the reply box.

[Instructions here]("http://ubuntuforums.org/showpost.php?p=8104352&postcount=1"). 

Thanks

Raymond

EDIT : will be back in about an hour :)

---

### Post by jimfl on 2010-02-08
Hello Raymond,

Thank you for replying and the instructions. The Results.txt file is attached. Oops, the file is 4K too long. I'm not familiar with the # option, but here goes:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=4dba10f5-8fde-4de9-9700-ef59010ba52d)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
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
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk /IO.SYS /MSDOS.SYS

sda3/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2              98,304    21,069,823    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,069,824   378,941,431   357,871,608   7 HPFS/NTFS
/dev/sda4         378,957,285   488,279,609   109,322,325   5 Extended
/dev/sda5         378,957,348   483,717,149   104,759,802  83 Linux
/dev/sda6         483,717,213   488,279,609     4,562,397  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01f1006c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    22,346,414    22,346,352   7 HPFS/NTFS
/dev/sdb2          22,346,415   488,392,064   466,045,650   5 Extended
/dev/sdb5          22,346,478   470,302,874   447,956,397  83 Linux
/dev/sdb6         470,302,938   488,392,064    18,089,127  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       f95eaa0d-9fe5-40a9-a9cc-2cf9b9285e9c   ext3                                     
/dev/sda1        07D7-0C09                              vfat       DellUtility                   
/dev/sda2        1216CA4516CA2995                       ntfs       RECOVERY                      
/dev/sda3        6282CDFF82CDD825                       ntfs       OS                            
/dev/sda5        67ddfe32-4369-435c-ad33-da0680634089   ext3                                     
/dev/sda6        ed8db7b9-4ce7-4da8-b84f-5ea58a5691a8   swap                                     
/dev/sdb1        8C929C10929BFD40                       ntfs                                     
/dev/sdb5        4dba10f5-8fde-4de9-9700-ef59010ba52d   ext4                                     
/dev/sdb6        13590e7b-6828-4f38-802e-8e7e07dbf8bb   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/8C929C10929BFD40  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5        /media/67ddfe32-4369-435c-ad33-da0680634089 ext3       (rw,nosuid,nodev,uhelper=devkit)


==================== sda3/ubuntu/disks/boot/grub/menu.lst: ====================

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
# kopt=root=UUID=6282CDFF82CDD825 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=6282CDFF82CDD825 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=6282CDFF82CDD825 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6282CDFF82CDD825 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6282CDFF82CDD825 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista (loader)
rootnoverify    (hd0,2)
savedefault
chainloader    +1


======================== sda3/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

=================== sda3: Location of files loaded by Grub: ===================


  10.7GB: ubuntu/disks/boot/grub/menu.lst
  10.7GB: ubuntu/disks/boot/initrd.img-2.6.28-11-generic
  10.7GB: ubuntu/disks/boot/initrd.img-2.6.28-15-generic
  10.7GB: ubuntu/disks/boot/vmlinuz-2.6.28-11-generic
  10.7GB: ubuntu/disks/boot/vmlinuz-2.6.28-15-generic

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

=========================== sda5/boot/grub/menu.lst: ===========================

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
timeout        10

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
# kopt=root=UUID=67ddfe32-4369-435c-ad33-da0680634089 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=67ddfe32-4369-435c-ad33-da0680634089

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
# defoptions=quiet splash quiet

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

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        67ddfe32-4369-435c-ad33-da0680634089
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=67ddfe32-4369-435c-ad33-da0680634089 ro quiet splash quiet 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        67ddfe32-4369-435c-ad33-da0680634089
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=67ddfe32-4369-435c-ad33-da0680634089 ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, memtest86+
uuid        67ddfe32-4369-435c-ad33-da0680634089
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista (loader)
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=67ddfe32-4369-435c-ad33-da0680634089 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ed8db7b9-4ce7-4da8-b84f-5ea58a5691a8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hda1  /media/windows_ntfs  ntfs  nls=utf8,umask=0222  0  0

=================== sda5: Location of files loaded by Grub: ===================


 194.0GB: boot/grub/menu.lst
 194.0GB: boot/grub/stage2
 194.0GB: boot/initrd.img-2.6.31-17-generic
 194.0GB: boot/vmlinuz-2.6.31-17-generic
 194.0GB: initrd.img
 194.0GB: vmlinuz

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
search --no-floppy --fs-uuid --set 4dba10f5-8fde-4de9-9700-ef59010ba52d
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 4dba10f5-8fde-4de9-9700-ef59010ba52d
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 4dba10f5-8fde-4de9-9700-ef59010ba52d
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb5 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 6282cdff82cdd825
    chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 67ddfe32-4369-435c-ad33-da0680634089
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=67ddfe32-4369-435c-ad33-da0680634089 ro quiet splash quiet
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 67ddfe32-4369-435c-ad33-da0680634089
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=67ddfe32-4369-435c-ad33-da0680634089 ro single
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 67ddfe32-4369-435c-ad33-da0680634089
    linux /boot/memtest86+.bin 
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
UUID=4dba10f5-8fde-4de9-9700-ef59010ba52d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=13590e7b-6828-4f38-802e-8e7e07dbf8bb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```


Jim

---

### Post by leclerc65 on 2010-02-08
I would avoid situation like this by clicking on 'Advanced' (the last step before the real install) and put the bootloader on the external drive.

---

### Post by raymondh on 2010-02-09
[COLOR="Red"]Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=4dba10f5-8fde-4de9-9700-ef59010ba52d)/boot/grub.[/COLOR]

[COLOR="Red"]/dev/[COLOR="Blue"]sdb5[/COLOR]        4dba10f5-8fde-4de9-9700-ef59010ba52d   ext4[/COLOR]   

It seems that GRUB2 has 'split'.  It is installed in the MBR of sda (your internal) but looks for Ubuntu in the external.

Let's try to get GRUB2 to look for internal-ubuntu (sda5).  For me, I would just re-install GRUB2.  Detach the external.  Boot into the liveCD and access a terminal.  Type and enter one at a time:

```
sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
sudo grub-install --root-directory=/media/sda5 /dev/sda
```

Close terminal, exit the live session (liveCd) and reboot. If you don't see your windows install and once in Ubuntu-internal, access a terminal and 

```
sudo update-grub2
```

Next step involves the external which you want to boot only if you have it plugged, right?  Try installing GRUB2 in the MBR of the external as well. Of course, attach the external.

```
sudo grub-install /dev/sdb
```

Sorry for the seemingly rush.  Am taking a quick break from helping my son finish his school project.

Here are links for your reference

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Raymond

---

### Post by jimfl on 2010-02-09
Hello Raymond,

I followed your directions as far as the first three lines of code, which seemed to work ok. I got this result: 

     Installation finished. No error reported.
     This is the contents of the device map  /media/sda5/boot/grub/device.map
      (hd0)    /dev/sda

However, when I rebooted I couldn't get to a terminal to complete your instructions because this appeared:

          GNU GRUB Version 1.97 beta4

    [Minimal BASH-like line editing is supported...]
    grub>

I tried rearranging the boot order of the internal and external drives but still only got the above GNU GRUB screen.  I also tried reading the links you sent but ended up getting massively confused.

I'm including this fdisk output in case it might mean more to you than it does to me.

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7        1312    10485760    7  HPFS/NTFS
/dev/sda3   *        1312       23589   178935804    7  HPFS/NTFS
/dev/sda4           23590       30394    54661162+   5  Extended
/dev/sda5           23590       30110    52379901   83  Linux
/dev/sda6           30111       30394     2281198+  82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01f1006c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1391    11173176    7  HPFS/NTFS
/dev/sdb2            1392       30401   233022825    5  Extended
/dev/sdb5            1392       29275   223978198+  83  Linux
/dev/sdb6           29276       30401     9044563+  82  Linux swap / Solaris

Jim
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by presence1960 on 2010-02-09
scrap what was here you have legacy grub on your internal disk and GRUB2 on the external disk. see below post. Sorry for the inconvenience. That is why the commands didn't work Raymondh and I gave you.

---

### Post by presence1960 on 2010-02-09
Bag that last post I made. I  just noticed you have GRUB Legacy on sda and GRUB2 on sdb. To fix the sda (internal) MBR you are going to need a 9.04 Live CD. Boot that with the external unplugged, choose "try ubuntu without any changes" & when the desktop loads open a terminal and do this:

1. Type sudo grub. Should get text of which last line is grub>
2. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)". 
   Use whatever your computer spits out for the following lines.
3. Type "root (hd0,4)"
4. Type "setup (hd0)", to install GRUB to MBR
5. Quit grub by typing "quit".
6. Reboot and remove the bootable CD.

Boot into Ubuntu and then windows to make sure that GRUB menu works.

If you want GRUB2 on MBR of external so your 9.10 with grub.cfg boots when the external is plugged in then you have to put GRUB2 on MBR of external disk. Boot the 9.10 Live CD with the external disk plugged in and choose try ubuntu without any changes. When the desktop loads open a terminal and run ```
sudo mount /dev/sdb5 /mnt
``` Then from terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
``` Reboot without the Live Cd and make sure the external is set to boot before the internal in the device boot order in BIOS. Boot into Ubuntu (on external) and open a terminal and run ```
echo "SET grub-pc/install_devices /dev/sdb" | sudo debconf-communicate

```This will insure any grub-pc (GRUB2) updates run from the external disk go to the MBR of the external disk not MBR of sda.

---

### Post by raymondh on 2010-02-09
sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   [COLOR="Red"]/boot/grub/menu.lst /etc/fstab[/COLOR]

Thanks presence ..... :)

Raymond

---

### Post by jimfl on 2010-02-09
Hello Raymond and presence,

I've started the download of 9.04. However, I'm running off the 9.10 Live CD as I can't boot from either hard drive, and I haven't figured out how to burn 9.04 onto a CD because my computer won't let me eject the 9.10 Live CD. If there's no way of forcing it to eject, I may be able to get a 9.04 CD from a friend this weekend.

Jim

---

### Post by raymondh on 2010-02-09
> **jimfl said:**
> Hello Raymond and presence,

I've started the download of 9.04. However, I'm running off the 9.10 Live CD as I can't boot from either hard drive, and I haven't figured out how to burn 9.04 onto a CD because my computer won't let me eject the 9.10 Live CD. If there's no way of forcing it to eject, I may be able to get a 9.04 CD from a friend this weekend.

Jim

Sorry Jim ..... you'll need to check the manuals for a 'manual eject'.  If you wish, post back your system (manufacturer & model) and I can quick check for you.

on my dell, there's a little hole beside the tray that I can push a thin paper clip through to force the eject.

Raymond

---

### Post by jimfl on 2010-02-09
Raymond, it's a Dell Inspiron 530. I found the eject hole and pushed a paper clip into it. It started to eject the drawer, but only about a 1/16 of an inch--not far enough to grab onto it, plus it pops back in within a second or so.

I'll just run off the Live CD until the weekend, get a 9.04 CD from a friend, and resume your instructions from that point.

I really appreciate all of your efforts. 

Jim

---

### Post by jimfl on 2010-02-12
It works! It works!

Thanks a million to Raymond and presence. I didn't have to wait to get a 9.04 LiveCD because I found this in one of the forums that let me boot into my internal drive from the GRUB prompt:

set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot

That booted from my internal and from there I just followed your last set of instructions.

An unexpected bonus is that when my external drive is installed, GRUB still gives me the option of booting from the internal.

Thanks again for all the help.:D

Jim

---

### Post by presence1960 on 2010-02-12
> **jimfl said:**
> It works! It works!

Thanks a million to Raymond and presence. I didn't have to wait to get a 9.04 LiveCD because I found this in one of the forums that let me boot into my internal drive from the GRUB prompt:

set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot

That booted from my internal and from there I just followed your last set of instructions.

An unexpected bonus is that when my external drive is installed, GRUB still gives me the option of booting from the internal.

Thanks again for all the help.:D

Jim

Glad you got it working! Enjoy Ubuntu. Sorry I haven't been around the past couple of days, but we just got 44" of snow in 5 days. Have been busy digging myself and my neighbors out.

---

### Post by raymondh on 2010-02-12
glad as well.

---

