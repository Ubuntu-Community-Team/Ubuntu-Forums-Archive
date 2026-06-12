---
title: "Dual Boot Broken after reload of XP"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by carterw65 on 2010-01-14
Hi all,

I am at my wits end with trying to figure out why this machine won't dual boot any more. I had to reload XP and it broke my grub. I have tried everything I can think of to fix it. I have to use SuperGrub cd to boot. I get the grub menu and when I select the kernel it gives an error 17, can't mount selected partition. Also, my sound is broke....again. I upgraded from 9.04 to 9.10 and had to uninstall grub2 to get everything working again. This time I reinstalled grub 2 in hopes it would help, but it did not.

Thanks for any help.:(

---

### Post by jamesbarnhill on 2010-01-14
Did you install XP after Ubuntu?
Did you try [this]("http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/")?
If all else fails try installing Ubuntu again, next to the rest, to see if it'll fix Grub...

---

### Post by carterw65 on 2010-01-14
Originally I installed XP first. But recently needed to reload xp with a clean copy. I tried the grub fix with livecd, didn't work. Same ol' error 17.

---

### Post by wlraider70 on 2010-01-15
down load this script.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
run it from the desktop and post the results. 

someone smarter then I will be along shortly.

---

### Post by presence1960 on 2010-01-15
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by presence1960 on 2010-01-15
> **jamesbarnhill said:**
> Did you install XP after Ubuntu?
Did you try [this]("http://microdotsagamedev.wordpress.com/2007/06/08/repair-your-grub-loader/")?
**_If all else fails try installing Ubuntu again_**, next to the rest, to see if it'll fix Grub...

That will not work for GRUB2, that is for Legacy GRUB 0.97

Bad suggestion to reinstall since your advice can not fix the problem.

---

### Post by carterw65 on 2010-01-15
Here are the results (thanks for all the help!)




```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive [CODE]
```
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda2 and looks 
                       at sector 198573982 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg 
                       /boot/grub/grub.conf /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda3 and 
                       looks at sector 180757878 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda4 starts at sector 250485480.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaafb0b21

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   143,781,749   143,781,687   7 HPFS/NTFS
/dev/sda2         143,781,750   246,260,384   102,478,635  83 Linux
/dev/sda3         246,260,385   250,485,479     4,225,095   5 Extended
/dev/sda5         246,260,448   250,485,479     4,225,032  82 Linux swap / Solaris
/dev/sda4         250,485,480   312,576,704    62,091,225   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8218A85118A845CF" TYPE="ntfs" 
/dev/sda2: UUID="e5c74164-a84a-4f74-a6db-6e42c67f8bbc" TYPE="ext3" 
/dev/sda4: LABEL="" UUID="9692-AA78" TYPE="vfat" 
/dev/sda5: UUID="20f5e5fb-ca7d-4928-a5b3-39f1f249626e" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/carterw65/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=carterw65)
/dev/sr0 on /media/cdrom1 type iso9660 (ro,nosuid,nodev,utf8,user=carterw65)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=========================== sda2/boot/grub/menu.lst: ===========================

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
timeout		15

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
# root		(hd0,0)
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
# kopt=root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro

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

title		Ubuntu 9.10, kernel 2.6.31-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Chainload into GRUB 2
root		(hd0,2)
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root=(hd0,2)
search --no-floppy --fs-uuid --set e5c74164-a84a-4f74-a6db-6e42c67f8bbc
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set e5c74164-a84a-4f74-a6db-6e42c67f8bbc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set e5c74164-a84a-4f74-a6db-6e42c67f8bbc
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set e5c74164-a84a-4f74-a6db-6e42c67f8bbc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set e5c74164-a84a-4f74-a6db-6e42c67f8bbc
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set e5c74164-a84a-4f74-a6db-6e42c67f8bbc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set e5c74164-a84a-4f74-a6db-6e42c67f8bbc
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set e5c74164-a84a-4f74-a6db-6e42c67f8bbc
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set e5c74164-a84a-4f74-a6db-6e42c67f8bbc
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set e5c74164-a84a-4f74-a6db-6e42c67f8bbc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set e5c74164-a84a-4f74-a6db-6e42c67f8bbc
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro single 
	initrd	/boot/initrd.img-2.6.28-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8218a85118a845cf
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

========================== sda2/boot/grub/grub.conf: ==========================

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
timeout		3

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,0)
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
# kopt=root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda2/etc/fstab: ===============================

proc            /proc           proc    defaults        0       0
UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc /               ext3    relatime,errors=remount-ro 0       1
UUID=94215051-5238-47ae-b495-bd2c7f2b4697 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  73.6GB: boot/grub/core.img
  73.6GB: boot/grub/grub.cfg
  73.6GB: boot/grub/grub.conf
  73.6GB: boot/grub/menu.lst
  73.6GB: boot/grub/stage2
  73.6GB: boot/initrd.img-2.6.28-16-generic
  73.6GB: boot/initrd.img-2.6.31-14-generic
  73.6GB: boot/initrd.img-2.6.31-15-generic
  73.6GB: boot/initrd.img-2.6.31-16-generic
  73.6GB: boot/initrd.img-2.6.31-17-generic
  73.6GB: boot/vmlinuz-2.6.28-16-generic
  73.6GB: boot/vmlinuz-2.6.31-14-generic
  73.6GB: boot/vmlinuz-2.6.31-15-generic
  73.6GB: boot/vmlinuz-2.6.31-16-generic
  73.6GB: boot/vmlinuz-2.6.31-17-generic
  73.6GB: initrd.img
  73.6GB: initrd.img.old
  73.6GB: vmlinuz
  73.6GB: vmlinuz.old[/CODE

---

### Post by carterw65 on 2010-01-15
That was whole lotta info. I don't have time this morning to even look at it. I wonder now, do I not have 2 instances of grub trying to run? (grub legacy and grub-pc?)

Those last few lines are interesting though, it says 73.6GB, that is my XP partition.

---

### Post by darkod on 2010-01-15
I don't know what procedures you used, but you made enormous mess. It seems you are using 9.10 which comes with grub2 but:

1. You have grub1 (official number ver 0.97) on the MBR of your hdd, as you can see at the top of the results.
2. Also at the top, where the partitions info is given, you have grub1 on both partitions /dev/sda2 and /dev/sda3. It shouldn't be on neither.

Unfortunately I don't know how to remove grub1 from the partitions, you'll have to wait for presence.

As far as reinstalling grub2 on your MBR with using your ubuntu root partition, /dev/sda2, you need to boot with 9.10 cd, Try Ubuntu option, and in terminal do:

sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Not sure if the above will work with the grub1 you have put on /dev/sda2 and /dev/sda3. Otherwise, that was all you needed to do, those two commands and make SURE you use 9.10 cd, not 9.04 or earlier.

PS. After better look, it seems this was upgrade from 9.04 to 9.10. And that you also upgraded grub1 to grub2, because you have grub.cfg also present. Reinstalling grub2 to the MBR should help in this case too because it seems the grub.cfg file is correct, as long as you get rid of the grub1 from /dev/sda2 and /dev/sda3.

---

### Post by presence1960 on 2010-01-15
I see your problem, your (hdX,Y) in menu,lst which is GRUB Legacy 0.97 is incorrect. it should be (hd0,1). here is how I would attempt to fix it.

Boot your machine and highlight the top kernel. Press "e" on the keyboard. Using your arrow keys navigate to (hd0,2) and change it to (hd0,1). Hit "b" to boot. Once in ubuntu open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst.

Change all the red (hd0,2) to (hd0,1) in :
```

title Ubuntu 9.10, kernel 2.6.31-16-generic
root [COLOR="Red"](hd0,2)[/COLOR]
kernel /boot/vmlinuz-2.6.31-16-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro quiet splash
initrd /boot/initrd.img-2.6.31-16-generic
quiet

title Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
root [COLOR="Red"](hd0,2)[/COLOR]
kernel /boot/vmlinuz-2.6.31-16-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro single
initrd /boot/initrd.img-2.6.31-16-generic

title Ubuntu 9.10, kernel 2.6.31-15-generic
root [COLOR="Red"](hd0,2)[/COLOR]
kernel /boot/vmlinuz-2.6.31-15-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro quiet splash
initrd /boot/initrd.img-2.6.31-15-generic
quiet

title Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
root [COLOR="Red"](hd0,2)[/COLOR]
kernel /boot/vmlinuz-2.6.31-15-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro single
initrd /boot/initrd.img-2.6.31-15-generic

title Ubuntu 9.10, kernel 2.6.31-14-generic
root [COLOR="Red"](hd0,2)[/COLOR]
kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
quiet

title Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root [COLOR="Red"](hd0,0)[/COLOR]
kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro single
initrd /boot/initrd.img-2.6.31-14-generic

title Ubuntu 9.10, kernel 2.6.28-16-generic
root [COLOR="Red"](hd0,2)[/COLOR]
kernel /boot/vmlinuz-2.6.28-16-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro quiet splash
initrd /boot/initrd.img-2.6.28-16-generic
quiet

title Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root [COLOR="Red"](hd0,2)[/COLOR]
kernel /boot/vmlinuz-2.6.28-16-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro single
initrd /boot/initrd.img-2.6.28-16-generic

title Chainload into GRUB 2
root [COLOR="Red"](hd0,2)[/COLOR]
kernel /boot/grub/core.img

title Ubuntu 9.10, memtest86+
root [COLOR="Red"](hd0,2)[/COLOR]
kernel /boot/memtest86+.bin
quiet

```

Click Save on top toolbar & close File. reboot & you should be good to go.

Note: In Legacy GRUB 0.97 and GRUB2 the Y designation in (hdX,Y) starts counting in different manners. In GRUB 0.97 the first partition is 0. In GRUB2 it is 1. Examples:

GRUB 0.97-sda1 = (hd0,0), sda2 = (hd0,1), sda3 = (hd0,2)
GRUB2 - sda1 = (hd0,1), sda2 = (hd0,2), sda3 = (hd0,3)

---

### Post by presence1960 on 2010-01-15
Your GRUB2 entries are incorrect also. From Ubuntu after doing all the above I suggested open a terminal and run ```
sudo update-grub
```

Hopefully that will refresh and correct the entries in grub.cfg
I am not sure if it will because you chose to chainload to GRUB2 rather than just installing it outright. I think that is one of the worst things the devs could have done with GRUB2. Either we are using it or we aren't. Now you have people with both Legacy GRUB and GRUB2 installed on their systems and a unique set of problems. Come on Ubuntu we can't be all things to everyone. Let's do one thing well and stick with that!

---

### Post by presence1960 on 2010-01-15
Carter,

Just a suggestion here. Next time do not do a dist upgrade as a lot of them cause problems and wind up being more work to fix the mess than just doing a clean install. When you get time peruse back through the forum and note that at every release there are a lot of threads about dist-upgrades messing up. You can do a clean install and have all your packages and settings saved for you. Here is how:

Back up your /home. Use the first part of [this how to]("http://ubuntuforums.org/showpost.php?p=7157175&postcount=5") in order to save all your packages to a file. Move that file with your backup of /home.

Restore the /home back up. Now use the second part of that "how to" to restore all your packages. Your settings for your software will be retained when you start an application because those settings are in /home which you had backed up and restored.

Note the only packages that won't be reinstalled on the clean install are third party packages not in the ubuntu repositories or packages you compiled from source.

---

### Post by carterw65 on 2010-01-15
Presence, that fixed my boot issue.....duh, I thought I was telling it the right drive. I also had the 31.17-generic kernel that I knew wasn't showing. I put it in menu.lst and now my sound is restored. I am going to try to uninstall grub now and update to grub2.

Thanks everyone for all the help. I will let you know how it goes.

---

### Post by carterw65 on 2010-01-15
Well the transition from grub to grub2 went very well, everything is working and looking good.

Presence, one more question. How do you usually go about backing up the /home directory? I should really do a clean install like you suggested anyway. I have done a lot of fiddling with things to try and figure stuff out, for instance, python. In the process I have a bunch of stuff (packages, files etc) that is just taking up space.

Thanks again for the help.

---

