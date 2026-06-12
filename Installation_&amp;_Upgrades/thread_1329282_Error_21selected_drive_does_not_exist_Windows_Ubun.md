---
title: "Error 21:selected drive does not exist Windows Ubuntu dual boot"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by drunkenbrawler on 2009-11-17
Hello everyone,
I'm new to Ubuntu and i'm facing a weird problem and dont know what to do.

I had 2 hard discs. One 80 GB PATA and a 160 GB SATA. I have Windows XP and Ubuntu-9.4 on my 80 GB hard disc. Currently my 160 GB disc crashed and I started getting > "GRUB READ ERROR"

After that I removed my crashed Harddisc and then PC automatically booted in Windows (No GRUB menu). I was not getting GRUB menu so I inserted Live CD and did following steps
```

sudo grub
find /boot/grub/stage1
```
then I noted returned location and did
```
root (hd#,#)
```
(where #,# is returned location like (hd0,1) but I dont remember exactly what it was
then I did
```
setup (hd0)
quit
```

This did it and I got Grub menu and started booting correctly. Then I tried to connect my crashed HDD and surprisinly it worked one time. After that when I try to boot in Windows, I get error saying
> Error 21: Selected disc does not exists.
Press any key to continue...

When I press any key, PC restarts. I dont know what to do. I am able to boot and work in Ubuntu but not in Windows. I have removed my SATA 160 GB disc. but I am not able to do anything about Windows. Please help... I need Windows to work on my academic software project.
Thanx

---

### Post by presence1960 on 2009-11-17
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.35 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by drunkenbrawler on 2009-11-17
Here are contents of Result.txt. Thanx for ur reply....

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe99ee99e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750    79,971,569    39,005,820  83 Linux
/dev/sda3          79,971,570   156,360,644    76,389,075   5 Extended
/dev/sda5          81,931,563   156,360,644    74,429,082   7 HPFS/NTFS
/dev/sda6          79,971,696    81,931,499     1,959,804  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="12EC1C0EEC1BEB2D" TYPE="ntfs" 
/dev/sda2: UUID="b32a2ed4-c12b-4bf3-afb6-2cc9e9739f19" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="0023937A0DA29709" LABEL="Downloads" TYPE="ntfs" 
/dev/sda6: TYPE="swap" UUID="6d924159-855d-412c-927d-46e9d04fa8b1" 

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
/dev/sr1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
# kopt=root=UUID=b32a2ed4-c12b-4bf3-afb6-2cc9e9739f19 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b32a2ed4-c12b-4bf3-afb6-2cc9e9739f19

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

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        b32a2ed4-c12b-4bf3-afb6-2cc9e9739f19
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=b32a2ed4-c12b-4bf3-afb6-2cc9e9739f19 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        b32a2ed4-c12b-4bf3-afb6-2cc9e9739f19
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=b32a2ed4-c12b-4bf3-afb6-2cc9e9739f19 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        b32a2ed4-c12b-4bf3-afb6-2cc9e9739f19
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=b32a2ed4-c12b-4bf3-afb6-2cc9e9739f19 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        b32a2ed4-c12b-4bf3-afb6-2cc9e9739f19
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=b32a2ed4-c12b-4bf3-afb6-2cc9e9739f19 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        b32a2ed4-c12b-4bf3-afb6-2cc9e9739f19
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b32a2ed4-c12b-4bf3-afb6-2cc9e9739f19 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        b32a2ed4-c12b-4bf3-afb6-2cc9e9739f19
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b32a2ed4-c12b-4bf3-afb6-2cc9e9739f19 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        b32a2ed4-c12b-4bf3-afb6-2cc9e9739f19
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=b32a2ed4-c12b-4bf3-afb6-2cc9e9739f19 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=6d924159-855d-412c-927d-46e9d04fa8b1 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  38.2GB: boot/grub/menu.lst
  38.2GB: boot/grub/stage2
  38.2GB: boot/initrd.img-2.6.28-11-generic
  38.1GB: boot/initrd.img-2.6.28-15-generic
  38.2GB: boot/initrd.img-2.6.28-16-generic
  38.1GB: boot/vmlinuz-2.6.28-11-generic
  38.2GB: boot/vmlinuz-2.6.28-15-generic
  38.2GB: boot/vmlinuz-2.6.28-16-generic
  38.2GB: initrd.img
  38.1GB: initrd.img.old
  38.2GB: vmlinuz
  38.2GB: vmlinuz.old

```

---

### Post by presence1960 on 2009-11-17
Boot into Ubuntu and open a terminal, run this command ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst

Scroll to the bottom where the windows entry is. Change this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```



TO:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
rootnoverify    (hd0,0)
chainloader     +1

```

Click Save on the top toolbar & close file. reboot & try windows booting windows again.

---

### Post by drunkenbrawler on 2009-11-17
Thanks a lot... that did it....
it will be nice if you can tell me what you did... :)

---

### Post by presence1960 on 2009-11-17
> **drunkenbrawler said:**
> Thanks a lot... that did it....
it will be nice if you can tell me what you did... :)

Ok, looking at your boot info script it looks like the 160 Gb disk you removed booted first and had GRUB installed on it. When you removed that your machine would boot into Windows because it's bootloader was on MBR of 80 GB disk. This is supported by the fact that your menu.lst in Ubuntu (sda2) looked like this:
```

# This entry automatically added by the Debian installer for a non-linux OS
# [COLOR="DarkRed"]on /dev/sdb1[/COLOR]
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
[COLOR="DarkRed"]map        (hd0) (hd1)
map        (hd1) (hd0)[/COLOR]
chainloader    +1
```

Note it says your windows is installed on sdb1- this means your 160 GB disk was booting first and was designated as (hd0). That is where the map lines came in. Windows needs to be on a primary partition on the first disk that boots. When 160 GB disk booted first you needed the map lines to "trick" or "entice" windows into thinking the disk it is installed on boots first.

Now you have the 80 GB disk only so that disk now becomes (hd0). So windows is no longer on (hd1,0) it is now on (hd0,0).

Since windows is now on the first disk that boots you no longer need the map lines.

Savedefault & makeactive really aren't necessary.

GRUB now takes over at boot because earlier you put it on MBR of the 80 GB disk with the operation you posted originally.

Any other questions ask!

---

### Post by drunkenbrawler on 2009-11-18
OK... Now I understand what happened... thanks again... I'm complete nOob to this all but I like to learn these things :)

---

