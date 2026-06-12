---
title: "Grub Error 13: Invalid or Unsupported Executable Format"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by root45 on 2009-11-28
Hi,

I've read through most of the threads on this issue, but none of them seem to help.

This is what's written in my menu.lst file:

```
title        Chainload into GRUB 2
root        (hd0,5)
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Ubuntu 9.10, kernel 2.6.31-302-ec2
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-302-ec2 root=/dev/sda6 ro splash vga=775 quiet
quiet

title        Ubuntu 9.10, kernel 2.6.31-302-ec2 (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-302-ec2 root=/dev/sda6 ro single

title        Ubuntu 9.10, memtest86+
root        (hd0,5)
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
map        (hd0)(hd1)
map        (hd1)(hd0)
chainloader    +1
```I added the lines
```

map        (hd0)(hd1)
map        (hd1)(hd0)
```after reading some of the posts in this forum, but the same error results before and after.

This is the output of sudo fdisk -l

```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4da74da6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2066    16595113+   7  HPFS/NTFS
/dev/sda3            2067       38913   295973527+   f  W95 Ext'd (LBA)
/dev/sda5            2067       35533   268823646   83  Linux
/dev/sda6           35534       38721    25607578+  83  Linux
/dev/sda7           38722       38913     1542208+  82  Linux swap / Solaris

```Most of the posts regarding this error arise from a mismatched set of partitions for booting, but from what I can tell, these match up in the right way. So I'm not sure where to go from here.

If it helps, there wasn't any problem until I tried upgrading from 9.04 to 9.10 earlier today. After restarting I got this error. Thanks for any input.

-Kris

---

### Post by presence1960 on 2009-11-28
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by root45 on 2009-11-28
Here's the output.

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4da74da6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    33,190,289    33,190,227   7 HPFS/NTFS
/dev/sda3          33,190,290   625,137,344   591,947,055   f W95 Ext d (LBA)
/dev/sda5          33,190,353   570,837,644   537,647,292  83 Linux
/dev/sda6         570,837,708   622,052,864    51,215,157  83 Linux
/dev/sda7         622,052,928   625,137,344     3,084,417  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="1498840E9883ED14" TYPE="ntfs" 
/dev/sda5: LABEL="/home" UUID="2e55cb8b-9d27-4a7d-83cb-85f69a203a63" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="/" UUID="155d64e8-60bd-446a-b2ae-5e2dae382f16" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" 

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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


======================== sda1/ubuntu/winboot/menu.lst: ========================

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

================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd0,5)/boot/grub/splashimages/Blue.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=/dev/sda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
# defoptions=splash vga=775 quiet

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
# howmany=1

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

title        Chainload into GRUB 2
root        (hd0,5)
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Ubuntu 9.10, kernel 2.6.31-302-ec2
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-302-ec2 root=/dev/sda6 ro splash vga=775 quiet
quiet

title        Ubuntu 9.10, kernel 2.6.31-302-ec2 (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.31-302-ec2 root=/dev/sda6 ro single

title        Ubuntu 9.10, memtest86+
root        (hd0,5)
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
map        (hd0)(hd1)
map        (hd1)(hd0)
chainloader    +1


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
search --no-floppy --fs-uuid --set 155d64e8-60bd-446a-b2ae-5e2dae382f16
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
menuentry "Ubuntu, Linux 2.6.31-302-ec2" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 155d64e8-60bd-446a-b2ae-5e2dae382f16
    linux    /boot/vmlinuz-2.6.31-302-ec2 root=UUID=155d64e8-60bd-446a-b2ae-5e2dae382f16 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-302-ec2
}
menuentry "Ubuntu, Linux 2.6.31-302-ec2 (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 155d64e8-60bd-446a-b2ae-5e2dae382f16
    linux    /boot/vmlinuz-2.6.31-302-ec2 root=UUID=155d64e8-60bd-446a-b2ae-5e2dae382f16 ro single 
    initrd    /boot/initrd.img-2.6.31-302-ec2
}
menuentry "Ubuntu, Linux 2.6.31-15-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 155d64e8-60bd-446a-b2ae-5e2dae382f16
    linux    /boot/vmlinuz-2.6.31-15-server root=UUID=155d64e8-60bd-446a-b2ae-5e2dae382f16 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-server
}
menuentry "Ubuntu, Linux 2.6.31-15-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 155d64e8-60bd-446a-b2ae-5e2dae382f16
    linux    /boot/vmlinuz-2.6.31-15-server root=UUID=155d64e8-60bd-446a-b2ae-5e2dae382f16 ro single 
    initrd    /boot/initrd.img-2.6.31-15-server
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 155d64e8-60bd-446a-b2ae-5e2dae382f16
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=155d64e8-60bd-446a-b2ae-5e2dae382f16 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 155d64e8-60bd-446a-b2ae-5e2dae382f16
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=155d64e8-60bd-446a-b2ae-5e2dae382f16 ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 155d64e8-60bd-446a-b2ae-5e2dae382f16
    linux    /boot/vmlinuz-2.6.31-14-server root=UUID=155d64e8-60bd-446a-b2ae-5e2dae382f16 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-server
}
menuentry "Ubuntu, Linux 2.6.31-14-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 155d64e8-60bd-446a-b2ae-5e2dae382f16
    linux    /boot/vmlinuz-2.6.31-14-server root=UUID=155d64e8-60bd-446a-b2ae-5e2dae382f16 ro single 
    initrd    /boot/initrd.img-2.6.31-14-server
}
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 155d64e8-60bd-446a-b2ae-5e2dae382f16
    linux    /boot/vmlinuz-2.6.28-16-generic root=UUID=155d64e8-60bd-446a-b2ae-5e2dae382f16 ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 155d64e8-60bd-446a-b2ae-5e2dae382f16
    linux    /boot/vmlinuz-2.6.28-16-generic root=UUID=155d64e8-60bd-446a-b2ae-5e2dae382f16 ro single 
    initrd    /boot/initrd.img-2.6.28-16-generic
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
    search --no-floppy --fs-uuid --set 1498840e9883ed14
    drivemap -s (hd0) ${root}
    chainloader +1
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
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    relatime,errors=remount-ro 0       1
/dev/sda5       /home           ext3    relatime        0       2
/dev/sda7       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 292.2GB: boot/grub/grub.cfg
 292.2GB: boot/grub/menu.lst
 292.2GB: boot/grub/stage2
 292.2GB: boot/initrd.img-2.6.28-16-generic
 292.2GB: boot/initrd.img-2.6.31-14-server
 292.2GB: boot/initrd.img-2.6.31-15-generic
 292.2GB: boot/initrd.img-2.6.31-15-server
 292.2GB: boot/initrd.img-2.6.31-302-ec2
 292.2GB: boot/vmlinuz-2.6.28-16-generic
 292.2GB: boot/vmlinuz-2.6.31-14-server
 292.2GB: boot/vmlinuz-2.6.31-15-generic
 292.2GB: boot/vmlinuz-2.6.31-15-server
 292.2GB: boot/vmlinuz-2.6.31-302-ec2
 292.2GB: initrd.img
 292.2GB: initrd.img.old
 292.2GB: vmlinuz
 292.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
00000200

Unknown BootLoader  on sda6

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
00000200

```

---

### Post by presence1960 on 2009-11-28
I see you did an upgrade to 9.10.

Can you chainload into GRUB 2 from the legacy GRUB menu?

Which choice in the grub menu do you choose when you get the error 13?

---

### Post by root45 on 2009-11-28
Sorry, I'm not entirely sure how to do that. Selecting "Chainload into GRUB 2" from the menu gives me another boot menu headed with "GNU GRUB version 1.97~beta4". If I try to boot anything from that menu I get the error that I "need to load the kernel first".

How exactly do I Chainload into GRUB2?

---

### Post by presence1960 on 2009-11-28
> **root45 said:**
> Sorry, I'm not entirely sure how to do that. Selecting "Chainload into GRUB 2" from the menu gives me another boot menu headed with "GNU GRUB version 1.97~beta4". If I try to boot anything from that menu I get the error that I "need to load the kernel first".

How exactly do I Chainload into GRUB2?

The way you just did it.

When do you get error 13? which menu items give that error?

---

### Post by root45 on 2009-11-28
The boot options

Ubuntu 9.10, kernel 2.6.31-302-ec2
Ubuntu 9.10, kernel 2.6.31-302-ec2 (recovery mode)

give error 13. The option

Ubuntu 9.10, memtest86+

runs the memory test. The option

Microsoft Windows XP Professional

now gives "Error 11: Unrecognized device string".

I tried deleting the "map (hd0)(hd1)" and "map (hd1)(hd0)" lines under the Windows entry in menu.lst. Now if I select

Microsoft Windows XP Professional

I'm taken to another boot screen (a Windows boot screen, I think). If I choose Windows everything works fine. Choosing "Ubuntu" loads a rather long splash screen which eventually results in a CLI prefaced with

BusyBox v1.1.0.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)

with the prompt "(initramfs)". On the old installation (9.04) choosing "Ubuntu" just loaded it, so I've never seen this before.

---

### Post by presence1960 on 2009-11-28
> **root45 said:**
> The boot options

Ubuntu 9.10, kernel 2.6.31-302-ec2
Ubuntu 9.10, kernel 2.6.31-302-ec2 (recovery mode)

give error 13. The option

Ubuntu 9.10, memtest86+

runs the memory test. The option

Microsoft Windows XP Professional

now gives "Error 11: Unrecognized device string".

I tried deleting the "map (hd0)(hd1)" and "map (hd1)(hd0)" lines under the Windows entry in menu.lst. Now if I select

Microsoft Windows XP Professional

I'm taken to another boot screen (a Windows boot screen, I think). If I choose Windows everything works fine. Choosing "Ubuntu" loads a rather long splash screen which eventually results in a CLI prefaced with

BusyBox v1.1.0.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)

with the prompt "(initramfs)". On the old installation (9.04) choosing "Ubuntu" just loaded it, so I've never seen this before.

Try booting one of the other Linux kernels. The two latest kernels from Synaptic for karmic are 2.31.6.15 & 2.6.31.14

I would stick with those if they successfully boot. I would then remove the other kernels from Synaptic by removing linux-headers-(kernel#) & linux-image-(kernel#)

For windows error 11 see [here]("https://help.ubuntu.com/community/Grub2#Resolving%20an%20%22Unrecognized%20Device%20String%22%20%28Error%2011%29")
It is late, I am going to bed. Hope this helps. Will check back tomorrow.

---

### Post by root45 on 2009-11-28
Okay. I've tried all the kernels I have available from GRUB. If I chainload into GRUB 2, I have the following boot options:

2.6.31-302-ec2
2.6.31-302-ec2 (recovery mode)
2.6.31-15-generic
2.6.31-15-generic (recovery mode)
2.6.31-16-generic
2.6.31-16-generic (recovery mode)
Memory test (memtest86+)
Windows XP

(plus some more server options). Trying 2.6.31-302-ec2 from this menu gives the error that I need to load the kernel first. I'm not entirely sure what that means.

If I try to load 2.6.31-15-generic or 2.6.31-16-generic, things start out fine, but eventually the screen starts to flash rapidly. A single user prompt appears, but the keyboard only accepts input half the time so I can't log in.

If I load the recovery mode for 2.6.31-15 or 2.6.31-16 and then select "Continue Booting" I'm dropped to a shell. The screen doesn't flash and everything seems to work okay, so for some reason this circumvents the issue with just loading these kernels directly. I can't start gdm from the shell.

Finally, I tried editing the boot command for 2.6.31-302-ec2 in the original GRUB menu to use the -15 kernel instead, and I just got a black screen. I waited about 5 or 10 minutes, but nothing happened.

So basically, none of these kernels helped. Any other ideas? Thanks.

---

