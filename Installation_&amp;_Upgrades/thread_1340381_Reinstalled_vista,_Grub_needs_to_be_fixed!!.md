---
title: "Reinstalled vista, Grub needs to be fixed!!"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by slippycurb on 2009-11-28
Greetings Oh Mighty Ones From Planet Ubuntu!!!!
The title is probably misleading....as the trouble is most definitively me. Any help from any of you Gorgeous Guys N Gals would make me incredibly happy!!!
I had to recently reinstall vista alongside my pre-existing ubuntu 9.08(I think,could be .04), and low and behold, the mbr is over written. I know I could just install a fresh 9.10, but I have compat-wireless with a special b43 driver I compiled and installed on kernel vmlinuz-2.6.28-15-generic. I would just like to fix the boot up and maybe upgrade to 9.10 online at a later date.
I have the 9.10 live distro and was able to run BOOT_INFO.sh to get the following information for any intelligent aliens that would like to help such a lowly uncouth creature as myself.

============================= Boot Info Summary: ==============================

=> Windows is installed in the MBR of /dev/sda
=> No boot loader is installed in the MBR of /dev/sdb

sda1: __________________________________________________ _______________________

File system: vfat
Boot sector type: Dell Utility: Fat16
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: 

sda2: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows Vista
Boot files/dirs: /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________ _______________________

File system: ext3
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 9.04
Boot files/dirs: /boot/grub/menu.lst /etc/fstab

sdb1: __________________________________________________ _______________________

File system: vfat
Boot sector type: Fat16
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: 

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa9f9aa9b

Partition Boot Start End Size Id System

/dev/sda1 63 80,324 80,262 de Dell Utility
/dev/sda2 * 81,920 563,703,807 563,621,888 7 HPFS/NTFS
/dev/sda3 563,704,785 625,137,344 61,432,560 83 Linux


Drive: sdb ___________________ __________________________________________________ ___

Disk /dev/sdb: 522 MB, 522452992 bytes
2 heads, 63 sectors/track, 8098 cylinders, total 1020416 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x001432e6

Partition Boot Start End Size Id System

/dev/sdb1 * 32 1,020,415 1,020,384 6 FAT16


blkid -c /dev/null: __________________________________________________ __________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: UUID="546659D46659B786" TYPE="ntfs" 
/dev/sda3: UUID="b7b7a00d-ca2f-4e7f-b183-f58bddefd0bb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: SEC_TYPE="msdos" UUID="3CEA-8D72" TYPE="vfat" 

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
/dev/sdb1 on /media/3CEA-8D72 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,sh ortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default	 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout	 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title	 Windows 95/98/NT/2000
# root	 (hd0,0)
# makeactive
# chainloader	+1
#
# title	 Linux
# root	 (hd0,1)
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b7b7a00d-ca2f-4e7f-b183-f58bddefd0bb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b7b7a00d-ca2f-4e7f-b183-f58bddefd0bb

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
## indomU=true
## indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title	 Ubuntu 9.04, kernel 2.6.28-16-generic
uuid	 b7b7a00d-ca2f-4e7f-b183-f58bddefd0bb
kernel	 /boot/vmlinuz-2.6.28-16-generic root=UUID=b7b7a00d-ca2f-4e7f-b183-f58bddefd0bb ro quiet splash 
initrd	 /boot/initrd.img-2.6.28-16-generic
quiet

title	 Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid	 b7b7a00d-ca2f-4e7f-b183-f58bddefd0bb
kernel	 /boot/vmlinuz-2.6.28-16-generic root=UUID=b7b7a00d-ca2f-4e7f-b183-f58bddefd0bb ro single
initrd	 /boot/initrd.img-2.6.28-16-generic

title	 Ubuntu 9.04, kernel 2.6.28-15-generic
uuid	 b7b7a00d-ca2f-4e7f-b183-f58bddefd0bb
kernel	 /boot/vmlinuz-2.6.28-15-generic root=UUID=b7b7a00d-ca2f-4e7f-b183-f58bddefd0bb ro quiet splash 
initrd	 /boot/initrd.img-2.6.28-15-generic
quiet

title	 Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid	 b7b7a00d-ca2f-4e7f-b183-f58bddefd0bb
kernel	 /boot/vmlinuz-2.6.28-15-generic root=UUID=b7b7a00d-ca2f-4e7f-b183-f58bddefd0bb ro single
initrd	 /boot/initrd.img-2.6.28-15-generic

title	 Ubuntu 9.04, kernel 2.6.28-11-generic
uuid	 b7b7a00d-ca2f-4e7f-b183-f58bddefd0bb
kernel	 /boot/vmlinuz-2.6.28-11-generic root=UUID=b7b7a00d-ca2f-4e7f-b183-f58bddefd0bb ro quiet splash 
initrd	 /boot/initrd.img-2.6.28-11-generic
quiet

title	 Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid	 b7b7a00d-ca2f-4e7f-b183-f58bddefd0bb
kernel	 /boot/vmlinuz-2.6.28-11-generic root=UUID=b7b7a00d-ca2f-4e7f-b183-f58bddefd0bb ro single
initrd	 /boot/initrd.img-2.6.28-11-generic

title	 Ubuntu 9.04, memtest86+
uuid	 b7b7a00d-ca2f-4e7f-b183-f58bddefd0bb
kernel	 /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title	 Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title	 Windows Vista (loader)
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda4 during installation
UUID=b7b7a00d-ca2f-4e7f-b183-f58bddefd0bb / ext3 relatime,errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sda3: Location of files loaded by Grub: ===================


288.6GB: boot/grub/menu.lst
288.6GB: boot/grub/stage2
288.6GB: boot/initrd.img-2.6.28-11-generic
288.6GB: boot/initrd.img-2.6.28-15-generic
288.6GB: boot/initrd.img-2.6.28-16-generic
288.6GB: boot/initrd.img-2.6.31-wl
288.6GB: boot/vmlinuz-2.6.28-11-generic
288.6GB: boot/vmlinuz-2.6.28-15-generic
288.6GB: boot/vmlinuz-2.6.28-16-generic
288.6GB: initrd.img
288.6GB: initrd.img.old
288.6GB: vmlinuz
288.6GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc

---

### Post by phillw on 2009-11-28
Recovering ubuntu / win boot areas is covered here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Should get you up and running with the minimum of fuss :-)

regards,

Phill.

---

### Post by slippycurb on 2009-11-28
Thank you.........Keep on Rocking

---

### Post by oldfred on 2009-11-28
I thought I had posted to your question but my answer is here.
[http://ubuntuforums.org/showthread.php?t=1340312](http://ubuntuforums.org/showthread.php?t=1340312)

You should only post once for the same question as we need to see what others have posted to not not waste our time with duplicate answers. We are all volunteers here trying to help.

---

### Post by Nohtanhoj on 2009-11-28
Hooray for forum search! Saved me many times...

Anyway, good luck with fixing GRUB. It may be intimidating but it's rewarding if you manage to get it working. If booting from LiveCD doesn't work, give Super Grub Disk a try.

---

