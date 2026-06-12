---
title: "XP and v8.04 dual-boot, not touching MBR install help request"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by ejvan on 2008-07-25
I've been searching the forums and have found a lot on dual-booting, but most say to nuke the XP MBR.  I don't want to do that if I don't have to.  In trying to follow the instructions shown here: 
[http://users.bigpond.net.au/hermanzone/p9.html]("http://users.bigpond.net.au/hermanzone/p9.html")

They use WinGrub.  I tried using the directions provided and have had no luck.  The setup is the following:

I want to install v8.04 onto my 2nd hard drive, process is as follows:
1.  Install XP onto hd(0,0) - no surprise there
2.  Install new HD into system, it works like a champ - shows up as HD(2,0)
3. Load v8.04 CD, boot, select HD(2,0) as the location, use the automatic partition option.
4.  I've tried using the manual partition and for either installation (default or manual), I've told it to install GRUB to the HD(2,0)'s MBR, not HD(0,0).  
5.  Follow the directions provided in the above mentioned thread to install & try to configure WinGRUB.

The error is as follows.  If I just reboot & select 'GRUB', it then finds the v8.04 correctly, but when trying to boot, it gets 'Error 17:  File not found'.

So... Figured it was something to do with my menu.lst file, right?  Yeah... well, the XP menu.lst file only has:

timeout 10

title Windows at (hd0,0)
root (hd0,0)
chainloader +1


Doesn't look right,especially since I am now able to choose between the various versions of the kernel (v8.04, v8.04 recovery, memtest, xp, etc).

Soooo... grab a copy of SuperGrub & boot into that CD.  It again sees either XP or the linux drives & choosing linux I now get:

'Error 17:  Can Not Mount Selected Partition'

At this point, XP continues to work just fine, but I can not boot into linux.  I really don't want to nuke my XP's MBR because, frankly, I see no need to.  WinGrub seems to work for others, but I'm having issues.  

Any suggestions would be appreciated.

---

### Post by Rocket2DMn on 2008-07-25
It is actually quite alright to kick Windows out of the MBR and have GRUB replace it.  The chainloader allows Windows to boot itself normally after GRUB without having to deal with anything extra.  If you ever decided to get rid of Ubuntu, Windows can easily be restored to the MBR.

I would just have the Super GRUB Disk reinstlal GRUB and overwrite the MBR.

---

### Post by ejvan on 2008-07-25
Thanks.  I used SG to update the MBR... no luck.  Still getting 'Can Not Mount Selected Partition' (Error 17).  I had to use SG to boot into XP. 

Something I forgot to mention, but may impact things.  I'm using an Asus P4C800 motherboard.  I've got HD(0,0) attached via SATA while HD(2,0) is attached via the secondary IDE - it's the master on that channel, but they're different controllers.

I'm also wondering if the Grub install that was put down by v8.04s installer is confused. I can't get to that partition so I don't know what it's got set in its menu.lst files, but I'm wondering if during the install it simply got confused & is somehow trying to mount HD(0,0) as the linux.

---

### Post by Rocket2DMn on 2008-07-25
If you boot from the LiveCD, mount the root partition (assuming you dont have a separate /boot partition), say at /media/linux.
Then navigate to /media/linux/boot/grub/menu.lst - you can see here where GRUB is looking (based on UUIDs).
From the LiveCD with the hard drive's root partition mounted at /media/linux, can you please post the output of these commands
```
sudo fdisk -l
cat /media/linux/etc/fstab
cat /media/linux/boot/grub/menu.lst
sudo blkid
mount
```
In order to mount your root partition to begin with, check the output of
```
sudo fdisk -l
```
then find your root partition (formatted with ext3).  Say it's at /dev/sdb1
Mount it (on the LiveCD):
```
sudo mkdir /media/linux
sudo mount -t ext3 /dev/sdb1 /media/linux
```

---

### Post by Herman on 2008-07-25
I would enter the BIOS and reverse the hard disk boot priority, (not the boot sequence), to make hard disk number 1 be number 2 instead and vice-versa.
That should be all that is needed I think.

Regards, Herman :)

---

### Post by ejvan on 2008-08-14
Rocket2DMn - 
Here's the output from the commands:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14117   113394771   83  Linux
/dev/sda2           14118       14589     3791340    5  Extended
/dev/sda5           14118       14589     3791308+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16708   134206978+   7  HPFS/NTFS

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x716fa141

  Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       36481   293033601    7  HPFS/NTFS

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39b192ce

  Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38913   312568641    7  HPFS/NTFS


ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon
(rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


ubuntu@ubuntu:~$ cat /media/disk/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=622ecbcd-4cdc-4bdf-892a-43c14fa7d4f9 /               ext3
relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=ee9425fd-e5cd-495f-b091-d0a46e73140d none            swap    sw
          0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


ubuntu@ubuntu:~$ cat /media/disk/boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=622ecbcd-4cdc-4bdf-892a-43c14fa7d4f9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.24-16-generic
root=UUID=622ecbcd-4cdc-4bdf-892a-43c14fa7d4f9 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.24-16-generic
root=UUID=622ecbcd-4cdc-4bdf-892a-43c14fa7d4f9 ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title           Microsoft Windows XP Professional
root            (hd3,0)
savedefault
map             (hd0) (hd3)
map             (hd3) (hd0)
chainloader     +1



ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="622ecbcd-4cdc-4bdf-892a-43c14fa7d4f9" TYPE="ext3"
/dev/sda5: UUID="ee9425fd-e5cd-495f-b091-d0a46e73140d" TYPE="swap"
/dev/sdb1: UUID="D8B04380B043645A" TYPE="ntfs"
/dev/sdc1: UUID="060CB96A0CB95581" LABEL="Data" TYPE="ntfs"
/dev/sdd1: UUID="36ECB911ECB8CBFD" LABEL="Tunes" TYPE="ntfs"
/dev/loop0: TYPE="squashfs"
ubuntu@ubuntu:~$



Sorry it took so long; been busy the past few weeks.

Herman - 
I tried changing the priority of the drives via the BIOS; no luck.  I still get the Error 17 even after I nuke the MBR with SG.

Thanks again for any/all suggestions.

---

### Post by Rocket2DMn on 2008-08-14
OK, I think I see what might be wrong.  Here is a snip from your menu.lst file on the hard drive
```
title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd2,0)
kernel /boot/vmlinuz-2.6.24-16-generic
root=UUID=622ecbcd-4cdc-4bdf-892a-43c14fa7d4f9 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd2,0)
kernel /boot/vmlinuz-2.6.24-16-generic
root=UUID=622ecbcd-4cdc-4bdf-892a-43c14fa7d4f9 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd2,0)
kernel /boot/memtest86+.bin
quiet
```
What it shows for all of them is
```
root (hd2,0)
```
This makes sense since the fstab file shows your Ubuntu on the sdc drive.  However, from the LiveCD, it shows that drive as sda.  Did you ever re-organize the hard drive arrangement inside of your computer or add a hard drive since installing Ubuntu?  It could be that the order that the drives are being detected in has changed.
You initially said that XP was on (hd0,0), but menu.lst is showing (hd3,0) - (I don't know what the 'map' stuff is though).  You may consider changing the (hd2,0) on your Ubuntu entries to (hd0,0).
You can edit your file from the LiveCD with (first making a backup):
```
sudo cp /media/disk/boot/grub/menu.lst /media/disk/boot/grub/menu.lst.bak
gksudo gedit /media/disk/boot/grub/menu.lst
```
Then go through and do the changes manually.  Save, close, and reboot normally.

---

