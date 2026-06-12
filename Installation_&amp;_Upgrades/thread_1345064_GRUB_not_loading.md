---
title: "GRUB not loading"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by trumpetgod on 2009-12-03
After a fresh install of Windows 7 x64, I successfully installed Ubuntu 8.04 (it's old, I know. I was just planning to update to the latest version once it was installed).  However, when the GRUB would normally show (I have ubuntu on my other two computers), GRUB does not load, it just goes straight into Windows 7.  I booted into the live CD and checked menu.lst, and the timer for the GRUB is 10, so it is not defaulting into Windows 7 because the timer is 0.  Other suggestions?

Other info: I am only using one 500GB 7200rpm Seagate hard drive

---

### Post by presence1960 on 2009-12-03
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by trumpetgod on 2009-12-03
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02180a83

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,465,144,064 1,465,144,002   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x964d9a8a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   904,111,144   903,904,297   7 HPFS/NTFS
/dev/sdb3         904,122,135   976,768,064    72,645,930   5 Extended
/dev/sdb5         904,122,198   973,683,584    69,561,387  83 Linux
/dev/sdb6         973,683,648   976,768,064     3,084,417  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="EXTERNAL" UUID="10D8-132E" TYPE="vfat" 
/dev/sdb1: UUID="CA5CCE835CCE6A31" LABEL="System Reserved" TYPE="ntfs" 
/dev/sdb2: UUID="1878E0C878E0A62A" TYPE="ntfs" 
/dev/sdb5: UUID="7eae72c5-d3e6-44f0-ba96-af701baa4195" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="3737e883-9d31-4666-8b03-2d76ef7ef1bb" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=7eae72c5-d3e6-44f0-ba96-af701baa4195 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7eae72c5-d3e6-44f0-ba96-af701baa4195 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7eae72c5-d3e6-44f0-ba96-af701baa4195 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=7eae72c5-d3e6-44f0-ba96-af701baa4195 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=3737e883-9d31-4666-8b03-2d76ef7ef1bb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 467.0GB: boot/grub/menu.lst
 467.1GB: boot/grub/stage2
 467.1GB: boot/initrd.img-2.6.24-19-generic
 467.1GB: boot/vmlinuz-2.6.24-19-generic
 467.1GB: initrd.img
 467.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo/sda1: device is busy
umount: /tmp/BootInfo/sda1: device is busy
```

EDIT: the 750gb drive is an external eSATA drive

---

### Post by darkod on 2009-12-03
Somehow grub ended up installed on the 750GB drive. Your computer is booting from the 500GB drive which has the win7 bootloader and boots win7 straight away.

I guess the best is to reinstall grub on the 500GB drive, /dev/sdb. Looking for nice tutorial right now. :)

Running in terminal
sudo grub-install /dev/sdb

should do the trick.

---

### Post by darkod on 2009-12-03
In fact, you might need to do the following after booting with the 8.04 livecd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by trumpetgod on 2009-12-03
running in terminal:

```
sudo grub-install /dev/sdb
```

gives:

Could not find device for /boot: Not found or not a block device.

---

### Post by trumpetgod on 2009-12-03
The tutorial at [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) seemed to be successful.  However, on reboot (I tried rebooting with and without external drive connected), there was no change, Windows 7 still boots unchallenged.

---

### Post by presence1960 on 2009-12-03
Do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,4)". 
5. Type "root (hd1,4)"
6. Type "setup (hd1)", to install GRUB to MBR
7. Quit grub by typing "quit".

```

Open a file browser and mount your Ubuntu root partition by clicking on it in the left pane. Once directories show on right it is mounted. 

Now open a terminal and run > gksu nautilus. Mount your ubuntu root partition on left pane and on the right navigate to /boot/grub/menu.lst. Open menu,lst file and change this:

```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7eae72c5-d3e6-44f0-ba96-af701baa4195 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7eae72c5-d3e6-44f0-ba96-af701baa4195 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

TO:

```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7eae72c5-d3e6-44f0-ba96-af701baa4195 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7eae72c5-d3e6-44f0-ba96-af701baa4195 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
chainloader	+1
```

Close file and reboot.

When rebooting go into BIOS and make the sdb disk (500 GB) first to boot in the hard disk boot order. Save changes to CMOS and continue booting. You should be good to go.

You want GRUB on the external disk so if you boot without the external plugged in it will go right to windows. if you boot with the external plugged in you will get GRUB and boot into Ubuntu.

---

