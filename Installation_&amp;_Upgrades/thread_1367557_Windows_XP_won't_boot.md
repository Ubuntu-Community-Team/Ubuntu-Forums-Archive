---
title: "Windows XP won't boot"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by rugbywarrior on 2009-12-29
Hello,

I'm not sure whats going on.  I have been fighting with grub for weeks since i tried to dualboot windows after xubuntu.  I finally reformatted xubuntu and reinstalled it in order to dual boot.  Grub works just fine but when I choose to start windows, the screen turns black with that little white thingy in the top corner and just stays like that.  i ran boot_info_script and this is what it said:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 513790830. But according to the info from 
                       fdisk, sda1 starts at sector 317572920.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b8387

Partition  Boot         Start           End          Size  Id System

/dev/sda1         317,572,920   625,137,344   307,564,425   7 HPFS/NTFS
/dev/sda2                  63   317,572,919   317,572,857   5 Extended
/dev/sda5                 126   305,556,299   305,556,174  83 Linux
/dev/sda6    *    305,556,363   317,572,919    12,016,557  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8A48BBCD48BBB5F3" TYPE="ntfs" 
/dev/sda5: UUID="0d386c39-b6e7-45d8-b629-01d9b97f0d00" TYPE="ext4" 
/dev/sda6: UUID="8ab12713-6608-4ade-b196-103c29742f30" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
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


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
# kopt=root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0d386c39-b6e7-45d8-b629-01d9b97f0d00

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

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro single 
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
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 8a48bbcd48bbb5f3
    drivemap -s (hd0) ${root}
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
UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8ab12713-6608-4ade-b196-103c29742f30 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/grub/menu.lst
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

```I think its because fdisk and the info in the boot sector are different.  I just have no idea how to fix it.  Please help!  Also, when I run gparted, it tells me that it is unable to read the contents of my ntfs partition.  I'm pretty sure both of these are caused by the same problem.

---

### Post by phillw on 2009-12-29
Hi !!,

Recover your win MBR - so it boots into win, then re-do your grub2 so it takes over -- both are covered here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You *may* just be able to re-do your grub2 - but re-doing the mbr for win, THEN re-doing grub seems a lot less painful.

Regards,

Phill.

---

### Post by rugbywarrior on 2009-12-29
I recovered my win MBR and when it restarted, it said :
 
No Bootable devices -- Strike F1 to retry boot, F2 for setup utility Press F5 to run onboard diagnostics. I ran the diagnostics and nothing came up. I know this seems to be becoming a windows problem but do you know what to do?
 
> **phillw said:**
> Hi !!,
 
Recover your win MBR - so it boots into win, then re-do your grub2 so it takes over -- both are covered here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
 
You *may* just be able to re-do your grub2 - but re-doing the mbr for win, THEN re-doing grub seems a lot less painful.
 
Regards,
 
Phill.

---

### Post by adam814 on 2009-12-29
In your boot.ini from Windows I notice two lines under operating systems

Try commenting out the second one since partition 2 on the disk is an extended partition with your linux install.  It may be looking for a Windows install that doesn't exist and hanging.  If that doesn't work try changing /optin after noexecute to /optout.

---

### Post by presence1960 on 2009-12-29
> **rugbywarrior said:**
> Hello,

I'm not sure whats going on.  I have been fighting with grub for weeks since i tried to dualboot windows after xubuntu.  I finally reformatted xubuntu and reinstalled it in order to dual boot.  Grub works just fine but when I choose to start windows, the screen turns black with that little white thingy in the top corner and just stays like that.  i ran boot_info_script and this is what it said:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 513790830. But according to the info from 
                       fdisk, sda1 starts at sector 317572920.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b8387

Partition  Boot         Start           End          Size  Id System

/dev/sda1         317,572,920   625,137,344   307,564,425   7 HPFS/NTFS
/dev/sda2                  63   317,572,919   317,572,857   5 Extended
/dev/sda5                 126   305,556,299   305,556,174  83 Linux
/dev/sda6    *    305,556,363   317,572,919    12,016,557  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8A48BBCD48BBB5F3" TYPE="ntfs" 
/dev/sda5: UUID="0d386c39-b6e7-45d8-b629-01d9b97f0d00" TYPE="ext4" 
/dev/sda6: UUID="8ab12713-6608-4ade-b196-103c29742f30" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
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


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
# kopt=root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0d386c39-b6e7-45d8-b629-01d9b97f0d00

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

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro single 
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
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 8a48bbcd48bbb5f3
    drivemap -s (hd0) ${root}
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
UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8ab12713-6608-4ade-b196-103c29742f30 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/grub/menu.lst
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

```I think its because fdisk and the info in the boot sector are different.  I just have no idea how to fix it.  Please help!  Also, when I run gparted, it tells me that it is unable to read the contents of my ntfs partition.  I'm pretty sure both of these are caused by the same problem.

Your boot.ini file is messed up. here is what you have:
```

================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS[COLOR="Red"].0[/COLOR] 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS[COLOR="Red"].0[/COLOR]="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
[COLOR="Red"]multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect [/COLOR]

```

I would edit that boot.ini file. You can do it from Ubuntu. Boot into Ubuntu. Open a file browser and mount your xp partition by clicking on it in the left pane. You may be asked for your superuser password to mount it. Once mounted make a back up of the file. Then open the file and change it to this:

```
[Boot Loader]

timeout=15

Default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[Operating Systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

Click Save on the top and close file. Reboot & see what happens. If it does not work you have the back up of the file if you wish to restore it to the way it was even though that does not boot.

Also I wonder if your partition numbering being off has something to do with it?

It can be fixed this way from terminal:

```
sudo fdisk /dev/sda
x
f
w
```

Enter each line one at a time in terminal.

If that rearranges your partition table so sda2 is windows make those lines in boot.ini with partition(1) read partition(2)

P.S. You also have the boot flag on sda6 (swap). You can remove that by booting the Live Cd and using gparted. Right click on sda6 and choose Manage Flags. Untick boot. After doing all the above you may want to put the boot flag on your windows partition.

---

### Post by oldfred on 2009-12-29
While I knew windows and Linux use different style line breaks I had not thought about editing windows files. Some  recently made this recommendation:

If editing windows files like boot.ini
(Use nano instead of gedit, it's better for dos-style linebreaks)

---

### Post by rugbywarrior on 2009-12-29
should I run the fixboot again after I edit the file?

---

### Post by presence1960 on 2009-12-29
```
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b8387

Partition  Boot         Start           End          Size  Id System

/dev/sda1         [COLOR="Red"]317,572,920[/COLOR]   625,137,344   307,564,425   7 HPFS/NTFS
/dev/sda2                  [COLOR="Red"]63[/COLOR]   317,572,919   317,572,857   5 Extended
/dev/sda5                 126   305,556,299   305,556,174  83 Linux
/dev/sda6    *    305,556,363   317,572,919    12,016,557  82 Linux swap / Solaris


```

I would try fixing your partition table first! Note the red highlighted start points. Your extended partition should be sda1 and your windows partition should be sda2.

Boot into Ubuntu and open a terminal and run these commands one line at a time:

```
sudo fdisk /dev/sda
x
f
w
```

Then I would fix your boot.ini file accordingly. if your windows becomes sda2 make boot.ini look like this, setting the timeout for your desired time span:

```
[Boot Loader]

timeout=15

Default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[Operating Systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

If it remains sda1 make (2) read (1)

Then try booting windows. if it doesn't boot we can go from there.

---

### Post by rugbywarrior on 2009-12-29
Okay  I think I have done everything and it is still not booting up.  I'm posting my boot info script as of now to see if I still have something messed up:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Fat16
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 513790830. But according to the info from 
                       fdisk, sda2 starts at sector 317572920.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b8387

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   317,572,919   317,572,857   5 Extended
/dev/sda5                 126   305,556,299   305,556,174  83 Linux
/dev/sda6         305,556,363   317,572,919    12,016,557  82 Linux swap / Solaris
/dev/sda2    *    317,572,920   625,137,344   307,564,425   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda2: UUID="8A48BBCD48BBB5F3" TYPE="ntfs" 
/dev/sda5: UUID="0d386c39-b6e7-45d8-b629-01d9b97f0d00" TYPE="ext4" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)


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
# kopt=root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0d386c39-b6e7-45d8-b629-01d9b97f0d00

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

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro single 
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
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 8a48bbcd48bbb5f3
    drivemap -s (hd0) ${root}
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
UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8ab12713-6608-4ade-b196-103c29742f30 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/grub/menu.lst
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
```
 

Hopefully, I didn't mess anything up.  Let me know

---

### Post by presence1960 on 2009-12-29
> **rugbywarrior said:**
> Okay  I think I have done everything and it is still not booting up.  I'm posting my boot info script as of now to see if I still have something messed up:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Fat16
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 513790830. But according to the info from 
                       fdisk, sda2 starts at sector 317572920.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b8387

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   317,572,919   317,572,857   5 Extended
/dev/sda5                 126   305,556,299   305,556,174  83 Linux
/dev/sda6         305,556,363   317,572,919    12,016,557  82 Linux swap / Solaris
/dev/sda2    *    317,572,920   625,137,344   307,564,425   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda2: UUID="8A48BBCD48BBB5F3" TYPE="ntfs" 
/dev/sda5: UUID="0d386c39-b6e7-45d8-b629-01d9b97f0d00" TYPE="ext4" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)


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
# kopt=root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0d386c39-b6e7-45d8-b629-01d9b97f0d00

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

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        0d386c39-b6e7-45d8-b629-01d9b97f0d00
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0d386c39-b6e7-45d8-b629-01d9b97f0d00
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 ro single 
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
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 8a48bbcd48bbb5f3
    drivemap -s (hd0) ${root}
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
UUID=0d386c39-b6e7-45d8-b629-01d9b97f0d00 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8ab12713-6608-4ade-b196-103c29742f30 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/grub/menu.lst
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
```
 

Hopefully, I didn't mess anything up.  Let me know

Looks good except for grub.cfg. The windows entry is still listed as the old entry (hd0,1). It is now on sda2 and needs to be (hd0,2). Should be a simple fix. Boot into Ubuntu and open a terminal. Run ```
sudo update-grub
```

When done reboot and try booting windows.

---

### Post by rugbywarrior on 2009-12-29
Ran sudo update got this:

```
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.
```

What happened?

---

### Post by presence1960 on 2009-12-29
> **rugbywarrior said:**
> Ran sudo update got this:

```
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.
```

What happened?

Have you fully converted to GRUB2 or are you still chainloading from the old GRUB with menu.lst?

You ran that from Ubuntu, not the Live CD right?

---

### Post by presence1960 on 2009-12-29
> **rugbywarrior said:**
> Ran sudo update got this:

```
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.
```

What happened?

I booted from my 9.10 Live USB and ran sudo update-grub and got the same error you just did. Boot your machine and boot into Ubuntu at the GRUB menu. When Ubuntu loads open a terminal and run that command again.

---

### Post by rugbywarrior on 2009-12-30
I was working off my live cd.  Fixed that.  Also, When I was following other forums, I took out grub-pc and installed grub.  I now reinstalled grub-pc again.  should I run grub-install again?  I ran update-grub after reinstalling and it worked, but windows still did not load.  I am starting to lose faith:(.  Is there anything else I can do?! I checked grub.cfg and the windows partition is under (hd0,2) now.

---

### Post by presence1960 on 2009-12-30
> **rugbywarrior said:**
> I was working off my live cd.  Fixed that.  Also, When I was following other forums, I took out grub-pc and installed grub.  I now reinstalled grub-pc again.  should I run grub-install again?  I ran update-grub after reinstalling and it worked, but windows still did not load.  I am starting to lose faith:(.  Is there anything else I can do?! I checked grub.cfg and the windows partition is under (hd0,2) now.

well it is really hard to keep track of what you have done especially since you did what we asked and what other forums have told you to do. You probably have a hodgepodge of boot files/directories in your /boot partition. At this point I would suspect that something is wrong with XP. You can find out by putting the windows bootloader on MBR and booting your machine. If you boot right into windows then we can reinstall GRUB. If you don't boot into windows your XP has other problems. To put windows bootloader on MBR do this:

Boot into Ubuntu. Open a terminal and run ```
sudo apt-get install lilo
```
Once lilo is installed run in terminal ```
sudo lilo -M /dev/sda mbr
```
This will fix your MBR so windows can boot. reboot , see what happens & report back.

---

### Post by rugbywarrior on 2009-12-31
> **presence1960 said:**
> well it is really hard to keep track of what you have done especially since you did what we asked and what other forums have told you to do. You probably have a hodgepodge of boot files/directories in your /boot partition. At this point I would suspect that something is wrong with XP. You can find out by putting the windows bootloader on MBR and booting your machine. If you boot right into windows then we can reinstall GRUB. If you don't boot into windows your XP has other problems. To put windows bootloader on MBR do this:

Boot into Ubuntu. Open a terminal and run ```
sudo apt-get install lilo
```
Once lilo is installed run in terminal ```
sudo lilo -M /dev/sda mbr
```
This will fix your MBR so windows can boot. reboot , see what happens & report back.

I did it and windows bootloader still couldn't open windows.  So I got angry enough, mounted my windows partition and copied my important files to xubuntu, reformatted, and did a fresh install of XP.  Luckily, I had more of an idea of what I was doing.  I booted from the live CD and ran:
```
sudo grub-install --root-directory=/media/sda5 /dev/sda
```

I restarted and got into xubuntu and ran update-grub.  Restarted and POOF... Windows started right up.  Thank you everybody who helped me figure this whole mess out.  I definately have a greater understanding of linux now.  

The last thing that I can byass easily enough but isn't right is when I start xubuntu is says:

One or more of the mounts listed in /etc/fstab cannot yet be mounted:
swap: waiting for UUID=8ab12713-6608-4ade-b196-103c29742f30
Press ESC to enter a recovery shell

I hit ESC and it works fine but I still want to fix it

My next question now is more simple.  Grub's list is:

ubuntu, linux ...... generic
ubuntu, linux ...... generic (recovery mode)
ubuntu, linux ...... generic
ubuntu, linux ...... generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows NT/2000/XP (loader)(on/dev/sda2)

My problem is that there are two of the same ubuntu options.  I want to take out the second 
ubuntu, linux ...... generic
ubuntu, linux ...... generic (recovery mode)
and I was also wondering if I should take out one of the memory tests.

Lastly and leastly, not terribly big deal is if i could rename what it says for example, rewriting:
Windows NT/2000/XP (loader)(on/dev/sda2) to just Windows XP

Thanks again!  My weeks of torturous frustration are over.:)

---

### Post by adam814 on 2009-12-31
As for removing the second ubuntu stanza it's most likely an old kernel.  It might be for example 2.6.31-14-generic or something like that.  To remove it boot to the first one (probably 2.6.31-16-generic) and remove the old one like any other package.

On grub legacy you could edit the menu.lst to change the entry name.  I believe some editing of /etc/grub.d/30_os-prober should do the trick, but I'm not sure exactly what you'd need to add there.  You could just change the name in /boot/grub/grub.cfg, but every time grub gets updated it'll likely be overwritten.

P.S. My system gives the same warning about the swap partition and then immediately continues (I don't have to press ESC).  I used ecryptfs-setup-swap to set up encrypted swap and my guess is it's waiting on cryptsetup to ready the partition.

---

### Post by rugbywarrior on 2009-12-31
> **adam814 said:**
> As for removing the second ubuntu stanza it's most likely an old kernel.  It might be for example 2.6.31-14-generic or something like that.  To remove it boot to the first one (probably 2.6.31-16-generic) and remove the old one like any other package.

On grub legacy you could edit the menu.lst to change the entry name.  I believe some editing of /etc/grub.d/30_os-prober should do the trick, but I'm not sure exactly what you'd need to add there.  You could just change the name in /boot/grub/grub.cfg, but every time grub gets updated it'll likely be overwritten.

P.S. My system gives the same warning about the swap partition and then immediately continues (I don't have to press ESC).  I used ecryptfs-setup-swap to set up encrypted swap and my guess is it's waiting on cryptsetup to ready the partition.

Just to be clear, I should remove the package called linux-headers-2.6.31-14-generic?

---

### Post by adam814 on 2009-12-31
You'd want to remove that one and also linux-image-2.6.31-14-generic as well.  The numbers might be different (i.e. it might be -15-generic).  I doubt Ubuntu package management will let you uninstall a running kernel, but just make sure it's the right kernel you're trying to remove.

---

### Post by presence1960 on 2009-12-31
> **rugbywarrior said:**
> Just to be clear, I should remove the package called linux-headers-2.6.31-14-generic?

also remove linux-image-2.6.31-14 for a complete wipe of that kernel.

Go to synaptic and find the ones you want to remove and mark for complete removal. You can also do it via terminal

---

### Post by presence1960 on 2009-12-31
If fixing the MBR did not work, you probably had more wrong with that windows install- a fact that I alluded to in my suggestions.

Glad you got it all sorted out. And you are correct about gaining experience and knowledge. Now you know something that I bet a lot of people on here may not know. So now pass it on and help someone with the same issue. Knowledge is not good unless shared.

---

