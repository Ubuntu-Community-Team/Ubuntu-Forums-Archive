---
title: "Screwed up Vista boot with Super Grub"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by choochoo22 on 2009-11-28
The short version is; I tried installing a dual-boot of Mythbuntu 9.04 upgraded to 9.10 with Vista.  Both OS were bootable only with a Super Grub CD.  I tried to make the MBR bootable with Super Grub, which was a very bad idea since I really don't know what I am doing, and now Mythbuntu is still bootable only with Super Grub, Vista is unbootable and all files inaccessable.

The CPU is C2 duo on Gigabyte MOBO: [http://www.gigabyte.us/Products/Motherboard/Products_Overview.aspx?ProductID=2659]("http://www.gigabyte.us/Products/Motherboard/Products_Overview.aspx?ProductID=2659")

Vista is installed on a SATA raid with 2 Seagate 250gb drives that is invisible to Nautilus.  Mythbuntu 9.10 is on an IDE 40gb drive.  There is a separate 250gb SATA NTFS drive full of Vista files which is visible to nautilus.

I REALLY don't want to re-build the Vista system if it can be salvaged but I have run out of ideas.  Can this be fixed?

---

### Post by Mark Phelps on 2009-11-28
To fix your Vista boot, you would need to have a Vista install DVD, boot from it, and run Startup Repair three times.

If you don't have that DVD, go to the NeoSmart Technology forums, look for their recovery CD, download it and burn it.

You can boot from that to recover your Vista MBR.

---

### Post by phillw on 2009-11-28
A nice, gentle how-to is here .. [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)   but, as the above post states - you need a boot disk.

Regards,

phill.

---

### Post by choochoo22 on 2009-11-28
Thanks, I'll check into those suggestions.

I tried fixing it by booting my Vista installation disk with no success.  The "repair" option doesn't see the existing installation, the "install" option says it will destroy all files on the target, and the "upgrade" option requires it be run from an existing installation.

---

### Post by presence1960 on 2009-11-28
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by choochoo22 on 2009-11-28
The previous suggestions for repairing with the Vista install disk failed. The "repair" function can't see the existing installation even after loading the raid drivers.  The "install" function does see the disk once the drivers are loaded but it sees the disk as empty.

Here are the results of the boot info script.  I believe sda and sdb are the raid array where Vista is installed, sdc id the auxillary NTFS disk used with Vista, and sdd is where Karmic is installed:

```
============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd6: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xefbb15a7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,746,495   976,744,448   7 HPFS/NTFS

/dev/sda1 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8a57b74f

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   488,392,703   488,390,656   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 41.2 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders, total 80418240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf310f310

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63    20,852,369    20,852,307  83 Linux
/dev/sdd2          20,852,370    80,405,324    59,552,955   5 Extended
/dev/sdd5          20,852,433    22,651,649     1,799,217  82 Linux swap / Solaris
/dev/sdd6          22,651,713    80,405,324    57,753,612  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sdb: TYPE="jmicron_raid_member" 
/dev/sdc1: UUID="E03E49623E493338" LABEL="Backup" TYPE="ntfs" 
/dev/sdd1: UUID="a7d3d835-b380-4f56-9ce1-1e6a5295b380" TYPE="ext3" 
/dev/sdd5: UUID="7e0eb14a-ab18-4d5d-aba3-5d4a7c5485a0" TYPE="swap" 
/dev/sdd6: UUID="602e271a-add2-4317-be96-f8d3dc8253bd" TYPE="xfs" 

=============================== "mount" output: ===============================

/dev/sdd1 on / type ext3 (rw,errors=remount-ro)
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
/dev/sdd6 on /var/lib type xfs (rw)


=========================== sdd1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=a7d3d835-b380-4f56-9ce1-1e6a5295b380 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a7d3d835-b380-4f56-9ce1-1e6a5295b380

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

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		a7d3d835-b380-4f56-9ce1-1e6a5295b380
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=a7d3d835-b380-4f56-9ce1-1e6a5295b380 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		a7d3d835-b380-4f56-9ce1-1e6a5295b380
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=a7d3d835-b380-4f56-9ce1-1e6a5295b380 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic
uuid		a7d3d835-b380-4f56-9ce1-1e6a5295b380
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a7d3d835-b380-4f56-9ce1-1e6a5295b380 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid		a7d3d835-b380-4f56-9ce1-1e6a5295b380
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a7d3d835-b380-4f56-9ce1-1e6a5295b380 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, memtest86+
uuid		a7d3d835-b380-4f56-9ce1-1e6a5295b380
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd1 during installation
UUID=a7d3d835-b380-4f56-9ce1-1e6a5295b380 /               ext3    errors=remount-ro 0       1
# /var/lib was on /dev/sdd6 during installation
UUID=602e271a-add2-4317-be96-f8d3dc8253bd /var/lib        xfs     defaults        0       2
# swap was on /dev/sdd5 during installation
UUID=7e0eb14a-ab18-4d5d-aba3-5d4a7c5485a0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.28-11-generic
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.28-11-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: initrd.img
    .0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh 

```

---

### Post by presence1960 on 2009-11-28
Unfortunately I know nada about RAID, but the boot info script output is the right tool to see what is going on here. Hopefully someone knowledgeable in RAID will come along and respond.

Sorry I did not see your mention of SATA Raid. But at least you have the info from the script posted here. Good luck!

---

