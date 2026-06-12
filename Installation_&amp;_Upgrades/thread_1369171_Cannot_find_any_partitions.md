---
title: "Cannot find any partitions"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by mrlabor1 on 2009-12-31
Hello,
 
I am brand new at trying to work through fixing these things on my own. I have had Ubuntu 8.04 on my laptop for a year now. It was shipped from Dell with Hardy pre installed. I had to dual boot with XP for Autocad. The most recent issue is I was not sure about moving up to 9.04 or 9.10 or mint. So I sued my laptop (inspiron 1525) to pout both 9.04 and mint 8 on an external usb Hard Drive. It worked great I could boot between the 4 operating systems. I then took my laptop out and could not boot. I could boot using a live CD. I could then see all the partitions and access all data, sloooowwwwly. I got home plugged in the external usb and all the operating systems showed up. 
 
What I have figured out is there is something wrong with my Master Boot Record. I have Ultimate boot CD and have looked at a few options with it. I also still have my XP CD and have looked at options with it. BOTH CD's when I am in those specific menus and choose the option I THINK is what is needed to repair, a warning shows up. DANGER DANGER! don't do this unless you really know what you are doing. You could permanantly erase all data and never be able to use this drive again! 
 
So I chicken out and look else where. 
 
I was told about "grub-install" I have tried a few different variations of the command even "fdisk -l" the return is usually "no disk or partition exists".
 
excuse the "book" but this is my first post and I wanted to make sure I wasn't leaving any info out. 
 
Thanks and please help
 
Lee:confused:

---

### Post by oldfred on 2009-12-31
With your external plugged in run this script. It will show where grub is and how your system is set up.  If from one of your working installs it will download to either downloads or the desktop:

Boot Info Script 0.42 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions:  louieb's
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 
or as example if on desktop or  downloads directory from liveCD download:
sudo bash ~/Desktop/boot_info_script*.sh
or depending on where it downloaded
sudo bash ~/Downloads/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here, it can be big. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text, to make it easier to view.

---

### Post by mrlabor1 on 2009-12-31
Ok,  I highlighted all and clicked on the # button.  I didn't look like much changed.  Anyways.  Here is the requested file.  You were right it is big!  I hope it lets you know what you need to explain to me what in the world I did to mess things up!  More so how to repair mistake!

Thanks for the quick reply!!  

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

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

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 8 Helena - Main 
                       Edition
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe0000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   116,053,559   116,053,497   7 HPFS/NTFS
/dev/sda2         116,053,560   234,436,544   118,382,985   5 Extended
/dev/sda5         116,053,623   229,504,589   113,450,967  83 Linux
/dev/sda6         229,504,653   234,436,544     4,931,892  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003cef0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   302,744,924   302,744,862   7 HPFS/NTFS
/dev/sdb2         302,744,925   976,768,064   674,023,140   5 Extended
/dev/sdb5         559,479,753   930,581,189   371,101,437  83 Linux
/dev/sdb6         970,808,013   976,768,064     5,960,052  82 Linux swap / Solaris
/dev/sdb7         302,745,051   553,519,574   250,774,524  83 Linux
/dev/sdb8         553,519,638   559,479,689     5,960,052  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="52F0137DF013670F" TYPE="ntfs" 
sda5: UUID="2470df3d-c9a1-4508-bb0d-ca24d261b036" TYPE="ext3" 
sda6: UUID="c5f665e6-4c72-4654-8898-1dd57191088b" TYPE="swap" 
sdb1: UUID="26382A3E382A0CFD" LABEL="Beavers Server" TYPE="ntfs" 
sdb5: UUID="714b24e8-2f64-4c6e-9e48-822f1f9f2464" TYPE="ext4" 
sdb6: UUID="7aac29ee-90d7-4196-832a-0d1c30f2f2ee" TYPE="swap" 
sdb7: UUID="d381b39a-2dc9-46a8-8e98-53a9d16d55b3" TYPE="ext3" 
sdb8: UUID="324da49a-fc69-4b84-a765-b14de2b0769b" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/mmcblk0p1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda5 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda1 on /media/disk-2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb7 on /media/disk-3 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/Beavers Server type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5 on /media/disk-4 type ext4 (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin 

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
# kopt=root=UUID=2470df3d-c9a1-4508-bb0d-ca24d261b036 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2470df3d-c9a1-4508-bb0d-ca24d261b036

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        2470df3d-c9a1-4508-bb0d-ca24d261b036
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=2470df3d-c9a1-4508-bb0d-ca24d261b036 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        2470df3d-c9a1-4508-bb0d-ca24d261b036
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=2470df3d-c9a1-4508-bb0d-ca24d261b036 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        2470df3d-c9a1-4508-bb0d-ca24d261b036
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root



=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=2470df3d-c9a1-4508-bb0d-ca24d261b036 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=c5f665e6-4c72-4654-8898-1dd57191088b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  97.6GB: boot/grub/menu.lst
  96.3GB: boot/grub/stage2
  96.3GB: boot/initrd.img-2.6.27-11-generic
  97.7GB: boot/initrd.img-2.6.27-14-generic
 102.5GB: boot/initrd.img-2.6.27-15-generic
  97.6GB: boot/initrd.img-2.6.27-16-generic
  96.4GB: boot/initrd.img-2.6.27-7-generic
  96.3GB: boot/vmlinuz-2.6.27-11-generic
  97.6GB: boot/vmlinuz-2.6.27-14-generic
  91.8GB: boot/vmlinuz-2.6.27-15-generic
  97.6GB: boot/vmlinuz-2.6.27-16-generic
  96.4GB: boot/vmlinuz-2.6.27-7-generic
  97.6GB: initrd.img
 102.5GB: initrd.img.old
  97.6GB: vmlinuz
  91.8GB: vmlinuz.old

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
search --no-floppy --fs-uuid --set 714b24e8-2f64-4c6e-9e48-822f1f9f2464
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
set root=(hd1,5)
search --no-floppy --fs-uuid --set 714b24e8-2f64-4c6e-9e48-822f1f9f2464
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
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (/dev/sdb5)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 714b24e8-2f64-4c6e-9e48-822f1f9f2464
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=714b24e8-2f64-4c6e-9e48-822f1f9f2464 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 714b24e8-2f64-4c6e-9e48-822f1f9f2464
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=714b24e8-2f64-4c6e-9e48-822f1f9f2464 ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 52f0137df013670f
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 2470df3d-c9a1-4508-bb0d-ca24d261b036
    linux /boot/vmlinuz-2.6.27-7-generic root=UUID=2470df3d-c9a1-4508-bb0d-ca24d261b036 ro quiet splash
    initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 2470df3d-c9a1-4508-bb0d-ca24d261b036
    linux /boot/vmlinuz-2.6.27-7-generic root=UUID=2470df3d-c9a1-4508-bb0d-ca24d261b036 ro single
    initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 2470df3d-c9a1-4508-bb0d-ca24d261b036
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
UUID=714b24e8-2f64-4c6e-9e48-822f1f9f2464 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=7aac29ee-90d7-4196-832a-0d1c30f2f2ee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 291.3GB: boot/grub/core.img
 291.5GB: boot/grub/grub.cfg
 287.0GB: boot/initrd.img-2.6.31-14-generic
 287.0GB: boot/vmlinuz-2.6.31-14-generic
 287.0GB: initrd.img
 287.0GB: vmlinuz

=========================== sdb7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d381b39a-2dc9-46a8-8e98-53a9d16d55b3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d381b39a-2dc9-46a8-8e98-53a9d16d55b3

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

title        Ubuntu 9.04, kernel 2.6.28-17-generic
uuid        d381b39a-2dc9-46a8-8e98-53a9d16d55b3
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=d381b39a-2dc9-46a8-8e98-53a9d16d55b3 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid        d381b39a-2dc9-46a8-8e98-53a9d16d55b3
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=d381b39a-2dc9-46a8-8e98-53a9d16d55b3 ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d381b39a-2dc9-46a8-8e98-53a9d16d55b3
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d381b39a-2dc9-46a8-8e98-53a9d16d55b3 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d381b39a-2dc9-46a8-8e98-53a9d16d55b3
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d381b39a-2dc9-46a8-8e98-53a9d16d55b3 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d381b39a-2dc9-46a8-8e98-53a9d16d55b3
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=2470df3d-c9a1-4508-bb0d-ca24d261b036 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=2470df3d-c9a1-4508-bb0d-ca24d261b036 ro single 
initrd        /boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 8.10, memtest86+ (on /dev/sda5)
root        (hd0,4)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Linux Mint 8 Helena, linux 2.6.31-14-generic (/dev/sdb5) (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=714b24e8-2f64-4c6e-9e48-822f1f9f2464 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb5.
title        Linux Mint 8 Helena, linux 2.6.31-14-generic (recovery mode) (on /dev/sdb5)
root        (hd1,4)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=714b24e8-2f64-4c6e-9e48-822f1f9f2464 ro single 
initrd        /boot/initrd.img-2.6.31-14-generic
savedefault
boot


=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb7 during installation
UUID=d381b39a-2dc9-46a8-8e98-53a9d16d55b3 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=324da49a-fc69-4b84-a765-b14de2b0769b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb7: Location of files loaded by Grub: ===================


 156.3GB: boot/grub/menu.lst
 156.3GB: boot/grub/stage2
 156.3GB: boot/initrd.img-2.6.28-11-generic
 156.3GB: boot/initrd.img-2.6.28-17-generic
 156.4GB: boot/vmlinuz-2.6.28-11-generic
 156.4GB: boot/vmlinuz-2.6.28-17-generic
 156.3GB: initrd.img
 156.3GB: initrd.img.old
 156.4GB: vmlinuz
 156.4GB: vmlinuz.old
```[/code]

---

### Post by oldfred on 2009-12-31
The copy of grub legacy you have in the MBR of sda points to the 9.04 installed on sdb. That is why you have to have the external sdb installed for it to work.

You have a couple of choices since you have several operating systems and two drives. I always like to have each drive have a operating system and that operating system set up in the MBR of that drive. I like to have grub/ubuntu on my first drive since it also boots other systems easily but windows is not so good about that.

You can either install windows or your grub from 8.10 to the MBR of sda. That way when the external sdb is not installed you can still boot. If you just want windows install that, if you want a choice install grub from sda5.

The reference to sda and sdb need to be carefully watched to make sure when you plug in the external that they do not change.

For the external you have mint and it has grub2 files in sdb6. You also have 9.04 in sdb7 with grub legacy files. I would install grub2 to the sdb MBR and use that for booting when the external is plugged in. Grub2 is very good at finding other operating systems and should easily find all the systems. I assume mint's grub2 is like Ubuntus.

Since you have a working system with the external plugged in you can just boot into the system you want to install to the MBR of that drive and reinstall grub to that MBR.

Boot into mint, if it has the full grub2 commands this should let you install grub2 to the MBR of the sdb.
reinstalls grub and allows choice of which drive to install to. Choose  as boot drive sdb when asked

sudo dpkg-reconfigure grub-pc

Then boot into 8.10 if you want the grub in sda or use your windows repair disk to reinstall windows to the MBR.
#reset grub boot
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,4)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition
setup (hd0)

As long as you can boot into your system you should not need the liveCD, but just incase this has instructions. Also instructions if you want the windows boot in the MBR.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You can also set your external as the first drive to boot then mint's grub will be incontrol. If not plugged in the MBR in sda will be in control.

---

### Post by mrlabor1 on 2009-12-31
Thank you again for the quick response and the very detailed explanation! It made sense after I read it through for the third time.  I will let you know if it works after the New Year!  

Until then,
Thanks and have a Happy New Year!

Lee

---

### Post by mrlabor1 on 2010-01-05
Oldfred,

Thanks for the help.  It worked beautifully.  Sorry I took so long to get back.  I was nervous and had to make super sure I knew and understood everything completely before I was to act.  (A day of hesitation trumps a lifetime of what did I loose?)  I want to say how great you guys have been.  Also how you have inspired me to be an active member in the Ubuntu community.  Once I learn something worth passing on I want to help others like you have helped me.  

Thanks again,

Mrlabor1

---

