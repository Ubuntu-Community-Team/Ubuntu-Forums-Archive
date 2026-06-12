---
title: "error 17 in grub trying to dual boot"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by jubaitca on 2009-12-22
Hi,

I am trying to dual/triple boot my computer. I already had it triple booting with vista, xp, ubuntu on 3 different partitions. I had installed it in that order too, and probably why I haven't run into this problem.

 So now i decided to format vista partition and intall windows 7 there. So I did that and realized the boot loader was gone. Used easybcd to get dual booting with xp. So next was Ubuntu. I read up some stuff on the forum and tried booting from the cd and in the terminal i enter "find /boot/grub/stage1"  in grub and it gives me an error saying the file can't be found. so i try root(hd0,X) (X going up to 2) and then setup (hd0) i get error 17: cannot mount selected partiton. I try to use the gui to open New Volume and I get the same message, this opens to the live version of ubuntu off the cd. 

Not sure what has happened, was wondering if anyone can provide any direction on this. Would be really helpful.

Thanks

---

### Post by presence1960 on 2009-12-22
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by jubaitca on 2009-12-22
Here it is: (its kinda long)

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g defaults,force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g defaults,force 0 0

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 sda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 sda5 ntfs-3g defaults,force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 sda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 sda5 ntfs-3g defaults,force 0 0

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda6': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda6 sda6 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda6 sda6 ntfs-3g defaults,force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda6': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda6 sda6 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda6 sda6 ntfs-3g defaults,force 0 0

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe6b90ab6

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    10,942,463    10,940,416  27 Hidden HPFS/NTFS
/dev/sda2    *     10,942,464   236,222,463   225,280,000   7 HPFS/NTFS
/dev/sda3         236,234,880   390,715,919   154,481,040   f W95 Ext d (LBA)
/dev/sda5         236,234,943   348,878,879   112,643,937   7 HPFS/NTFS
/dev/sda6         348,878,943   390,715,919    41,836,977   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8C0C0C060C0BE9D2" LABEL="ServiceV002" TYPE="ntfs" 
/dev/sda2: UUID="DCB62D0DB62CEA2A" TYPE="ntfs" 
/dev/sda5: UUID="6E74939E7493681B" TYPE="ntfs" 
/dev/sda6: UUID="40E83ECAE83EBE4A" LABEL="New Volume" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /media/ServiceV002 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

```

---

### Post by presence1960 on 2009-12-22
your first problem is that your windows partitions can not be mounted because of unclean shutdown. I would recommend following the instructions given for each partition in the results:
```

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g defaults,force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g defaults,force 0 0

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 sda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 sda5 ntfs-3g defaults,force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 sda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 sda5 ntfs-3g defaults,force 0 0

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda6': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda6 sda6 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda6 sda6 ntfs-3g defaults,force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda6': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda6 sda6 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda6 sda6 ntfs-3g defaults,force 0 0
```

The other problem is you do not have Linux (Ubuntu) on your hard disk. You probably wiped that during the windows installation, which by the way was the windows you kept in suspend or hibernation when you installed the second windows? That can cause the problem you have.

---

### Post by jubaitca on 2009-12-22
I am pretty sure linux is still there in the third partition. I can access it from windows 7. As a matter of fact, I can open the menu.lst file from it (that was probably used before I installed windows 7). 
 
This is what it looks like: 
```
 
 
# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
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
default 0
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10
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
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=40E83ECAE83EBE4A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio
## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks
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
title Ubuntu 8.10, kernel 2.6.27-9-generic
root ()/ubuntu/disks
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=40E83ECAE83EBE4A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd /boot/initrd.img-2.6.27-9-generic
title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root ()/ubuntu/disks
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=40E83ECAE83EBE4A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio single
initrd /boot/initrd.img-2.6.27-9-generic
title Ubuntu 8.10, kernel 2.6.27-7-generic
root ()/ubuntu/disks
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=40E83ECAE83EBE4A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd /boot/initrd.img-2.6.27-7-generic
title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root ()/ubuntu/disks
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=40E83ECAE83EBE4A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio single
initrd /boot/initrd.img-2.6.27-7-generic
title Ubuntu 8.10, memtest86+
root ()/ubuntu/disks
kernel /boot/memtest86+.bin
### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root
&#12288;
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
chainloader +1
&#12288;
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows Vista/Longhorn (loader)
root (hd0,1)
savedefault
chainloader +1

```
&#12288;

---

### Post by jubaitca on 2009-12-22
I don't quite understand choice 1 where it says to safelye remove external devices from windows taskbar?? Not sure how I would go about doing that in windows 7.

---

### Post by oldfred on 2009-12-22
I think the comments refer to a USB type device since that is all you could unmount. You need to have windows run its chkdsk and any other repairs that it can do on all the NTFS partitions, probalby one at a time.

You must have had a wubi install inside windows. Because of all the errors mounting the NTFS partitions it could not look into the windows partition to find the wubi install. One of the disadvanges of wubi is that it depends on windows to work.

---

### Post by jubaitca on 2009-12-23
> **oldfred said:**
> I think the comments refer to a USB type device since that is all you could unmount. You need to have windows run its chkdsk and any other repairs that it can do on all the NTFS partitions, probalby one at a time.
 
You must have had a wubi install inside windows. Because of all the errors mounting the NTFS partitions it could not look into the windows partition to find the wubi install. One of the disadvanges of wubi is that it depends on windows to work.
 
By ntfs you mean only the partition used for xp and windows 7. The ubuntu partition wouldn't be ntfs right?

---

### Post by oldfred on 2009-12-23
Because you have wubi it is in the ntfs partition. It is just a folder within windows and can be uninstalled like  any program in windows. It is a system with a virtual drive (root.disk) within windows.

If it was a separate partition dual boot the partition would be formated to ext3 or ext4 and windows would not even see it.

info on wubi
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by jubaitca on 2009-12-23
I followed the instructions to shut down xp properly and remove any external device and welll, before I proceed with removing wubi i ran the script again and this time it looks better:

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /ntdetect.com

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   /wubildr.mbr

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda6/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe6b90ab6

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    10,942,463    10,940,416  27 Hidden HPFS/NTFS
/dev/sda2    *     10,942,464   236,222,463   225,280,000   7 HPFS/NTFS
/dev/sda3         236,234,880   390,715,919   154,481,040   f W95 Ext d (LBA)
/dev/sda5         236,234,943   348,878,879   112,643,937   7 HPFS/NTFS
/dev/sda6         348,878,943   390,715,919    41,836,977   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8C0C0C060C0BE9D2" LABEL="ServiceV002" TYPE="ntfs" 
/dev/sda2: UUID="DCB62D0DB62CEA2A" TYPE="ntfs" 
/dev/sda5: UUID="6E74939E7493681B" TYPE="ntfs" 
/dev/sda6: UUID="40E83ECAE83EBE4A" LABEL="New Volume" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)


==================== sda6/ubuntu/disks/boot/grub/menu.lst: ====================

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
# kopt=root=UUID=40E83ECAE83EBE4A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title        Ubuntu 8.10, kernel 2.6.27-9-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=40E83ECAE83EBE4A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=40E83ECAE83EBE4A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=40E83ECAE83EBE4A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=40E83ECAE83EBE4A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
chainloader    +1


======================== sda6/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

=================== sda6: Location of files loaded by Grub: ===================


 178.6GB: ubuntu/disks/boot/grub/menu.lst
 182.0GB: ubuntu/disks/boot/initrd.img-2.6.27-7-generic
 182.0GB: ubuntu/disks/boot/initrd.img-2.6.27-9-generic
 182.0GB: ubuntu/disks/boot/vmlinuz-2.6.27-7-generic
 179.3GB: ubuntu/disks/boot/vmlinuz-2.6.27-9-generic

============================= sda6/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
```Everything looks clean but I still get the same error as before. Is there anything else I should do?

---

### Post by jubaitca on 2009-12-24
I am not sure how I can find wubi in windows? Do I just search for it like searching for files in windows?

---

### Post by oldfred on 2009-12-24
It was my understanding that wubi was just like any other windows program and you can uninstall it the same way.

---

### Post by presence1960 on 2009-12-25
> **jubaitca said:**
> I am not sure how I can find wubi in windows? Do I just search for it like searching for files in windows?

You can uninstall wubi like any other windows program by going to Control Panel > Add/remove programs in XP and Control Panel in Vista (I am not sure which software in Control Panel does that in Vista).

If I were you I would do an installation of Ubuntu to a dedicated partition for a real dual boot setup. I would also get rid of Easy BCD and use GRUB to boot.

---

