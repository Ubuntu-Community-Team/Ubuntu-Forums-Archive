---
title: "cannot boot into ubuntu after installing it in a vista machine"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by ububtunovice on 2008-11-26
I installed Ubuntu 8.10 on top of Windows Vista from the Live CD. (I thought that it would uninstall Vista from the machine)
Now when I start the computer, I do not see any grub options, but 
rather go straight to Windows Boot Manager which displays the message that says that Windows has failed to start. I cannot even repair Vista using the reinstallation DVD that came with it. Not sure what to do. Any help as to how to boot into Ubuntu? 

Thanks!

---

### Post by __Ryan__ on 2008-11-26
You need to install the grub bootloader, for some reason it didn't happen during the installation.  

Fire up the LiveCD and run:

```
sudo grub-install /dev/sda
```

You need to replace "/dev/sda" with the correct drive where your Linux system resides.  It may be /dev/hda or something similar.

---

### Post by ububtunovice on 2008-11-27
thanks!....i have two hard drives and i have installed ubuntu 8.10 in each of them...but now when i reboot my system, grub hangs saying "loading stage 1.5...please wait"...what might be going wrong?

---

### Post by caljohnsmith on 2008-11-27
How about first posting:
```
sudo fdisk -lu
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
Also, do you have a preference of which Ubuntu is in control of the booting process? And just out of curiosity, why do you have Ubuntu 8.10 installed on both drives?

---

### Post by ububtunovice on 2008-12-26
Sorry for this very late response. I was on a vacation till now and did not have access to my computer.

Here is the output:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30000000

  Device	     Boot	  Start	     End	 Blocks	    Id	  System
/dev/sda1             *             63     605441654   302720796    83     Linux
/dev/sda2                       605441655  625137344     9847845     5    Extended
/dev/sda5                       605441718  625137344     9847813+   82    Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30000000

  Device	     Boot	  Start	     End	 Blocks	    Id	  System
/dev/sdb1                          63      605441654   302720796    83     Linux
/dev/sdb2                       605441655  625137344     9847845     5    Extended
/dev/sdb5                       605441718  625137344     9847813+   82    Linux swap / Solaris

ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB
ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
ff00

ubuntu@ubuntu:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
ff00

I installed Ubuntu on one of the drives and it did not work; so I installed it on both the drives. Also, I am not sure how to find out which Ubuntu is in control of the booting process.

Thanks so much!

---

### Post by caljohnsmith on 2008-12-26
Hope you had a good vacation. :) I'm not seeing though how you could be getting Windows boot manager at this point, unless Vista is on another drive different than sda or sdb; both sda and sdb have Grub installed to their MBRs (Master Boot Records), so you should get Grub on start up. Just to clarify, you're saying on start up, you don't get Grub, but somehow still get a message about Vista failing to start? 

In order to get a better picture of your setup, how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by ububtunovice on 2008-12-28
I do get grub on start up but it hangs saying "loading stage 1.5...please wait"...

The computer I am trying to set up ubuntu on is not yet connected to the internet...so I can't use wget to obtain boot_info_script.txt...is there some specific commands that you would like me to run to understand my problem better?

Thanks so much for your prompt replies! Its keeping me excited about setting up ubuntu on my machine :)

---

### Post by caljohnsmith on 2008-12-28
OK, from whichever computer has internet access, how about right-clicking [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script, select "save target as...", save the "boot_info_script.txt" to that computer, transfer it to the Desktop of the Ubuntu computer, and then run it with:
```
sudo bash ~/Desktop/boot*.txt
```
Let me know how that goes.

---

### Post by ububtunovice on 2008-12-29
Here is the contents of RESULTS.txt file: 

============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for its boot files.
 => Grub is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for its boot files.
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   605441654   302720796   83  Linux
/dev/sda2       605441655   625137344     9847845    5  Extended
/dev/sda5       605441718   625137344     9847813+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   605441654   302720796   83  Linux
/dev/sdb2       605441655   625137344     9847845    5  Extended
/dev/sdb5       605441718   625137344     9847813+  82  Linux swap / Solaris

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders, total 2015232 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              32     2015231     1007600    e  W95 FAT16 (LBA)

sfdisk -V /dev/sdc:

Warning: partition 1 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="515b576b-f65d-4a2f-8e46-971adec64541" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="ce76ce4b-bccc-487e-8f7a-73462eaf6519" TYPE="swap" 
/dev/sdb1: UUID="26c6cbc1-9981-4400-8dbb-211a40323e9f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="28b27fb7-13c2-43e7-84bd-6cf45cf1216a" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc1: SEC_TYPE="msdos" UUID="64B9-10C7" TYPE="vfat" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

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
# kopt=root=UUID=515b576b-f65d-4a2f-8e46-971adec64541 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=515b576b-f65d-4a2f-8e46-971adec64541

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		515b576b-f65d-4a2f-8e46-971adec64541
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=515b576b-f65d-4a2f-8e46-971adec64541 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		515b576b-f65d-4a2f-8e46-971adec64541
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=515b576b-f65d-4a2f-8e46-971adec64541 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		515b576b-f65d-4a2f-8e46-971adec64541
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root



=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=515b576b-f65d-4a2f-8e46-971adec64541 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ce76ce4b-bccc-487e-8f7a-73462eaf6519 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda1/boot: ==================================

total 11948
drwxr-xr-x  3 root root    4096 2008-11-25 12:24 .
drwxr-xr-x 20 root root    4096 2008-11-25 12:24 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-11-26 09:02 grub
-rw-r--r--  1 root root 8176604 2008-11-25 12:24 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

=============================== sda1/boot/grub: ===============================

total 224
drwxr-xr-x 2 root root   4096 2008-11-26 09:02 .
drwxr-xr-x 3 root root   4096 2008-11-25 12:24 ..
-rw-r--r-- 1 root root    197 2008-11-25 12:24 default
-rw-r--r-- 1 root root     30 2008-11-25 12:24 device.map
-rw-r--r-- 1 root root   8108 2008-11-25 12:24 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-11-25 12:24 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-11-25 12:25 installed-version
-rw-r--r-- 1 root root   8712 2008-11-25 12:24 jfs_stage1_5
-rw-r--r-- 1 root root   4436 2008-11-26 09:08 menu.lst
-rw-r--r-- 1 root root   5571 2008-11-26 09:02 menu.lst.bak
-rw-r--r-- 1 root root   7352 2008-11-25 12:24 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-11-25 12:24 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-11-25 12:24 stage1
-rw-r--r-- 1 root root 121460 2008-11-25 12:25 stage2
-rw-r--r-- 1 root root   9556 2008-11-25 12:24 xfs_stage1_5

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=26c6cbc1-9981-4400-8dbb-211a40323e9f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=26c6cbc1-9981-4400-8dbb-211a40323e9f

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		26c6cbc1-9981-4400-8dbb-211a40323e9f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=26c6cbc1-9981-4400-8dbb-211a40323e9f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		26c6cbc1-9981-4400-8dbb-211a40323e9f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=26c6cbc1-9981-4400-8dbb-211a40323e9f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		26c6cbc1-9981-4400-8dbb-211a40323e9f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=515b576b-f65d-4a2f-8e46-971adec64541 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=515b576b-f65d-4a2f-8e46-971adec64541 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.10, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=26c6cbc1-9981-4400-8dbb-211a40323e9f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=28b27fb7-13c2-43e7-84bd-6cf45cf1216a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

total 11948
drwxr-xr-x  3 root root    4096 2008-11-26 07:44 .
drwxr-xr-x 20 root root    4096 2008-11-26 07:43 ..
-rw-r--r--  1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-11-26 07:44 grub
-rw-r--r--  1 root root 8176243 2008-11-26 07:43 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic

=============================== sdb1/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2008-11-26 07:44 .
drwxr-xr-x 3 root root   4096 2008-11-26 07:44 ..
-rw-r--r-- 1 root root    197 2008-11-26 07:44 default
-rw-r--r-- 1 root root     30 2008-11-26 07:44 device.map
-rw-r--r-- 1 root root   8108 2008-11-26 07:44 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-11-26 07:44 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-11-26 07:44 installed-version
-rw-r--r-- 1 root root   8712 2008-11-26 07:44 jfs_stage1_5
-rw-r--r-- 1 root root   5353 2008-11-26 07:44 menu.lst
-rw-r--r-- 1 root root   7352 2008-11-26 07:44 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-11-26 07:44 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-11-26 07:44 stage1
-rw-r--r-- 1 root root 121460 2008-11-26 07:44 stage2
-rw-r--r-- 1 root root   9556 2008-11-26 07:44 xfs_stage1_5

=============================== StdErr Messages: ===============================

Unknown MBR on /dev/sdc

00000000  fa be 00 7c bf 00 7a b9  00 01 fc 0e 1f 0e 07 f3  |...|..z.........|
00000010  a5 ea 16 7a 00 00 bb be  7b 33 c9 80 3f 80 75 06  |...z....{3..?.u.|
00000020  fe c5 8b f3 eb 07 80 3f  00 75 02 fe c1 83 c3 10  |.......?.u......|
00000030  81 fb fe 7b 72 e5 83 f9  04 74 0b 81 f9 03 01 74  |...{r....t.....t|
00000040  0a bb a5 7a eb 2c bb 87  7a eb 27 8b 4c 02 8b 14  |...z.,..z.'.L...|
00000050  b8 01 02 bb 00 7c cd 13  73 05 bb bc 7a eb 13 2e  |.....|..s...z...|
00000060  a1 fe 7d 3d 55 aa 74 05  bb bc 7a eb 05 ea 00 7c  |..}=U.t...z....||
00000070  00 00 2e 8a 07 3c 00 74  0c 53 bb 07 00 b4 0e cd  |.....<.t.S......|
00000080  10 5b 43 eb ed eb fe 4e  6f 20 62 6f 6f 74 61 62  |.[C....No bootab|
00000090  6c 65 20 70 61 72 74 69  74 6f 6e 20 69 6e 20 74  |le partiton in t|
000000a0  61 62 6c 65 00 49 6e 76  61 6c 69 64 20 50 61 72  |able.Invalid Par|
000000b0  74 69 74 6f 6e 20 74 61  62 6c 65 00 49 6e 76 61  |titon table.Inva|
000000c0  6c 69 64 20 6f 72 20 64  61 6d 61 67 65 64 20 42  |lid or damaged B|
000000d0  6f 6f 74 61 62 6c 65 20  70 61 72 74 69 74 69 6f  |ootable partitio|
000000e0  6e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |n...............|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 01  |................|
000001c0  01 00 0e 0f e0 5f 20 00  00 00 e0 bf 1e 00 00 00  |....._ .........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

No errors were reported.


Thanks!

---

### Post by caljohnsmith on 2008-12-29
According to the script output, you have Grub correctly installed to both of your HDDs right now. But since Grub is not able to even load its stage1.5 file, I suspect you might be facing an issue with how your HDDs are configured in BIOS. But just to make sure Grub is properly installed, how about doing the following:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
Reboot, and let me know exactly what happens on start up. If you get the same problem with Grub hanging on loading the stage1.5 file, how about going into your BIOS and switch sda and sdb in the boot order. In other words, if sda is being booted first on start up, change it so sdb boots first instead, or vice versa. Reboot, and let me know exactly what happens.

---

### Post by ububtunovice on 2009-01-20
I did the grub commands, but grub again hung on loading the stage 1.5 file. In my BIOS, the boot sequence has options for only Hard Disk, Removable, P4-PLDS DVD+/-RW D. The Hard Disk Option does not have Hard Disk 0 and Hard Disk 1 sub-options. So, I am not sure how to change the boot order of my hard drives. Please help!

Thanks a lot!

PS: The BIOS settings for Standard CMOS features does show both my SATA drives. But, the RAID option for SATA Mode is on. Should I switch it to IDE?

---

### Post by caljohnsmith on 2009-01-21
How about putting the "Removable" drive before the "Hard Disk" in your boot order, and let me know what happens. If that doesn't change anything, then I would go ahead and try switching from RAID to IDE-emulation; let me know if that changes anything, and we can work from there.

---

### Post by ububtunovice on 2009-01-26
Changing RAID to IDE did the job for me! Thanks for all your replies; they were a tremendous help!

There is still a small problem though; my desktop is somehow moved a bit to the right, and there is a black vertical strip on the screen on the left. Any idea as to how to get this right?

Thanks!

---

### Post by caljohnsmith on 2009-01-27
Glad to hear you can boot Ubuntu OK now; about your screen issue, it sounds like the Ubuntu desktop may just be a little off center. Can you change your monitor settings to move the desktop back towards the left? If you have a digital camera, it might help if you could take a picture of what you mean and post a link to the picture; that way I'll get a better idea of exactly what you are trying to describe.

---

### Post by ububtunovice on 2009-01-29
using monitor's auto adjust did the job! Thanks!

---

### Post by caljohnsmith on 2009-01-29
Great, glad to hear you got the display issue resolved; cheers and hope your Ubuntu experience goes smoother from here on out. :)

---

