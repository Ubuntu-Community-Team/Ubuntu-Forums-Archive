---
title: "Grub Error"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by stepstools on 2010-01-13
So, I had 9.04 (Upgraded to 9.10), but I wanted to do a clean install of 9.10.  I got a 9.10 CD through ShipIt to ensure there were no download/burning errors.  So I ran through the prompts, and it looked as if everything had installed OK.  But when I go to boot, I get a message from GRUB that says - Error: No Such Device d358c5d7-9426-4ac2-a93a-9d8a28beb67a  Any ideas?  I have a presentation on Ubuntu next Thursday, so quick help is needed!

---

### Post by presence1960 on 2010-01-13
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by stepstools on 2010-01-14
Here it is - 
```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 32.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007468b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   306,664,784   306,664,722  83 Linux
/dev/sda2         306,664,785   312,576,704     5,911,920   5 Extended
/dev/sda5         306,664,848   312,576,704     5,911,857  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa4b57300

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1002 MB, 1002438656 bytes
65 heads, 32 sectors/track, 941 cylinders, total 1957888 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     1,957,887     1,957,856   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="009f68d5-74ee-425f-9400-597b25d4c15b" TYPE="ext3" 
/dev/sda5: UUID="4a211576-299d-4914-85c9-989d00745f6d" TYPE="swap" 
/dev/sdb1: UUID="526837A6683787AD" LABEL="FreeAgent Drive" TYPE="ntfs" 
/dev/sdc1: LABEL="Back-Up" UUID="BD83-F2B3" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-17-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jeremy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jeremy)
/dev/sdc1 on /media/Back-Up type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=jeremy)
/dev/sdb1 on /media/FreeAgent Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda1/boot/grub/menu.lst: ===========================

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# root		(hd0,1)
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
# kopt=root=UUID=009f68d5-74ee-425f-9400-597b25d4c15b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=009f68d5-74ee-425f-9400-597b25d4c15b

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
# defoptions=quiet

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

title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		009f68d5-74ee-425f-9400-597b25d4c15b
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=009f68d5-74ee-425f-9400-597b25d4c15b ro quiet 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		009f68d5-74ee-425f-9400-597b25d4c15b
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=009f68d5-74ee-425f-9400-597b25d4c15b ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		009f68d5-74ee-425f-9400-597b25d4c15b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=009f68d5-74ee-425f-9400-597b25d4c15b ro quiet 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		009f68d5-74ee-425f-9400-597b25d4c15b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=009f68d5-74ee-425f-9400-597b25d4c15b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		009f68d5-74ee-425f-9400-597b25d4c15b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=009f68d5-74ee-425f-9400-597b25d4c15b /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4a211576-299d-4914-85c9-989d00745f6d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  14.3GB: boot/grub/menu.lst
  14.4GB: boot/grub/stage2
  14.4GB: boot/initrd.img-2.6.28-11-generic
  14.3GB: boot/initrd.img-2.6.28-17-generic
  14.4GB: boot/vmlinuz-2.6.28-11-generic
  14.4GB: boot/vmlinuz-2.6.28-17-generic
  14.3GB: initrd.img
  14.4GB: initrd.img.old
  14.4GB: vmlinuz
  14.4GB: vmlinuz.old
```

Thanks for the quick response!

---

### Post by darkod on 2010-01-14
It seems grub1 is still there somehow and looking for partition with UUID that doesn't exist any more.
When you reinstalled 9.10 clean, did you use the Erase and use whole disk option? Or what?

---

### Post by presence1960 on 2010-01-14
you do not have 9.10 installed. you have 9.04. Something must have gone wrong with the installation. Reinstall from 9.10 CD and at the partitioner window choose use entire disk.

---

### Post by stepstools on 2010-01-14
I re-installed 9.04 as a stable release.

---

### Post by Leppie on 2010-01-14
which entry were you trying to boot?

---

### Post by presence1960 on 2010-01-14
> **stepstools said:**
> I re-installed 9.04 as a stable release.

?????

---

### Post by stepstools on 2010-01-15
Hey, a guy needs a computer to use!  So what now?

---

### Post by Leppie on 2010-01-15
maybe try to clarify which release you are using and what you are trying to boot using which version of grub?

---

### Post by darkod on 2010-01-15
> **stepstools said:**
> Hey, a guy needs a computer to use!  So what now?

That guy should answer few of our questions because we don't have a crystal ball to know what he did.
I asked whether you used Erase and use whole disk option because that would wipe the disk. You didn't reply anything. I suspect you reinstalled but without formatting and now you have a mix up of old and new files.

Not sure, but I think just a grub1 reinstall on the MBR of /dev/sda might help you. Otherwise the boot files look fine.

Follow the procedure here for 9.04 version and make sure you use 9.04 cd:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

