---
title: "Can't boot. /dev/hda1 is GONE."
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by bukzor on 2009-11-27
After upgrade to Karmic, my machine will no longer boot with a "ALERT! /dev/disk/by-uuid/XXX does not exist." error.

I did search the forums but my situation seems different from all of the problems I found in that:

[LIST=1]
[*]/dev/disk/by-uuid is **completely** missing.
[*]Partitions (/dev/hda2, etc.) are also missing.
[/LIST]

Because of #2, the root partition is not mounted, and I can't get to fdisk or /etc/mtab or any of the usual suggestions.


This is what I see at the boot-recovery (busybox) terminal:

```
$ ls /dev/sd*
/dev/sda /dev/sdb

$ ls /dev/disk/* -l
/dev/disk/by-id:
total 0
lrwxrwxrwx 1 root root 9 2009-11-28 20:32 ata-MAXTOR_6L060J3_663210555230 -> ../../sdb
lrwxrwxrwx 1 root root 9 2009-11-28 20:32 ata-MAXTOR_6L060J3_663217454727 -> ../../sda
lrwxrwxrwx 1 root root 26 2009-11-28 20:32 dm-name-pdc_dgecfaiii -> ../../mapper/pdc_dgecfaiii
lrwxrwxrwx 1 root root 26 2009-11-28 20:32 dm-uuid-DMRAID-pdc_dgecfaiii -> ../../mapper/pdc_dgecfaiii
lrwxrwxrwx 1 root root 9 2009-11-28 20:32 scsi-SATA_MAXTOR_6L060J3_663210555230 -> ../../sdb
lrwxrwxrwx 1 root root 9 2009-11-28 20:32 scsi-SATA_MAXTOR_6L060J3_663217454727 -> ../../sda

/dev/disk/by-label:
total 0
lrwxrwxrwx 1 root root 9 2009-11-28 20:33 Ubuntu\x209.10\x20i386 -> ../../sr0

/dev/disk/by-path:
total 0
lrwxrwxrwx 1 root root 9 2009-11-28 20:32 pci-0000:00:0f.1-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root 9 2009-11-28 20:32 pci-0000:00:0f.1-scsi-0:0:1:0 -> ../../sdb
lrwxrwxrwx 1 root root 9 2009-11-28 20:32 pci-0000:00:0f.1-scsi-1:0:0:0 -> ../../sr0
```



------
Problem:

A long time ago I had my disks in a RAID array. The new dmraid package in Karmic detected this and set up my disks to mount as raid. Note the '/dev/sr0' partition shown above. Not very helpful...

------
Solution:

Download and boot to a Karmic Live-CD.
Run the following to remove lingering RAID meta-data:

```
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
```

---

### Post by lloyd_b on 2009-11-27
> **bukzor said:**
> After upgrade to Karmic, my machine will no longer boot with a "ALERT! /dev/disk/by-uuid/XXX does not exist." error.

I did search the forums but my situation seems different from all of the problems I found in that:

[LIST=1]
[*]/dev/disk/by-uuid is **completely** missing
[*]/dev/hda1 is also missing
[*]It seems that my IDE drives are being detected as SCSI devices (/dev/sda & /dev/sdb, but no partitions)
[/LIST]

Because of #2, the root partition is not mounted, and I can't get to fdisk or /etc/mtab or any of the usual suggestions.

I think the root of the problem is #3. Does anyone know why Ubuntu would suddenly think these drives were SCSI?

I've tried booting to a rescue terminal under my previous kernel version, but no love. This means (to me) that the kernel version is not the issue.

I have a live CD, but at this point I wouldn't know what to do after using it...

Exactly what were you upgrading from?  For quite a while now, the IDE and SCSI drivers have been "unified", so that IDE drives show up as "/dev/sda..." rather than "/dev/hda..." (IIRC, then change occurred around Feisty).

At any rate, try booting the install CD, and then go into "rescue" mode.  At the prompt, "fdisk -l" to list out all the partitions on your drives.

The fact that you're seeing "/dev/sda", but not "/dev/sda1" makes me suspect that your partition table on that disk is messed up.

Lloyd B.

---

### Post by woelf on 2009-11-27
I have the same problem.
if I use the live cd there is no other filesystem then the cd.

sudo mount /dev/sda1 /mnt
mount: you must specify the filesystem type

( [http://ubuntuforums.org/showthread.php?t=1195275&highlight=rescue+mode](http://ubuntuforums.org/showthread.php?t=1195275&highlight=rescue+mode)
step 12 )

---

### Post by darkod on 2009-11-27
> **woelf said:**
> I have the same problem.
if I use the live cd there is no other filesystem then the cd.

sudo mount /dev/sda1 /mnt
mount: you must specify the filesystem type

( [http://ubuntuforums.org/showthread.php?t=1195275&highlight=rescue+mode](http://ubuntuforums.org/showthread.php?t=1195275&highlight=rescue+mode)
step 12 )

What does
sudo fdisk -l

show?

---

### Post by woelf on 2009-11-27
Disk /dev/sda 1000.2 GB, 1000204886016 bytes
255 heads,63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk indentifier: 0X0003bad9

Device Boot   Start      End     Blocks   Id  System
/dev/sda1 *       1   120851  970735626   83  Linux
/dev/sda2     120852  121601    6024375    5  Extended
/dev/sda5     120852  121601    6024343+  82  Linux swap / Solaris

---

### Post by darkod on 2009-11-27
How about something like this:
[http://www.linuxquestions.org/questions/linux-newbie-8/having-problems-mounting-hd.-mount-you-must-specify-the-filesystem-type-188956/](http://www.linuxquestions.org/questions/linux-newbie-8/having-problems-mounting-hd.-mount-you-must-specify-the-filesystem-type-188956/)

I'm not sure if it can destroy the data so BE CAREFUL. I just found it on google, haven't used it myself. It is best to read around more about that error and the fixes. The partition is obviously shown in fdisk, it's still there.

---

### Post by oldfred on 2009-11-27
So we can see your entire configuration run this script. You can download it with the liveCD.

Boot Info Script 0.34 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
Instructions 
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280) 
cd to directory saved to: 
chmod 755 boot_info_script034.sh 
sudo ./boot_info_script034.sh 
or as example if on desktop 
sudo bash ~/Desktop/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by bukzor on 2009-11-27
Here's the info that you guys asked for. It looks like the partitions are fine, to me.

fdisk -l:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74ed74ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2              20        7299    58476600    f  W95 Ext'd (LBA)
/dev/sda3               1          19      152586   83  Linux
/dev/sda5              20        7056    56524671   83  Linux
/dev/sda6            7057        7299     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf07df07d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        7299    58621185    f  W95 Ext'd (LBA)
/dev/sdb5               2        7299    58621153+  83  Linux

```

And the bootinfoscript output:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /grub/stage2 and /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74ed74ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2              20        7299    58476600    f  W95 Ext'd (LBA)
/dev/sda3               1          19      152586   83  Linux
/dev/sda5              20        7056    56524671   83  Linux
/dev/sda6            7057        7299     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf07df07d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        7299    58621185    f  W95 Ext'd (LBA)
/dev/sdb5               2        7299    58621153+  83  Linux

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders, total 117266688 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x74ed74ed

Partition  Boot         Start           End          Size  Id System

/dev/sda2             305,235   117,258,434   116,953,200   f W95 Ext d (LBA)
/dev/sda5             305,298   113,354,639   113,049,342  83 Linux
/dev/sda6         113,354,703   117,258,434     3,903,732  82 Linux swap / Solaris
/dev/sda3                  63       305,234       305,172  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders, total 117266688 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf07df07d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065   117,258,434   117,242,370   f W95 Ext d (LBA)
/dev/sdb5              16,128   117,258,434   117,242,307  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda3: UUID="17a59b8e-904d-46ed-968c-d8ca2d3c53b7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="1d79a35a-566c-4083-a75a-bafc8b0bb545" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="a9f4b03c-8af6-4dad-a5cc-802fb407b81f" 
/dev/sdb5: UUID="e6f4858b-a962-4146-ad9f-064bc8bd5cdc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6 -- converted during upgrade to edgy
UUID=1d79a35a-566c-4083-a75a-bafc8b0bb545 / ext3 defaults,errors=remount-ro,relatime 0 1
# /dev/hda3 -- converted during upgrade to edgy
UUID=17a59b8e-904d-46ed-968c-d8ca2d3c53b7 /boot ext3 defaults,relatime 0 2
# /dev/hda7 -- converted during upgrade to edgy
UUID=a9f4b03c-8af6-4dad-a5cc-802fb407b81f none swap sw 0 0
/dev/sdb5 /media/disk ext3 defaults,errors=remount-ro,relatime 0 1
/dev/scd0        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

============================= sda3/grub/menu.lst: =============================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=1d79a35a-566c-4083-a75a-bafc8b0bb545 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
root		(hd0,2)
kernel		/vmlinuz-2.6.31-15-generic root=UUID=1d79a35a-566c-4083-a75a-bafc8b0bb545 ro quiet splash 
initrd		/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.31-15-generic root=UUID=1d79a35a-566c-4083-a75a-bafc8b0bb545 ro  single
initrd		/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.28-16-generic root=UUID=1d79a35a-566c-4083-a75a-bafc8b0bb545 ro quiet splash 
initrd		/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.28-16-generic root=UUID=1d79a35a-566c-4083-a75a-bafc8b0bb545 ro  single
initrd		/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=================== sda3: Location of files loaded by Grub: ===================


    .1GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd.img-2.6.28-16-generic
    .1GB: initrd.img-2.6.31-15-generic
    .0GB: vmlinuz-2.6.28-16-generic
    .0GB: vmlinuz-2.6.31-15-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
00000200

Unknown BootLoader  on sda3

00000000  f6 f6 f6 f6 f6 f6 f6 f6  f6 f6 f6 f6 f6 f6 f6 f6  |................|
*
00000200

```

---

### Post by darkod on 2009-11-27
@bukzor
I would try reinstalling grub2 by booting with the CD, selecting Try Ubuntu and running in terminal

```
sudo -i
mount /dev/sda7 /mnt
mount /dev/sda6 /mnt/boot (if you had separate /boot partition)
grub-install --root-directory=/mnt/ /dev/sda
```Note: I am talking about grub2 and 9.10 cd. Adjust the commands /dev/sda7 and /dev/sda6 with your partition for / and /boot (if you had one).
Also it doesn't hurt running
sudo update-grub

after that. Reboot and see how it goes.

---

### Post by bukzor on 2009-11-27
Tried that but it didn't go so well.

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mount /dev/disk/by-uuid/1d79a35a-566c-4083-a75a-bafc8b0bb545 /mnt
root@ubuntu:~# mount /dev/disk/by-uuid/17a59b8e-904d-46ed-968c-d8ca2d3c53b7 /mnt/boot/
root@ubuntu:~# grub-install --root-directory=/mnt/ /dev/sda
/dev/sda does not have any corresponding BIOS drive.

---

### Post by darkod on 2009-11-27
Why did you use /dev/disk/byuuid instead of /dev/sda3 or /dev/sda4 or whatever? Try with the exact command as specified, not sure myself if it should work otherwise.

---

### Post by bukzor on 2009-11-27
The exact commands specified tried to mount my swap space to /mnt...
I got those by-uuid paths from my fstab (see previous post). 

The mounts worked fine, but grub-install doesn't like /dev/sda from some reason (/dev/sda does not have any corresponding BIOS drive ).

---

### Post by darkod on 2009-11-27
That seems to be the problem. How about this:
[http://www.cyberciti.biz/faq/error-devhdx-does-not-have-any-corresponding-bios-drive-and-solution/](http://www.cyberciti.biz/faq/error-devhdx-does-not-have-any-corresponding-bios-drive-and-solution/)

---

### Post by darkod on 2009-11-27
Also check post #7 here:
[http://ubuntuforums.org/showthread.php?t=665877](http://ubuntuforums.org/showthread.php?t=665877)

---

### Post by bukzor on 2009-11-27
Added a --recheck argument as found in those threads and grub liked that better. Rebooting now...


```
# grub-install --recheck --root-directory=/mnt /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/boot/grub"] is not on an XFS filesystem
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb

```

---

### Post by bukzor on 2009-11-27
No change after reboot. 
Waiting for Fred or Lloyd to get back now.
--Buck

---

### Post by oldfred on 2009-11-27
Your installs do not look quite right. You have menu.lst in sda3 and a fstab in sda5 but not both in either.

my entry is this with both in the boot dir:
Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

Did you have 2 different installs of Ubuntu or a separate /boot?

---

### Post by oldfred on 2009-11-27
Further reading shows you have a separate /boot in sda3 and root in sda5.

Did you install grub2 or do you still have grub legacy 0.97. Upgrades did not upgrade grub to grub2 unless you separately install it.

---

### Post by oldfred on 2009-11-27
I have checked UUID's and kernel numbers and cannot see any discrepancies. That error should be that a UUID or kernel in menu.lst does not match the actual in the files.

I also saw where someone solved the problem by chrooting into his system and running the apt-get update and apt-get upgrade.


SOLUTION: Alert! /dev/disk/by-uuid/ ...<your UUID>.... does not exist
[http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)
[http://ubuntuforums.org/showthread.php?t=813090](http://ubuntuforums.org/showthread.php?t=813090)

---

### Post by bukzor on 2009-11-27
> **oldfred said:**
> I have checked UUID's and kernel numbers and cannot see any discrepancies. That error should be that a UUID or kernel in menu.lst does not match the actual in the files.

I also saw where someone solved the problem by chrooting into his system and running the apt-get update and apt-get upgrade.


SOLUTION: Alert! /dev/disk/by-uuid/ ...<your UUID>.... does not exist
[http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)
[http://ubuntuforums.org/showthread.php?t=813090](http://ubuntuforums.org/showthread.php?t=813090)

I get this error because /dev/disk/by-uuid doesn't exist *at all*, and so it throws a 'does not exist' message.

I tried the chroot trick shown in those threads. I was able to fully update the install, and also took the time to re-install my kernel and install grub2, but after all that, there's no change in symptoms.

I took the grub2 installer's advice and chain-loaded it from the old grub install, so I was able to try loading the newest kernel and my previous (jaunty) kernel in both grub and grub2, also in normal and recovery modes, but no combination made any difference.


Two unsolved questions:
* Why is /dev/disk/by-uuid missing?
* Why are none of my partitions detected? (/dev/sda[0-9])

--Buck

---

### Post by bukzor on 2009-11-27
Just to put all the command together for my future reference:


```
sudo -i
mount /dev/disk/by-uuid/1d79a35a-566c-4083-a75a-bafc8b0bb545 /mnt
mount /dev/disk/by-uuid/17a59b8e-904d-46ed-968c-d8ca2d3c53b7 /mnt/boot/
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
cp /etc/resolv.conf /mnt/var/run/resolvconf/resolv.conf 
chroot /mnt /bin/bash
```

---

### Post by lloyd_b on 2009-11-27
Looking over the thread, and one question comes into mind:  You have grub2 installed, correct?  If so, what are the contents of the file "/boot/grub/grub.cfg"?

'grub2' no longer uses 'menu.lst' for its configuration - the file 'grub.cfg' (which is a totally different format than menu.lst) stores the config info for grub2.

Lloyd B.

---

### Post by bukzor on 2009-11-27
grub.cfg attached.

I have both grub and grub2 installed (as suggested by the grub2 installer) and both give the same results.

---

### Post by oldfred on 2009-11-27
The script never showed the install of grub2 nor the grub.cfg, so I thought you had just an upgrade with old grub.

There is a bug in grub2 for separate boot partitions:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/478035](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/478035)

In the grub.cfg you posted the UUID for is different for the search line and the root=UUID= line and that may be ok since you have /boot in a separate partition. I do not know, but it would seem to me the UUID for  vmlinuz-2.6.28-16-generic should be the partition it is in sda3 not where ubuntu is sda5.

     search --no-floppy --fs-uuid --set 17a59b8e-904d-46ed-968c-d8ca2d3c53b7
     linux    /vmlinuz-2.6.28-16-generic root=UUID=1d79a35a-566c-4083-a75a-bafc8b0bb545 ro single  

Because of the bug I would think about removing grub2 until it is fixed.

---

### Post by bukzor on 2009-11-28
Good ideas, but I still have "classic" grub installed and have been trying it to no avail, so I'm confident no bug in grub2 would cause my problems.

I installed grub2 recently (four or so posts ago). 

Here's a repost of the boot_script_info results, from my chroot'ed environment.



```
root@ubuntu:~# ./boot_info_script037.sh 
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda2 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda3 for information... 
Searching sdb1 for information... 
Searching sdb5 for information... 
Finished. The results are in the file RESULTS2.txt located in /root

```

---

### Post by oldfred on 2009-11-28
I still do not see any problems. I might try installing grub to sdb to boot directly to sda5 and switch drive order to see if the /boot is an issue. This is just a stab in the dark, if you have tried all the other fixes in the links I gave before.

---

### Post by bukzor on 2009-11-28
I think it's time to file an official bug. What do you think the correct package is?

---

### Post by darkod on 2009-11-28
IMHO, it's just an upgrade process and grub upgrade went wrong/confused.

> Disk /dev/sda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74ed74ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2              20        7299    58476600    f  W95 Ext'd (LBA)
/dev/sda3               1          19      152586   83  Linux
/dev/sda5              20        7056    56524671   83  Linux
/dev/sda6            7057        7299     1951866   82  Linux swap / SolarisWhy do you think you should have sda1? All cilinders are here, from 1 to 7299.

You also said in one post you tried to keep grub1 and chainload grub2. Why would you want to chainload from one to the other?

After you executed the --recheck and it seems to add (hd0) /dev/sda as device, I would still try once more to install grub2 (and forget everything about grub1 and menu.lst) with:

sudo -i
mount /dev/sda5 /mnt (I guess this is your /)
mount /dev/sda3 /mnt/boot
grub-install --root-directory=/mnt/ /dev/sda

Maybe this time you won't get the "does not have corresponding drive in BIOS blabla" error since /dev/sda is tied to (hd0). It can't hurt. It could only help.

---

### Post by oldfred on 2009-11-28
Please understand that the error is not this:

I get this error because /dev/disk/by-uuid doesn't exist *at all*, and so it throws a 'does not exist' message.

It is saying that it cannot find the drive/partition by using UUIDs. This is almost always a typo in menu.lst or how grub is installed. I have not been able to see a typo and that is why we recommend reinstalling grub and making sure system is up to date.

Darko - I also do not think it makes sense to chainboot from grub1 to grub2 this way. But when they first came out with grub2 with 9.04 that was what they recommended because they were sure there were many issues to be resolved and did not want users not to be able to boot at all. But this allowed for testing of grub2.

---

### Post by darkod on 2009-11-28
> **oldfred said:**
> 
Darko - I also do not think it makes sense to chainboot from grub1 to grub2 this way. But when they first came out with grub2 with 9.04 that was what they recommended because they were sure there were many issues to be resolved and did not want users not to be able to boot at all. But this allowed for testing of grub2.

I'm not developer but I perfectly understand that new software can have some hiccups. But it seems that was long ago (in relative terms). And because I just entered into Ubuntu with 9.10 I don't know the "history". I just let Grub2 to run the show and it works perfect. In fact, at time of install didn't even notice the Advanced button that would open the grub2 where to install options. :)
It seems the OP did the upgrade recently and IMHO and limited experience it's better either to stick with grub1 or let grub2 take over. Trying to mix them can never be good.

The last time the OP tried to reinstall grub2 it returned some error about /dev/sda not having entry in BIOS (not to look for the exact words). Since with using --recheck that was corrected it seems, I think grub2 definitely deserves another shot. It might restore your system to working state with just few commands.

---

### Post by bukzor on 2009-11-28
> **oldfred said:**
> Please understand that the error is not this:

I get this error because /dev/disk/by-uuid doesn't exist *at all*, and so it throws a 'does not exist' message.

It is saying that it cannot find the drive/partition by using UUIDs. This is almost always a typo in menu.lst or how grub is installed. I have not been able to see a typo and that is why we recommend reinstalling grub and making sure system is up to date.


Actually, that *is* the problem... If i look in /dev/disk (under the busybox boot shell) I only see by-id and by-path. **The by-uuid directory is missing.**

Also, I've been using the uuid's from my fstab to get to my chroot environment (see above post), so I know there's no typo there.

I've reinstalled grub and installed grub2, and it has no effect. I'll go install grub2 to the MBR as you guys want, but I don't expect anything from it.

---

### Post by bukzor on 2009-11-28
darkod:
> Why do you think you should have sda1?
I don't expect an sda1, but I do expect an sda7 and others.
When I do an 'ls /dev/sd*' from the busybox shell, I get simply:
```
/dev/sda
/dev/sdb
```
No partitions at all!

Also, I've tried installing grub2 to the MBR, with no change. The problem is nearly certainly NOT in grub.

At this point, all I want is a suggestion about which package to file a bug against.

I'm also going to try to generate some debugging output for udev to figure out why by-uuid is missing. Maybe it's udev's fault or maybe it's something lower-level.

---

### Post by bukzor on 2009-11-29
Downloaded and used the Karmic Live-CD.
I notice that I get the exact same behaviour as I'm seeing when attempting to boot from disk.

Note: No partitions (/dev/sda2 etc) and no /dev/disks/by-uuid directory.

```
ubuntu@ubuntu:/media$ ls /dev/sd*
/dev/sda /dev/sdb

ubuntu@ubuntu:/media$ ls /dev/disk/* -l
/dev/disk/by-id:
total 0
lrwxrwxrwx 1 root root 9 2009-11-28 20:32 ata-MAXTOR_6L060J3_663210555230 -> ../../sdb
lrwxrwxrwx 1 root root 9 2009-11-28 20:32 ata-MAXTOR_6L060J3_663217454727 -> ../../sda
lrwxrwxrwx 1 root root 26 2009-11-28 20:32 dm-name-pdc_dgecfaiii -> ../../mapper/pdc_dgecfaiii
lrwxrwxrwx 1 root root 26 2009-11-28 20:32 dm-uuid-DMRAID-pdc_dgecfaiii -> ../../mapper/pdc_dgecfaiii
lrwxrwxrwx 1 root root 9 2009-11-28 20:32 scsi-SATA_MAXTOR_6L060J3_663210555230 -> ../../sdb
lrwxrwxrwx 1 root root 9 2009-11-28 20:32 scsi-SATA_MAXTOR_6L060J3_663217454727 -> ../../sda

/dev/disk/by-label:
total 0
lrwxrwxrwx 1 root root 9 2009-11-28 20:33 Ubuntu\x209.10\x20i386 -> ../../sr0

/dev/disk/by-path:
total 0
lrwxrwxrwx 1 root root 9 2009-11-28 20:32 pci-0000:00:0f.1-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root 9 2009-11-28 20:32 pci-0000:00:0f.1-scsi-0:0:1:0 -> ../../sdb
lrwxrwxrwx 1 root root 9 2009-11-28 20:32 pci-0000:00:0f.1-scsi-1:0:0:0 -> ../../sr0
```

---

### Post by oldfred on 2009-11-29
You did not say you were running raid. That is a whole different can of worms.

If you are not running raid and the drives were once in a raid config, karmic finds raid that used to exist. 
I saw in this thread the raid issue and how to fix it. See Presence's comments:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)

---

### Post by bukzor on 2009-11-29
I'm *not* running RAID, that's the problem. Good spot! I originally had a RAID setup, but removed it maybe three years ago. I didn't know what /dev/sr0 meant, I guess you did. Where do you get the decoder ring?

I've run these commands to remove the RAID metadata and I'm restgarting now. I'll also make sure RAID is disabled in my BIOS.


```
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
```

---

### Post by darkod on 2009-11-29
Also
sudo apt-get remove dmraid

It's not whether you are running it or no, like Fred said, it can DETECT older raid remains. And then it all goes downhill from there. :)

I am surpsirsed it didn't show earlier, the fdisk you were posting should have displayed it too. That's why I didn't think of it either. The devices are not called /dev/sda1 at all in raid, but rather /dev/mapper/blabla and you posted normal layout of /dev/sda.

---

### Post by bukzor on 2009-11-29
That did the trick! Thanks so much guys! 

I'll mark the thread as solved and update the OP with solution.

---

