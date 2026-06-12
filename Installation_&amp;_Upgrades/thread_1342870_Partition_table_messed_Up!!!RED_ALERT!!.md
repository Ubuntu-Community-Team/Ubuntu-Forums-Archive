---
title: "Partition table messed Up!!!RED ALERT!!"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by rahilm on 2009-12-01
hello..all....i thought this might be the appropriate place to post partition related problems.. I did three horrible mistakes and want your help in correcting them...
Background:
XP, 9.04 and 9.10 boot peacefully in my harddisk.

Mistake 1:
I got windows 7 professional and installed it in place of XP.It reset my MBR AND partition table. I reinstall grub2 to correct it.

Present Scenario:
All linuxes boot perfectly except that only the partition editor does not detect my partitions. It shows the whole disk as unallocated.

Mistake 2:
I had previously made a backup of my MBR using...
sudo dd if=/dev/sda count=1 bs=512 > smbr

i tried to restore that using
sudo dd if=smbr of=/dev/sda count=1 bs=512

Present Scenario:
Nothing boots....and whats more all partition edtors show my D drive : 74 GB NTFS partition , the most valuable thing on my PC as unpartitioned....

Mistake 3:
Waiting to happen...



Please help in the name of all humanity..

---

### Post by darkod on 2009-12-01
Use the script link in my signature, download and execute that script, and post back the content of the created results.txt file. Please wrap CODE tags around it, # icon in the toolbar for easier reading.
The script can be executed, for example if on Desktop:
sudo bash ~/Desktop/boot_info_script*.sh

---

### Post by rahilm on 2009-12-01
That sdb is just a memory card reader in which i had installed grub:

```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b5d41

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    47,295,359    47,295,297   7 HPFS/NTFS
/dev/sda2          47,295,360   114,398,864    67,103,505   7 HPFS/NTFS
/dev/sda3         114,398,865   312,576,704   198,177,840   f W95 Ext d (LBA)
Empty Partition
/dev/sda5         114,398,991   135,363,689    20,964,699  83 Linux
/dev/sda6         135,363,753   154,513,169    19,149,417  83 Linux
/dev/sda7         154,513,233   156,344,579     1,831,347  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 993 MB, 993001472 bytes
2 heads, 1 sectors/track, 969728 cylinders, total 1939456 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00086601

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            133     1,939,455     1,939,323   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="3878467A78463742" TYPE="ntfs" 
/dev/sda2: UUID="3CB01714B016D46C" LABEL="Extended" TYPE="ntfs" 
/dev/sda5: LABEL="jaunty" UUID="d31d0d22-8ded-4a76-acb0-c1770822047e" TYPE="ext3" 
/dev/sda6: LABEL="karmic" UUID="f2f23828-ce5d-4e22-947f-f39bdd8a3383" TYPE="ext4" 
/dev/sda7: TYPE="swap" UUID="99b7e6bc-c2a4-47b7-b54e-bc54ee177549" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="MOMIN" UUID="272F-0186" TYPE="vfat" 

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
/dev/sdb1 on /media/MOMIN type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda5 on /media/jaunty type ext3 (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/menu.lst: ===========================

default        saved
# GRUB configuration file '/boot/grub/menu.lst'.
# generated by 'grubconfig'.  Sun Oct 25 16:32:07 2009
#
# The backup copy of the MBR for drive '/dev/sda' is
# here '/boot/grub/mbr.sda.12701'.  You can restore it like this.
# dd if=/boot/grub/mbr.sda.12701 of=/dev/sda bs=512 count=1
#
# Start GRUB global section
timeout        30
#color white/brown red/black

#A splash image for the menu
#splashimage=/boot/grub/splashimages/29962-grubuntu.xpm.gz
gfxmenu /boot/grub/deep_stage1
# End GRUB global section

title        Linux Mint 7 Gloria, kernel 2.6.28-11-generic
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda8 ro quiet splash vga=788 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Linux Mint 7 Gloria, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda8 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Linux Mint 7 Gloria, memtest86+
root        (hd0,7)
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
# linux installation on /dev/sda6.
title        Ubuntu 9.04 (9.04) (on /dev/sda6)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-14-generic root=/dev/sda6 quiet splash
initrd        /boot/initrd.img-2.6.28-14-generic
savedefault
boot

title        Ubuntu 9.04 (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda8 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet
# Linux bootable initrd config ends
title Install GRUB to floppy disk (on /dev/fd0)
pause Insert a formatted floppy disk and press enter.
root (hd0,5)
setup (fd0)
pause Press enter to continue.
title Install GRUB to Linux partition (on /dev/sda6)
root (hd0,5)
setup (hd0,5)
pause Press enter to continue.
title -     For help press 'c', then type: 'help'
root (hd0)
title -     For usage examples, type: 'cat /boot/grub/usage.txt'
root (hd0)
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
# kopt=root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d31d0d22-8ded-4a76-acb0-c1770822047e

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
# defoptions=splash vga=792

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

title        Debian GNU/Linux, kernel 2.6.28-14-generic
root        d31d0d22-8ded-4a76-acb0-c1770822047e
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro splash vga=792
initrd        /boot/initrd.img-2.6.28-14-generic

title        Debian GNU/Linux, kernel 2.6.28-14-generic (recovery mode)
root        d31d0d22-8ded-4a76-acb0-c1770822047e
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Debian GNU/Linux, kernel 2.6.28-11-generic
root        d31d0d22-8ded-4a76-acb0-c1770822047e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro splash vga=792
initrd        /boot/initrd.img-2.6.28-11-generic

title        Debian GNU/Linux, kernel 2.6.28-11-generic (recovery mode)
root        d31d0d22-8ded-4a76-acb0-c1770822047e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Debian GNU/Linux, kernel memtest86+
root        d31d0d22-8ded-4a76-acb0-c1770822047e
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd0,6)
search --fs-uuid --set d31d0d22-8ded-4a76-acb0-c1770822047e
if font /usr/share/grub/ascii.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
set root=(hd0,6)
search --fs-uuid --set d31d0d22-8ded-4a76-acb0-c1770822047e
menuentry "Ubuntu, linux 2.6.28-14-generic" {
    linux    /boot/vmlinuz-2.6.28-14-generic root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro  quiet splash
    initrd    /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu, linux 2.6.28-14-generic (single-user mode)" {
    linux    /boot/vmlinuz-2.6.28-14-generic root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro single 
    initrd    /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu, linux 2.6.28-11-generic" {
    linux    /boot/vmlinuz-2.6.28-11-generic root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro  quiet splash
    initrd    /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, linux 2.6.28-11-generic (single-user mode)" {
    linux    /boot/vmlinuz-2.6.28-11-generic root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro single 
    initrd    /boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    set root=(hd0,1)
    chainloader +1
}
menuentry "Linux Mint 7 Gloria, kernel 2.6.28-11-generic (on /dev/sda8)" {
    set root=(hd0,8)
    linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda8 ro quiet splash vga=788
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Linux Mint 7 Gloria, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda8)" {
    set root=(hd0,8)
    linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda8 ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Linux Mint 7 Gloria, memtest86+ (on /dev/sda8)" {
    set root=(hd0,8)
    linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 9.04 (recovery mode) (on /dev/sda8)" {
    set root=(hd0,8)
    linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda8 ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda8)" {
    set root=(hd0,8)
    linux /boot/memtest86+.bin 
}
menuentry "Linux Mint 7 Gloria, kernel 2.6.28-11-generic (on /dev/sda8)" {
    set root=(hd0,8)
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro quiet splash vga=791
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Linux Mint 7 Gloria, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda8)" {
    set root=(hd0,8)
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Linux Mint 7 Gloria, memtest86+ (on /dev/sda8)" {
    set root=(hd0,8)
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=d31d0d22-8ded-4a76-acb0-c1770822047e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=99b7e6bc-c2a4-47b7-b54e-bc54ee177549 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  58.5GB: boot/grub/grub.cfg
  58.5GB: boot/grub/menu.lst
  58.5GB: boot/grub/stage2
  60.6GB: boot/initrd.img-2.6.28-11-generic
  58.6GB: boot/initrd.img-2.6.28-14-generic
  58.5GB: boot/vmlinuz-2.6.28-11-generic
  60.2GB: boot/vmlinuz-2.6.28-14-generic
  58.6GB: initrd.img
  60.6GB: initrd.img.old
  60.2GB: vmlinuz
  58.5GB: vmlinuz.old

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
set root=(hd0,8)
search --no-floppy --fs-uuid --set f2f23828-ce5d-4e22-947f-f39bdd8a3383
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
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set f2f23828-ce5d-4e22-947f-f39bdd8a3383
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f2f23828-ce5d-4e22-947f-f39bdd8a3383 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set f2f23828-ce5d-4e22-947f-f39bdd8a3383
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f2f23828-ce5d-4e22-947f-f39bdd8a3383 ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0000-0d84
    chainloader +1
}
menuentry "Linux Mint 7 Gloria, kernel 2.6.28-11-generic (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d31d0d22-8ded-4a76-acb0-c1770822047e
    linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda8 ro quiet splash vga=788
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Linux Mint 7 Gloria, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d31d0d22-8ded-4a76-acb0-c1770822047e
    linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda8 ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Linux Mint 7 Gloria, memtest86+ (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d31d0d22-8ded-4a76-acb0-c1770822047e
    linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 9.04 (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d31d0d22-8ded-4a76-acb0-c1770822047e
    linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda8 ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d31d0d22-8ded-4a76-acb0-c1770822047e
    linux /boot/memtest86+.bin 
}
menuentry "Debian GNU/Linux, kernel 2.6.28-14-generic (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d31d0d22-8ded-4a76-acb0-c1770822047e
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro splash vga=792
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Debian GNU/Linux, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d31d0d22-8ded-4a76-acb0-c1770822047e
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro single
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Debian GNU/Linux, kernel 2.6.28-11-generic (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d31d0d22-8ded-4a76-acb0-c1770822047e
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro splash vga=792
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Debian GNU/Linux, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d31d0d22-8ded-4a76-acb0-c1770822047e
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Debian GNU/Linux, kernel memtest86+ (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d31d0d22-8ded-4a76-acb0-c1770822047e
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
# / was on /dev/sda8 during installation
UUID=f2f23828-ce5d-4e22-947f-f39bdd8a3383 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=99b7e6bc-c2a4-47b7-b54e-bc54ee177549 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  71.9GB: boot/grub/grub.cfg
  70.1GB: boot/initrd.img-2.6.31-14-generic
  71.6GB: boot/vmlinuz-2.6.31-14-generic
  70.1GB: initrd.img
  71.6GB: vmlinuz

=========================== sdb1/boot/grub/menu.lst: ===========================

default        saved
# GRUB configuration file '/boot/grub/menu.lst'.
# generated by 'grubconfig'.  Sun Oct 25 16:32:07 2009
#
# The backup copy of the MBR for drive '/dev/sda' is
# here '/boot/grub/mbr.sda.12701'.  You can restore it like this.
# dd if=/boot/grub/mbr.sda.12701 of=/dev/sda bs=512 count=1
#
# Start GRUB global section
timeout        30
#color white/brown red/black

#A splash image for the menu
#splashimage=/boot/grub/splashimages/29962-grubuntu.xpm.gz
gfxmenu /boot/grub/deep_stage1
# End GRUB global section

title        Linux Mint 7 Gloria, kernel 2.6.28-11-generic
root        (hd1,7)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda8 ro quiet splash vga=788 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Linux Mint 7 Gloria, kernel 2.6.28-11-generic (recovery mode)
root        (hd1,7)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda8 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Linux Mint 7 Gloria, memtest86+
root        (hd1,7)
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
rootnoverify    (hd1,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title        Ubuntu 9.04 (9.04) (on /dev/sda6)
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.28-14-generic root=/dev/sda6 quiet splash
initrd        /boot/initrd.img-2.6.28-14-generic
savedefault
boot

title        Ubuntu 9.04 (recovery mode)
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda8 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        (hd1,5)
kernel        /boot/memtest86+.bin
quiet
# Linux bootable initrd config ends
title Install GRUB to floppy disk (on /dev/fd0)
pause Insert a formatted floppy disk and press enter.
root (hd0,5)
setup (fd0)
pause Press enter to continue.
title Install GRUB to Linux partition (on /dev/sda6)
root (hd0,5)
setup (hd0,5)
pause Press enter to continue.
title -     For help press 'c', then type: 'help'
root (hd0)
title -     For usage examples, type: 'cat /boot/grub/usage.txt'
root (hd0)
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
# kopt=root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d31d0d22-8ded-4a76-acb0-c1770822047e

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
# defoptions=splash vga=792

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

title        Debian GNU/Linux, kernel 2.6.28-14-generic
root        d31d0d22-8ded-4a76-acb0-c1770822047e
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro splash vga=792
initrd        /boot/initrd.img-2.6.28-14-generic

title        Debian GNU/Linux, kernel 2.6.28-14-generic (recovery mode)
root        d31d0d22-8ded-4a76-acb0-c1770822047e
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Debian GNU/Linux, kernel 2.6.28-11-generic
root        d31d0d22-8ded-4a76-acb0-c1770822047e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro splash vga=792
initrd        /boot/initrd.img-2.6.28-11-generic

title        Debian GNU/Linux, kernel 2.6.28-11-generic (recovery mode)
root        d31d0d22-8ded-4a76-acb0-c1770822047e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d31d0d22-8ded-4a76-acb0-c1770822047e ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Debian GNU/Linux, kernel memtest86+
root        d31d0d22-8ded-4a76-acb0-c1770822047e
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/menu.lst
    .1GB: boot/grub/stage2
    .0GB: initrd.gz
    .0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde 

```

---

### Post by darkod on 2009-12-01
OK. First of all, are you sure you installed win7 at all? You can see on sda1 (top of the results) you have boot/ini and ntldr present. That is how winxp is booting, not win7. EDIT: This might be because of the MBR restore you tried with dd. Highly recommended not to do that again. Any problem that was present might have been resolved in a better way.

According to the results, you have:
sda1 47GB ntfs
sda2 67GB ntfs
sda5 21GB ext3 jaunty
sda6 19GB ext4 karmic
sda7 2GB swap

Is this what you expect to see?

---

### Post by rahilm on 2009-12-01
> **darkod said:**
> OK. First of all, are you sure you installed win7 at all? You can see on sda1 (top of the results) you have boot/ini and ntldr present. That is how winxp is booting, not win7.

According to the results, you have:
sda1 47GB ntfs
sda2 67GB ntfs
sda5 21GB ext3 jaunty
sda6 19GB ext4 karmic
sda7 2GB swap

Is this what you expect to see?

Now.. i remember...that was mistake 3: Re-installing XP which hung in the middle...

The disk sizes are all wrong almost twice of the real values

there is an sda3 74.2 GB which is my D: Drive ...The reason i posted this thread

---

### Post by rahilm on 2009-12-01
If you can see in the image is the real problem:

---

### Post by darkod on 2009-12-01
Sorry, my mistake, I doubled the values. You have a real problem because no sda3 is shown up. In the results sda3 is shown as the extended partition, the one in which your both ubuntus are.

So you need to have a third ntfs partition in addition to the two I mentioned, right?

---

### Post by rahilm on 2009-12-01
> **darkod said:**
> Sorry, my mistake, I doubled the values. You have a real problem because no sda3 is shown up. In the results sda3 is shown as the extended partition, the one in which your both ubuntus are.

So you need to have a third ntfs partition in addition to the two I mentioned, right?

right

---

### Post by darkod on 2009-12-01
First step would be to download clonezilla and back up all of your partitions or just the 74GB partition (hopefully it can see it).

Go to [www.clonezilla.org]("http://www.clonezilla.org") and get the image. Burn it on CD, it's bootable image. You will be able to boot with the CD and make an image of the partitions you need to an external usb hdd for example. I do not recommend saving the backup image on your internal drive.

CloneZilla can recognize ntfs, ext3 and ext4, and it only images the used part with the data. If it can't recognize the 74GB partition, I think there is option to just image all of it sector by sector.

After you have the data safe, you can try either installing win7 on sda1, or repairing XP on sda1. They might in fact recognize the 74GB partition and all to be fine, but you need to have the backup in case it doesn't.

You shouldn't have done all that install/restore cycles, especially if a problem appeared.

If clonezilla can see the 74GB you're good.

---

### Post by darkod on 2009-12-01
Also, depending of the importance of the data on 74GB partition, you might want to start searching for recovery software for windows. Hopefully some bootable software which can detect ntfs data partitions and recover the data.

CloneZilla is a great tool for both ntfs and ext3/ext4 but check if it will help you recover the data if the partition table got really messed up.

Data Recovery Software usually scans the disk sector by sector, so even destroyed partition table wouldn't stop it. Not sure how exactly CloneZilla does it.

---

### Post by rahilm on 2009-12-01
i'll try it

---

### Post by rahilm on 2009-12-01
i'll try it but it'll take three days just to download it...(bad connection here)

---

### Post by darkod on 2009-12-01
:( It's a small image, 100MB not a whole cd.

You can try repairing XP as I said, but it's a bit risky. You will not install it on the 74GB partition anyway so it will not touch it. But it's much better to have a backup first before trying that.

---

### Post by rahilm on 2009-12-01
100 MB may be a small image but it is a very big file..it'll download it in 5 minutes but i don't have an unlimited plan here ... and i am still a kid to afford those extra bucks

---

### Post by rahilm on 2009-12-01
Listen one and listen all...

I came across a magnificent piece of software.. a life saver .. in crisis like situation like mine...
just needed the right word 'Partition Recovery Linux' and google


its called TestDisk

[html]www.cgsecurity.org/wiki/TestDisk[/html]Highly recommended. I am changing the status to SOLVED.

What it did:
Everything is back to normal. With a single In-Depth scan, it restored my partition table, now I can try installing Windows 7 again and restore Grub2

Thanx all you guys for helping me

---

