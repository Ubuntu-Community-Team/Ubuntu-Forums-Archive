---
title: "trashed grub with Windows 7 install"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by daswizard on 2010-03-30
Help.  I had an open partition on my laptop and decided to install Win 7 to it.  I figured it'd trash grub, but thought I could boot from USB and repair the problem.  Nope!  Now, when I boot from the HD I get the grub rescue prompt and I'm stuck.  Ran the boot info script and here are the results.  

	```
Boot Info Script 0.55    dated February 15th, 2010                     
 ============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
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
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 PwnSauce
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0177e1d7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       465,884       465,822   b W95 FAT32
/dev/sda2         225,841,770   329,380,694   103,538,925  83 Linux
/dev/sda3             465,885   225,841,769   225,375,885   5 Extended
/dev/sda5             465,948   191,944,619   191,478,672  83 Linux
/dev/sda6         216,588,393   225,841,769     9,253,377  82 Linux swap / Solaris
/dev/sda7         191,944,683   216,588,329    24,643,647  83 Linux
/dev/sda4         329,380,695   390,716,864    61,336,170   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107860992 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773166 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00087a33

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    10,233,404    10,233,342   b W95 FAT32
/dev/sdb2          20,482,875   976,768,064   956,285,190   7 HPFS/NTFS
/dev/sdb3          10,233,405    20,482,874    10,249,470  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       c836cdb4-815f-4e31-889a-3bbf607b4a7f   ext3                                     
/dev/sda1        17F7-717B                              vfat                                     
/dev/sda2        4b4727df-528e-4365-909d-bd1e5d66ed6d   ext3       sda2                          
/dev/sda4        8A02454702453A09                       ntfs                                     
/dev/sda5        f9e6797a-3b18-4e28-9351-78bd0264dec2   ext3                                     
/dev/sda6        7d8aff4a-4ece-4ed9-9166-62607bb44f6d   swap                                     
/dev/sda7        3d11d811-eaf0-4a6b-a306-1eb1db66b10a   ext3                                     
/dev/sdb1        0C5C-6366                              vfat       UBUNTU                        
/dev/sdb2        7860629B6062603C                       ntfs       FreeAgent                     
/dev/sdb3        f1913854-9309-49f4-bcad-32488fb11563   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb2        /media/FreeAgent         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


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
# kopt=root=UUID=f9e6797a-3b18-4e28-9351-78bd0264dec2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f9e6797a-3b18-4e28-9351-78bd0264dec2

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

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		f9e6797a-3b18-4e28-9351-78bd0264dec2
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=f9e6797a-3b18-4e28-9351-78bd0264dec2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		f9e6797a-3b18-4e28-9351-78bd0264dec2
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=f9e6797a-3b18-4e28-9351-78bd0264dec2 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		f9e6797a-3b18-4e28-9351-78bd0264dec2
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=f9e6797a-3b18-4e28-9351-78bd0264dec2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		f9e6797a-3b18-4e28-9351-78bd0264dec2
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=f9e6797a-3b18-4e28-9351-78bd0264dec2 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		f9e6797a-3b18-4e28-9351-78bd0264dec2
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=f9e6797a-3b18-4e28-9351-78bd0264dec2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		f9e6797a-3b18-4e28-9351-78bd0264dec2
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=f9e6797a-3b18-4e28-9351-78bd0264dec2 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		f9e6797a-3b18-4e28-9351-78bd0264dec2
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=f9e6797a-3b18-4e28-9351-78bd0264dec2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		f9e6797a-3b18-4e28-9351-78bd0264dec2
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=f9e6797a-3b18-4e28-9351-78bd0264dec2 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		f9e6797a-3b18-4e28-9351-78bd0264dec2
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=f9e6797a-3b18-4e28-9351-78bd0264dec2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		f9e6797a-3b18-4e28-9351-78bd0264dec2
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=f9e6797a-3b18-4e28-9351-78bd0264dec2 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		f9e6797a-3b18-4e28-9351-78bd0264dec2
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=f9e6797a-3b18-4e28-9351-78bd0264dec2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		f9e6797a-3b18-4e28-9351-78bd0264dec2
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=f9e6797a-3b18-4e28-9351-78bd0264dec2 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, memtest86+
uuid		f9e6797a-3b18-4e28-9351-78bd0264dec2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

UUID=4b4727df-528e-4365-909d-bd1e5d66ed6d /media/sda2 ext3 defaults 0 0
UUID=f9e6797a-3b18-4e28-9351-78bd0264dec2 / ext3 defaults 0 1
UUID=7d8aff4a-4ece-4ed9-9166-62607bb44f6d swap swap sw 0 0

=================== sda5: Location of files loaded by Grub: ===================


  93.0GB: boot/grub/core.img
  93.0GB: boot/grub/menu.lst
  93.0GB: boot/grub/stage2
  93.1GB: boot/initrd.img-2.6.31-14-generic
  93.0GB: boot/initrd.img-2.6.31-15-generic
  29.1GB: boot/initrd.img-2.6.31-16-generic
  29.2GB: boot/initrd.img-2.6.31-17-generic
  20.8GB: boot/initrd.img-2.6.31-19-generic
    .6GB: boot/initrd.img-2.6.31-20-generic
  93.0GB: boot/vmlinuz-2.6.31-14-generic
  93.1GB: boot/vmlinuz-2.6.31-15-generic
  29.2GB: boot/vmlinuz-2.6.31-16-generic
  20.5GB: boot/vmlinuz-2.6.31-17-generic
  29.1GB: boot/vmlinuz-2.6.31-19-generic
  67.5GB: boot/vmlinuz-2.6.31-20-generic
    .6GB: initrd.img
  20.8GB: initrd.img.old
  67.5GB: vmlinuz
  29.1GB: vmlinuz.old

=========================== sda7/boot/grub/menu.lst: ===========================

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
timeout		10

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
# kopt=root=UUID=3d11d811-eaf0-4a6b-a306-1eb1db66b10a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3d11d811-eaf0-4a6b-a306-1eb1db66b10a

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

splashimage=3d11d811-eaf0-4a6b-a306-1eb1db66b10a/boot/grub/splash.xpm.gz

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.10, kernel 2.6.31-19-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=f9e6797a-3b18-4e28-9351-78bd0264dec2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=f9e6797a-3b18-4e28-9351-78bd0264dec2 ro single 
initrd		/boot/initrd.img-2.6.31-19-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.10, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		Ubuntu 8.10, kernel 2.6.30.9
uuid		3d11d811-eaf0-4a6b-a306-1eb1db66b10a
kernel		/boot/vmlinuz-2.6.30.9 root=UUID=3d11d811-eaf0-4a6b-a306-1eb1db66b10a ro quiet splash 
initrd		/boot/initrd.img-2.6.30.9
quiet

title		Ubuntu 8.10, kernel 2.6.30.9 (recovery mode)
uuid		3d11d811-eaf0-4a6b-a306-1eb1db66b10a
kernel		/boot/vmlinuz-2.6.30.9 root=UUID=3d11d811-eaf0-4a6b-a306-1eb1db66b10a ro  single
initrd		/boot/initrd.img-2.6.30.9

title		Ubuntu 8.10, memtest86+
uuid		3d11d811-eaf0-4a6b-a306-1eb1db66b10a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=3d11d811-eaf0-4a6b-a306-1eb1db66b10a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=7d8aff4a-4ece-4ed9-9166-62607bb44f6d none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 105.8GB: boot/grub/core.img
 105.9GB: boot/grub/menu.lst
 105.8GB: boot/grub/stage2
 105.8GB: boot/initrd.img-2.6.30.9
 105.8GB: boot/vmlinuz-2.6.30.9
 105.8GB: initrd.img
 105.8GB: vmlinuz 
```

Thanks for your help!

---

### Post by oldfred on 2010-03-30
You have both grub2 and grub legacy parts. Grub2 is in the MBR but no grub.cfg to boot from. You still have grub legacy's menu.lst.

Do you want sda5 or sda7 as your boot? both seem to have the mixed grubs.

I do not know if there is an easier way but the full chroot will work from a liveCd. # are comments

Of course you must first know what partition you want to mount, in this example I'm using sda5:

sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
sudo apt-get update && sudo apt-get upgrade  #this updates everything
apt-get dist-upgrade     #would upgrade you to the latest kernel in the repositories
#purge old and new 
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
# installs grub2
apt-get install grub-pc grub-common
apt-get install --reinstall grub-pc
grub-install /dev/sda
grub-install --recheck /dev/sda
update-grub
#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

### Post by daswizard on 2010-03-30
Thanks, Oldfred.  That got me back into Ubuntu and I ran update-grub after I got in.  However, it wouldn't recognize the Windows 7 installation in sda4 for some reason...  Is there a way I can work around it?
Thanks!

---

### Post by oldfred on 2010-03-30
Your windows boots from sda1, or you are missing the boot files that are in sda1 and not in sda4. Try the sudo update-grub again, but if not then it is probably saying there is a problem with the win7 that needs repair before it will see it. Your sda1 does not look like at standard 100mb boot partition. Win7 installs two partitions with a clean install or will install in one partition if the partition is created in advance. Boot flag is also on sda1.

---

### Post by hobo on 2010-03-31
The same exact problem happened to me. I tried to fix the MBR for w7 but the (bootsect.exe) was not on my Recovery disk using W7 Home Ultimate. So I had to reinstall W7 from an image I made.
There are three partitions on the disk from the HP factory. 1 System hidden, W7 and a Factory Image.
Can W7 and Grub 2 coexist? If so how?
This new HP computer is sweet and I really would like to get 10.04 up and running with 3 linux partitions... /os , /home ,/swap.

btw...I am not sure why this thread shows (solved) I don't see a solution.

hobo

---

### Post by oldfred on 2010-03-31
hobo,

I think daswizard got back into his system so he posted solved. Not sure if the last update-grub found his win7 or not.

Since this is solved not many look at it to contribute help, just looking for solutions. You may do better with a total new thread of your own and a title related to grub2 finding win7. Many seem to have dual booted Vista or Win7. There have been issues with some windows software that writes hidden data into the MBR. Grub2 is slightly larger than the windows boot loader or old grub so that writing into the MBR can corrupt grub2. Software should not be writing hidden info in the MBR.

---

### Post by daswizard on 2010-04-01
What worked for me, after I recovered the system using Oldfred's suggestions, was to follow the instructions found [Here]("https://help.ubuntu.com/community/WindowsDualBoot") for Installing Windows after Ubuntu.  Specifically "[Master Boot Record backup and re-replacement]("https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement")" where you backup your MBR on your Ubuntu system, install Windows, then boot from a live CD and replace the MBR with the backup previously referenced.  Then I booted into Ubuntu, ran [FONT=Courier New]sudo update-grub[/FONT] and it found the Windows loader and added it to the grub boot menu.  No problem!

---

### Post by oldfred on 2010-04-01
the procedure daswizard followed works as it just makes a bit for bit copy of the MBR. But it has become so easy to reinstall grub2 from the liveCD that I usually just recommend the  reinstall of grub.

Old grub usually requires the chroot method which is a lot of commands, grub2 rarely requires the full chroot version to reinstall.

---

### Post by hobo on 2010-04-06
Thanks for updating this thread. Instead of having a real dual boot, I set my new machine up with 2 separate drives. One with 9.10 and the other with the factory installed W7. I can select, at boot time, where I want to go. The rest of the family can just boot straight to W7 or not. I also setup a shared drive so my music can be seen by both OSs. I intend to leave 10.04 to my 'test' laptop for now.

btw...W7 won't recognize a partition unless 'IT' formats it. hmmm?

hobo

---

