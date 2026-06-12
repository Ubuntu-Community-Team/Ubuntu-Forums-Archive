---
title: "Boots to grub post grub  reinstall"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by sinurge on 2010-02-16
When i boot my computer it falls back to the grub prompt

I installed Fedora 11 on my computer already running Jaunty + Vista in dual boot. I did not like fedora due to its nvdia drivers issue hence removed it and deleted the partition.

post that grub failed for the first time, i reinstalled it - it failed again. i was able to boot using 
rootnoverify (hd0,2)
root (hd0,2)
chainloader +1
boot 

but everytime its boots it falls to grub prompt 

today i again installed it again. post that i am unable to boot even with the above command.

btw when i was able to boot - when tried to mount hte windows partition it never allowed me giving multiple errors, i used the ntfsfix program but that showed me an error and asked me to run chkdsk , isn't this a windows command. 

Also - fdisk -l , tells me the the partitions and drives are not in the same order.

Please help - am contemplating - loading thru vista fixing mbr and then installing grub-legacy again.

---

### Post by oldfred on 2010-02-17
You need to reinstall grub and also use the Vista repair console to run the chkdsk.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by sinurge on 2010-02-17
Thanks!!!

I have the installation DVD when i tried to boot from there my HDD and partitions were not detected by windows vista. C: returns an errors and bootrec does not know the disk to fix

I deleted the vista partition by booting from the ubuntu disk and then reinstalled grub, but even then on reboot it falls back to grub.

Not sure what is the problem. 

Once falling to grub i got the the os by running roonov....root...chainloader +1, boot command which brought the os choosing screen in grub. when i chose vista it threw me the correct bootmgr missing errors. 

As i am getting to the os choosing screen my assumption is that it is grub boot stage2. When i install grub btw there are 2 warnings, "could not  efs..stage1 ..this is not Fatal". I thought i could just delete these files and allow grub to install them fresh. but i dont think i can delete them.

---

### Post by darkod on 2010-02-18
Your first mistake to start with was letting fedora install its grub too. Once you already had ubuntu (linux) on your computer, you DON'T need to install grub with any subsequent linux installs. If you kept your ubuntu grub, deleting the fedora partition wouldn't have broken it.

You better run the boot info script because it sounds like you have grub all over the place, not only on MBRs but on partitions too. You can download it in my signature, move it on desktop for example, and run it with:

sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with loads info about your boot process. Copy the content here and wrap it in CODE tags for easier reading.

You can do all of that from the live desktop too.

---

### Post by sinurge on 2010-02-20
the output is below but i did one more mistake, in doing some self help i installed mint os helena as well.. and there is more **** now 

<code>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks at sector 253698 
    on boot drive #1 for the stage2 file. A stage2 file is at this location on 
    /dev/sda. Stage2 looks on partition #6 for /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 905. But according to the info from fdisk, 
                       sda5 starts at sector 70799360.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 8 Helena - x64 
                       Edition
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda3 and 
                       looks at sector 37357895 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41958f33

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   276,494,714   276,478,650   f W95 Ext d (LBA)
/dev/sda5          70,799,360   276,492,287   205,692,928   7 HPFS/NTFS
/dev/sda6              16,191    70,798,454    70,782,264  83 Linux
/dev/sda2    *    276,496,384   378,896,383   102,400,000   7 HPFS/NTFS
/dev/sda3         378,896,384   468,595,602    89,699,219  83 Linux
/dev/sda4         468,599,985   488,392,064    19,792,080  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        246650367783FCBF                       ntfs                                     
/dev/sda3        9a7ae8b8-49cd-4de0-8df1-9125808dfb51   ext3                                     
/dev/sda4        c34ba65e-626d-469c-bab8-919dcd4d9e32   swap                                     
/dev/sda5        54A0B4D1A0B4BAB6                       ntfs       New Volume                    
/dev/sda6        b52c0685-148d-4a4d-ba2d-514bd3666d25   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda5        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /media/disk              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6        /media/disk-1            ext3       (rw,nosuid,nodev,uhelper=hal)


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b52c0685-148d-4a4d-ba2d-514bd3666d25 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b52c0685-148d-4a4d-ba2d-514bd3666d25

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

title        Linux Mint 8 Helena - x64 Edition, kernel 2.6.31-14-generic
uuid        b52c0685-148d-4a4d-ba2d-514bd3666d25
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=b52c0685-148d-4a4d-ba2d-514bd3666d25 ro pci=nomsi quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Linux Mint 8 Helena - x64 Edition, kernel 2.6.31-14-generic (recovery mode)
uuid        b52c0685-148d-4a4d-ba2d-514bd3666d25
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=b52c0685-148d-4a4d-ba2d-514bd3666d25 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        b52c0685-148d-4a4d-ba2d-514bd3666d25
kernel        /boot/grub/core.img

title        Linux Mint 8 Helena - x64 Edition, memtest86+
uuid        b52c0685-148d-4a4d-ba2d-514bd3666d25
kernel        /boot/memtest86+.bin
quiet

title        Ubuntu 9.04, kernel 2.6.28-18-generic
uuid        9a7ae8b8-49cd-4de0-8df1-9125808dfb51
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=9a7ae8b8-49cd-4de0-8df1-9125808dfb51 ro pci=nomsi quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set b52c0685-148d-4a4d-ba2d-514bd3666d25
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set b52c0685-148d-4a4d-ba2d-514bd3666d25
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-14-generic (/dev/sda6)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set b52c0685-148d-4a4d-ba2d-514bd3666d25
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b52c0685-148d-4a4d-ba2d-514bd3666d25 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set b52c0685-148d-4a4d-ba2d-514bd3666d25
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b52c0685-148d-4a4d-ba2d-514bd3666d25 ro single 
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
menuentry "Ubuntu 9.04, kernel 2.6.28-18-generic (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 9a7ae8b8-49cd-4de0-8df1-9125808dfb51
    linux /boot/vmlinuz-2.6.28-18-generic root=UUID=9a7ae8b8-49cd-4de0-8df1-9125808dfb51 ro pci=nomsi quiet splash
    initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode) (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 9a7ae8b8-49cd-4de0-8df1-9125808dfb51
    linux /boot/vmlinuz-2.6.28-18-generic root=UUID=9a7ae8b8-49cd-4de0-8df1-9125808dfb51 ro pci=nomsi single
    initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-17-generic (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 9a7ae8b8-49cd-4de0-8df1-9125808dfb51
    linux /boot/vmlinuz-2.6.28-17-generic root=UUID=9a7ae8b8-49cd-4de0-8df1-9125808dfb51 ro pci=nomsi quiet splash
    initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode) (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 9a7ae8b8-49cd-4de0-8df1-9125808dfb51
    linux /boot/vmlinuz-2.6.28-17-generic root=UUID=9a7ae8b8-49cd-4de0-8df1-9125808dfb51 ro pci=nomsi single
    initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 9a7ae8b8-49cd-4de0-8df1-9125808dfb51
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=9a7ae8b8-49cd-4de0-8df1-9125808dfb51 ro pci=nomsi quiet splash
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 9a7ae8b8-49cd-4de0-8df1-9125808dfb51
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=9a7ae8b8-49cd-4de0-8df1-9125808dfb51 ro pci=nomsi single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 9a7ae8b8-49cd-4de0-8df1-9125808dfb51
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=b52c0685-148d-4a4d-ba2d-514bd3666d25 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=c34ba65e-626d-469c-bab8-919dcd4d9e32 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  19.1GB: boot/grub/core.img
  19.1GB: boot/grub/grub.cfg
  19.0GB: boot/grub/menu.lst
  19.1GB: boot/grub/stage2
  19.1GB: boot/initrd.img-2.6.31-14-generic
  19.0GB: boot/vmlinuz-2.6.31-14-generic
  19.1GB: initrd.img
  19.0GB: vmlinuz

=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=9a7ae8b8-49cd-4de0-8df1-9125808dfb51 ro pci=nomsi

## default grub root device
## e.g. groot=(hd0,0)
# groot=9a7ae8b8-49cd-4de0-8df1-9125808dfb51

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

title        Ubuntu 9.04, kernel 2.6.28-18-generic
uuid        9a7ae8b8-49cd-4de0-8df1-9125808dfb51
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=9a7ae8b8-49cd-4de0-8df1-9125808dfb51 ro pci=nomsi quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid        9a7ae8b8-49cd-4de0-8df1-9125808dfb51
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=9a7ae8b8-49cd-4de0-8df1-9125808dfb51 ro pci=nomsi  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, kernel 2.6.28-17-generic
uuid        9a7ae8b8-49cd-4de0-8df1-9125808dfb51
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=9a7ae8b8-49cd-4de0-8df1-9125808dfb51 ro pci=nomsi quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid        9a7ae8b8-49cd-4de0-8df1-9125808dfb51
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=9a7ae8b8-49cd-4de0-8df1-9125808dfb51 ro pci=nomsi  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        9a7ae8b8-49cd-4de0-8df1-9125808dfb51
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9a7ae8b8-49cd-4de0-8df1-9125808dfb51 ro pci=nomsi quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        9a7ae8b8-49cd-4de0-8df1-9125808dfb51
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9a7ae8b8-49cd-4de0-8df1-9125808dfb51 ro pci=nomsi  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        9a7ae8b8-49cd-4de0-8df1-9125808dfb51
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=9a7ae8b8-49cd-4de0-8df1-9125808dfb51 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda4 :
UUID=c34ba65e-626d-469c-bab8-919dcd4d9e32 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda5 /media/Data ntfs-3g defaults,locale=en_IN 0 0

=================== sda3: Location of files loaded by Grub: ===================


 221.0GB: boot/grub/menu.lst
 221.0GB: boot/grub/stage2
 220.6GB: boot/initrd.img-2.6.28-11-generic
 220.6GB: boot/initrd.img-2.6.28-17-generic
 220.5GB: boot/initrd.img-2.6.28-18-generic
 220.6GB: boot/vmlinuz-2.6.28-11-generic
 220.6GB: boot/vmlinuz-2.6.28-17-generic
 220.6GB: boot/vmlinuz-2.6.28-18-generic
 220.5GB: initrd.img
 220.6GB: initrd.img.old
 220.6GB: vmlinuz
 220.6GB: vmlinuz.old 
</code>

---

