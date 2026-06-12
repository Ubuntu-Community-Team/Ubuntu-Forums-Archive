---
title: "Ubuntu or Win 7 but not both.."
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by Merovius on 2010-01-10
On a system   with Ubuntu 8.10 and Windows XP, tried to upgrade to Windows 7 and now it will boot to Windows 7 but not Ubuntu. If I use Super Grub Disk to fix grub I can boot Ubuntu but not Windows 7. I tried installing 7 ona seperate drive (triple boot) but could not boot it. Repairing grub made no difference. It was like it did not exist. I decided to update over XP in the hope grub would boot 7 and then I would edit the grub menu to say 7. No go. The nearest I get was an error about system32 being missing. The XP install was 32 bit. The Win 7 was 64. 

Ideas? Help!

---

### Post by kansasnoob on 2010-01-10
Well we need to see exactly what you have, so with all drives plugged in just the way you want them, please run the Boot Info Script and post the results as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

It will run either from the Live CD or your installed Ubuntu.

---

### Post by Merovius on 2010-01-10
Here goes,

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #5 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sde
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /Windows/System32/winload.exe /ntldr 
                       /NTDETECT.COM

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sde2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 251.0 GB, 251000193024 bytes
16 heads, 63 sectors/track, 486344 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0b830627

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   490,231,727   490,231,665   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000700b8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   312,578,047   312,576,000   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf2def2de

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   490,207,409   490,207,347   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006fc37

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   625,139,423   625,139,361   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00044b40

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   613,008,269   613,008,207  83 Linux
/dev/sde2         613,008,270   625,137,344    12,129,075   5 Extended
/dev/sde5         613,008,333   625,137,344    12,129,012  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="D0A8287AA82860E8" LABEL="Disk Two" TYPE="ntfs" 
sdb1: UUID="3EA45AF6A45AAFDF" TYPE="ntfs" 
sdc1: UUID="68407E84407E5930" TYPE="ntfs" 
sdd1: UUID="8E20A6EB20A6DA0B" LABEL="New Volume" TYPE="ntfs" 
sde1: UUID="ab9c7d11-f569-4cd9-a683-dcc45013732b" TYPE="ext3" 
sde5: UUID="f37b5905-9b36-4de3-be5f-a8d3375fa65a" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sde1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-14-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /media/Disk_Two type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1 on /media/New_Volume_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/sdc1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mike/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mike)


================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sde1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=ab9c7d11-f569-4cd9-a683-dcc45013732b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ab9c7d11-f569-4cd9-a683-dcc45013732b

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		ab9c7d11-f569-4cd9-a683-dcc45013732b
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=ab9c7d11-f569-4cd9-a683-dcc45013732b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		ab9c7d11-f569-4cd9-a683-dcc45013732b
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=ab9c7d11-f569-4cd9-a683-dcc45013732b ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, memtest86+
uuid		ab9c7d11-f569-4cd9-a683-dcc45013732b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4a8a471e-d875-42e4-857b-eb2da53a2496 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4a8a471e-d875-42e4-857b-eb2da53a2496 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.24-21-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=4a8a471e-d875-42e4-857b-eb2da53a2496 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=4a8a471e-d875-42e4-857b-eb2da53a2496 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
chainloader	+1


=============================== sde1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sde1 :
UUID=ab9c7d11-f569-4cd9-a683-dcc45013732b	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sda1 :
UUID=D0A8287AA82860E8	/media/Disk_Two	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sdd1 :
UUID=8E20A6EB20A6DA0B	/media/New_Volume_	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sdb1 :
UUID=3EA45AF6A45AAFDF	/media/sdb1	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sdc1 :
UUID=68407E84407E5930	/media/sdc1	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sde5 :
UUID=f37b5905-9b36-4de3-be5f-a8d3375fa65a	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0



=================== sde1: Location of files loaded by Grub: ===================


 160.5GB: boot/grub/menu.lst
 160.6GB: boot/grub/stage2
 160.6GB: boot/initrd.img-2.6.27-11-generic
 160.6GB: boot/initrd.img-2.6.27-14-generic
 160.5GB: boot/initrd.img-2.6.27-7-generic
 160.5GB: boot/initrd.img-2.6.27-9-generic
 160.5GB: boot/vmlinuz-2.6.27-11-generic
 160.5GB: boot/vmlinuz-2.6.27-14-generic
 160.5GB: boot/vmlinuz-2.6.27-7-generic
 160.5GB: boot/vmlinuz-2.6.27-9-generic
 160.6GB: initrd.img
 160.6GB: initrd.img.old
 160.5GB: vmlinuz
 160.5GB: vmlinuz.old

---

### Post by Merovius on 2010-01-10
I get the impression that this setup is really messed up. Not my machine so it's all learning curve for me..

---

### Post by presence1960 on 2010-01-10
> **Merovius said:**
> I get the impression that this setup is really messed up. Not my machine so it's all learning curve for me..

why all those windows OS installs? That is problem #1. 

Problem # 2 is put GRUB on MBR of sde, then go into BIOS and put sde as first disk to boot in the hard disk boot order. Then you will be able to boot into Ubuntu and edit menu.lst to get windows booting. Do this:

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd4,0)". 
5. Type "root (hd4,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd4)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

Go into BIOS and setup your hard disk boot order as sde, sda, sdb, sdc, sdd. Save changes to CMOS and continue booting. Highlight Ubuntu & press "e" on keyboard. Use your arrow keys to navigate to root (hd1,0) and change it to root (hd0,0) Then hit Ctrl + x to boot. When you get into ubuntu post back and we'll edit menu.lst & get windows booting.

---

### Post by kansasnoob on 2010-01-11
Sorry to just disappear, had other irons in the fire. Things don't look horrible to me.

If this quote from your OP is true:

> If I use Super Grub Disk to fix grub I can boot Ubuntu but not Windows 7.

I don't think you'll need to even mess with the BIOS, that is if you can restore Ubuntu's grub as you said in your OP, and Ubuntu is bootable under its own power, then all you should have to do is add the Win 7 on sdc1 to the menu.lst.

Now, the Windows on sdb1 is missing some boot files and I don't know how to fix that. Others around here do, but not me. Just for comparison look at the difference:

> sdb1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files/dirs: /Windows/System32/winload.exe

sdc1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files/dirs: /boot.ini /Windows/System32/winload.exe /ntldr
/NTDETECT.COM

See where it lists Boot files/directories for each?

As far as the menu.lst I assume you know how to edit it:

```
sudo gedit /boot/grub/menu.lst
```

Make changes (more about that below), click on Save, then File > Quit.

Specific to this system everything above the following lines looks OK to me, but everything below them is junk:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root
```

The Windows entry should look like this:

```
# This entry added for a non-linux OS on /dev/sdc1
title          Windows 7
rootnoverify   (hd2,0)
savedefault
makeactive
map            (hd4) (hd2)
map            (hd2) (hd4)
chainloader    +1
```

If you can figure out how to replace the /boot.ini/ntldr/NTDETECT.COM files on sdb1 then you'd add it like:

```
# This entry added for a non-linux OS on /dev/sdb1
title          Windows 7
rootnoverify   (hd1,0)
savedefault
makeactive
map            (hd4) (hd1)
map            (hd1) (hd4)
chainloader    +1
```

I think that's it unless I missed something.

This is a great read on legacy grub:

[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)

---

### Post by Merovius on 2010-01-11
Thanks for the tips. 

The system has had two Ubuntu installs and three windows installs in it's time. I only want to have the Ubuntu 8.10 and Windows 7 installs to boot. I believe Windows 7 is on sdb at this point. (It's early last night is a blur..) There is also an install from a previous attempt on sdc. Tried to put 7 on a new partition and leave XP on it's partition and Ubuntu on its partition. Then tried installing 7 OVER xp and just booting 7 and Ubuntu. Neither way worked obviously.

Will start trying some of these ideas after work and get back with progress. Thanks again.

---

### Post by Merovius on 2010-01-11
I am home and ready to try and fix this. I am posting from Ubuntu  8.10. I could not follow the directions from "presence1960". Live Ubuntu CD booted, terminal said Grub was not installed. Used Super Grub Disk and had it install grub. PC boots into Ubuntu now. Believe it tobe booting from sde,0. Will check boot order in bios after sending this.

TIA

---

### Post by Mark Phelps on 2010-01-11
Realize that installing Win7 to an unformatted drive will result in two partitions: (1) a small one containing the boot loader (and other) files, (2) a larger one containing the remainder of the OS and files.

If you want to prevent this, just create an empty NTFS partition and install Win7 to that.  It will then install ALL its files to that partition.

---

### Post by Merovius on 2010-01-11
That may have been my problem to begin with yesterday. Wish I'd have known that sooner..

---

### Post by Merovius on 2010-01-11
I have edited the menu list.lst. Cleaned it up a lot. Ubuntu boots fine but the entry for Windows 7 just results in a reboot. Please see menu below.



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
# kopt=root=UUID=ab9c7d11-f569-4cd9-a683-dcc45013732b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ab9c7d11-f569-4cd9-a683-dcc45013732b

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		ab9c7d11-f569-4cd9-a683-dcc45013732b
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=ab9c7d11-f569-4cd9-a683-dcc45013732b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		ab9c7d11-f569-4cd9-a683-dcc45013732b
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=ab9c7d11-f569-4cd9-a683-dcc45013732b ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, memtest86+
uuid		ab9c7d11-f569-4cd9-a683-dcc45013732b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry added for a non-linux OS on /dev/sdc1
title          Windows 7
rootnoverify   (hd2,0)
savedefault
makeactive
map            (hd4) (hd2)
map            (hd2) (hd4)
chainloader    +1

---

### Post by Merovius on 2010-01-11
Edited again and I can boot into either OS now. :guitar:

Thanks for the tips kansasnoob & presence1960 You led me down the right path.

---

### Post by presence1960 on 2010-01-11
Glad you got it working. Enjoy!

---

