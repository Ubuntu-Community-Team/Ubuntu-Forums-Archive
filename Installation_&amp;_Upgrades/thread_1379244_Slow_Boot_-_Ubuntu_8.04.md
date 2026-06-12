---
title: "Slow Boot - Ubuntu 8.04"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by gkaucher on 2010-01-12
I was given a Dell Dimension 4700 and I figured that I would wipe it clean and install Ubuntu 8.04. It seems to have installed successfully, but in booting up it takes too long, about 7 minutes!

My installation procedure to install was

1) Used dd from the PartedMagic disk to erase the entire disk.

2) Used Gparted from the PartedMagic disk to partition the 160GB HDD into
   /dev/sda1 for the Ubuntu 8.04 OS (about 15 GB)
   /dev/sda2 for the Home Directory (about 35 GB
   /dev/sda3 for the Swap file (1 GB)
   I left the remainder of the disk as unallocated, since I want to add
   a windows system later and set up dual boot.

3) I downloaded the 32 bit version of Ubuntu and installed it using my newly created partitons. I set the mount point for /dev/sda1 as /, and /dev/sda2 as /home. I requested ext 3 formatting for /dev/sda1 and /dev/sda2. I set the bootloader on /dev/sda1. 


The installation went fine, and I downloaded and installed the 141 upgrades. But it takes a long time to boot up. Here is what my fdisk -l looks like:
  

```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e2016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+  83  Linux
/dev/sda2            1913        6374    35841015   83  Linux
/dev/sda3            6375        6505     1052257+  82  Linux swap / Solaris

```


I installed startup manager, so I could see where the boot process seems to hang up. It seems to never really recognize root, and spends a lot of time installing the hardware drivers. But it does eventually get there. 

If there is something flawed in my installation procedure, I could easily reinstall at this point, since I don't have anything critical on the computer at this point.

Any suggestions appreciated.

Gary

---

### Post by gkaucher on 2010-01-12
Not sure if it matters or not, but here is a copy of my fstab. Is there anything that could be changed that might speed up the boot process?



```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fd32d54b-57d0-4889-b8d7-0d96bd2152d3 /    ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=8c194b9d-19ac-4153-afcb-5d465bfdedca /home           ext3    relatime        0       2
# /dev/sda3
UUID=0f7022d0-eb40-4138-882d-71a97eabe167 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by raymondh on 2010-01-12
I agree ... 7 minutes is too long.  My 9.04 is up by the 22nd second and at 'rest' by the 73rd (with wifi up).

From the tutorials and tips section ... though they may be for edgy, the ideas are the same for hardy.  Hope this can help.

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

Raymond

---

### Post by gkaucher on 2010-01-12
Thanks for the links Raymond. I am looking through them. Here are the results of using the Boot Info Script. Is there anything that looks like an obvious problem? Should I have installed the bootloader in /dev/sda or /dev/sda1? 

```
============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 20119615 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e2016

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    30,716,279    30,716,217  83 Linux
/dev/sda2          30,716,280   102,398,309    71,682,030  83 Linux
/dev/sda3         102,398,310   104,502,824     2,104,515  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="fd32d54b-57d0-4889-b8d7-0d96bd2152d3" TYPE="ext3" 
/dev/sda2: UUID="8c194b9d-19ac-4153-afcb-5d465bfdedca" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="0f7022d0-eb40-4138-882d-71a97eabe167" 
/dev/sda3: UUID="0f7022d0-eb40-4138-882d-71a97eabe167" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-26-generic/volatile type tmpfs (rw)
/dev/sda2 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/gary/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gary)


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
timeout		8

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
# kopt=root=UUID=fd32d54b-57d0-4889-b8d7-0d96bd2152d3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
# defoptions=splash

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=fd32d54b-57d0-4889-b8d7-0d96bd2152d3 ro splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=fd32d54b-57d0-4889-b8d7-0d96bd2152d3 ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=fd32d54b-57d0-4889-b8d7-0d96bd2152d3 ro splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=fd32d54b-57d0-4889-b8d7-0d96bd2152d3 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fd32d54b-57d0-4889-b8d7-0d96bd2152d3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=8c194b9d-19ac-4153-afcb-5d465bfdedca /home           ext3    relatime        0       2
# /dev/sda3
UUID=0f7022d0-eb40-4138-882d-71a97eabe167 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  10.2GB: boot/grub/menu.lst
  10.3GB: boot/grub/stage2
  10.3GB: boot/initrd.img-2.6.24-24-generic
  10.2GB: boot/initrd.img-2.6.24-24-generic.bak
  10.3GB: boot/initrd.img-2.6.24-26-generic
  10.3GB: boot/initrd.img-2.6.24-26-generic.bak
  10.3GB: boot/vmlinuz-2.6.24-24-generic
  10.2GB: boot/vmlinuz-2.6.24-26-generic
  10.3GB: initrd.img
  10.3GB: initrd.img.old
  10.2GB: vmlinuz
  10.3GB: vmlinuz.old
=============================== StdErr Messages: ===============================

ls: cannot access /dev/mapper: No such file or directory
```

---

### Post by raymondh on 2010-01-12
It could very well be.

BIOS will go through each and every bootable device to find a OS to boot.  HD > CD > Floppy > partitions.  It might help if you re-install GRUB in the MBR of the HD instead of it in the partition.

Just to share with you my set-up.  Grub is in the MBR of the HD.  I also have OSX in a partition.  Since OSX and GRUB do not see eye-to-eye, I had to install its' bootloader in the OSX partition and chainloaded that to GRUB. So, when I startup my system, and I want to use OSX, I select from GRUB which will then segue to the OSX boot process.  Net effect is that it does take some time (about 2 minutes from power-on) to load OSX and about 3 to get it at rest.

Raymond

---

### Post by gkaucher on 2010-01-12
Thanks. I'm still new at this. I wasn't sure when I answered the boatloader question in the advanced section of the install. I'm not "advanced" yet. It does seem as if the computer is "lost" during the long boot process, and it may indeed be searching through devices. 

Is there some kind of command that I can make in a terminal to reinstall grub. Do I need to do it from a live CD?  Do I designate /dev/sda as the bootloader, or hd0,0?

Thanks,

Gary

---

### Post by kansasnoob on 2010-01-12
Very simple, either from your installed Ubuntu or the Live CD go to terminal and:

```
sudo grub
```

```
root (hd0,0)
```

```
setup (hd0)
```

BTW those are zeros! You should see this:

> Checking if "/boot/grub/stage1" exists... **yes**
Checking if "/boot/grub/stage2" exists... **yes**
Checking if "/boot/grub/e2fs_stage1_5" exists... **yes**
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
**succeeded**
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... **succeeded**
Done. 

Then just run:

```
quit
```

Should be good to go!

---

### Post by gkaucher on 2010-01-12
Thanks. I ran the code, and almost got the same response (see below). The number 16 appears instead of 15 on two instances. Not sure if that matters. An asterisk is also missing.

```
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 16 sectors are embedded.
succeeded
Running "install /boot/grub/stage1  (hd0) (hd0)1+16 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.
```


I ran the Boot Script Info thing, and it appears that Grub was installed in the MBR of /dev/sda. Here is the output. Do I have to also remove grub from /dev/sda1? The boot speed did not change. Still 7 minutes.  Here is the output of the results.txt


```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 20119615 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e2016

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    30,716,279    30,716,217  83 Linux
/dev/sda2          30,716,280   102,398,309    71,682,030  83 Linux
/dev/sda3         102,398,310   104,502,824     2,104,515  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="fd32d54b-57d0-4889-b8d7-0d96bd2152d3" TYPE="ext3" 
/dev/sda2: UUID="8c194b9d-19ac-4153-afcb-5d465bfdedca" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="0f7022d0-eb40-4138-882d-71a97eabe167" 
/dev/sda3: UUID="0f7022d0-eb40-4138-882d-71a97eabe167" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-26-generic/volatile type tmpfs (rw)
/dev/sda2 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/gary/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gary)


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
timeout		8

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
# kopt=root=UUID=fd32d54b-57d0-4889-b8d7-0d96bd2152d3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
# defoptions=splash

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=fd32d54b-57d0-4889-b8d7-0d96bd2152d3 ro splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=fd32d54b-57d0-4889-b8d7-0d96bd2152d3 ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=fd32d54b-57d0-4889-b8d7-0d96bd2152d3 ro splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=fd32d54b-57d0-4889-b8d7-0d96bd2152d3 ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fd32d54b-57d0-4889-b8d7-0d96bd2152d3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=8c194b9d-19ac-4153-afcb-5d465bfdedca /home           ext3    relatime        0       2
# /dev/sda3
UUID=0f7022d0-eb40-4138-882d-71a97eabe167 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  10.2GB: boot/grub/menu.lst
  10.3GB: boot/grub/stage2
  10.3GB: boot/initrd.img-2.6.24-24-generic
  10.2GB: boot/initrd.img-2.6.24-24-generic.bak
  10.3GB: boot/initrd.img-2.6.24-26-generic
  10.3GB: boot/initrd.img-2.6.24-26-generic.bak
  10.3GB: boot/vmlinuz-2.6.24-24-generic
  10.2GB: boot/vmlinuz-2.6.24-26-generic
  10.3GB: initrd.img
  10.3GB: initrd.img.old
  10.2GB: vmlinuz
  10.3GB: vmlinuz.old
=============================== StdErr Messages: ===============================

ls: cannot access /dev/mapper: No such file or directory
```

---

### Post by gkaucher on 2010-01-13
Still no luck in improving the boot speed. It still takes about 7 minutes. In watching the text during the boot process, it seems to be held up by 

1)Mounting the root file system
2)Waiting for the root file system
3)something about scripts
4)Loading hardware drivers

Do I have to edit the fstab file or something in order to get the grub change that I made work properly? 

Thanks,

Gary

---

### Post by gkaucher on 2010-01-13
It seems as though I added grub to the MBR on /dev/sda. Do I still need to do something to remove grub from /dev/sda1? 

Should I also edit some file (fstab or menu.1st?).

Thanks for the help.

---

### Post by wrose51106 on 2010-01-13
Whats the system specs?

---

### Post by gkaucher on 2010-01-13
Dell Dimension 4700

Intel(R) Pentium(R) 4 CPU 3.20 GHz
512MB of DDR2 SDRAM (400 MHz)
160GB SATA HDD
16X DVD-ROM/48X/24X/48X CD-RW combo drive
integrated graphics

---

### Post by wrose51106 on 2010-01-13
Just out of curiosity, can you disable HT in the BIOS?

-Bill

---

### Post by gkaucher on 2010-01-13
Thanks for the suggestion. I'll try anything at this point. I may even reinstall, since there is nothing to lose on the computer.

HT was set "on" in the BIOS even though the factory default is "off". So I set it to "off", but the boot time was still as slow as before. Most of the time delay that occurs during the boot occurs when there is not an "OK" response from the StartupManager text in these items:

1) Mounting root filesystem
2) Waiting for root filesystem
3) Running scripts - init - bottom
4) Setting the system clock
5) Loading hardware drivers

Other than this 7 minute boot, it seems to work fine,

Gary

---

### Post by wrose51106 on 2010-01-13
I am by no means that good at Linux, but been repairing PC's for over ten years. My logical guess would be there is a hardware conflict, I would start by checking for BIOS updates, then load defaults. Do you have multiple optical drives? Is there some funky add-in card in there?

-Bill

---

### Post by Retry13 on 2010-01-13
FWIW, I had a similar problem with Puppy taking 13 min to boot; turned out to be a dying hard drive.  You might try a quick install of Puppy or some other easy install to the hard drive and see how long it takes to boot.

Hope this is of some help.

Regards,  Retry13

---

### Post by gkaucher on 2010-01-15
The computer is currently running its original Dell Bios version A06, and the most recent version available from Dell is A10. In reading the issues resolved in the versions leading up to A10 I saw one reference to improving the ability to handle large hard drives. I'm not sure if that's my problem here or not.

The computer does have both a CD drive and a DVD drive. I don't think there is any kind of add-on card, but I will check.

I suppose the HDD could have some problems, although it seems to work ok after it boots up. The computer is around 5 years old, so anything is possible.

---

### Post by gkaucher on 2010-01-16
I upgraded the BIOS from version A06 to A10, but it still takes 7 minutes to boot.

I noticed that it wasn't keeping time correctly in the BIOS  so I changed the CMOS battery. While I had the case open, I reset the CMOS using the jumper. But none of this made any difference. Still 7 minutes.

Awhile back I added grub to the MBR on /dev/sda. Do I still need to do something to remove grub from /dev/sda1? Do any files need to be edited?

Thanks,

Gary

---

### Post by Sylslay on 2010-01-16
I would go for standard installation (withaout manual partitionig), before check any hardware issue.

PS. I read all story.
I kow that even 7 years old Mobo, run ok with 250GB IDE, It all depend on BIOS

---

