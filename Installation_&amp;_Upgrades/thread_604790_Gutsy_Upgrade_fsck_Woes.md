---
title: "Gutsy Upgrade fsck Woes"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by WelterPelter on 2007-11-06
Upgraded to Gutsy when it came out.
Was working fine until the first time fsck checked a disk during boot.
Now it hangs when trying to check /dev/sda1

I read several threads about this, but the only suggestions that applied correctly to my situation involved changing the fsck check frequency.

I set the check frequency up to 100, and now the system boots again, but only because it's not checking the disk (and the disk is fine, btw.). 

This work-around is fine for now, but I want to know how to permanently repair this error. I have looked at the other threads on this topic. That doesn't mean I've understood them, of course. 

Thanks.

---

### Post by kshane on 2007-11-06
> **WelterPelter said:**
> Upgraded to Gutsy when it came out.
Was working fine until the first time fsck checked a disk during boot.
Now it hangs when trying to check /dev/sda1

I read several threads about this, but the only suggestions that applied correctly to my situation involved changing the fsck check frequency.

I set the check frequency up to 100, and now the system boots again, but only because it's not checking the disk (and the disk is fine, btw.). 

This work-around is fine for now, but I want to know how to permanently repair this error. I have looked at the other threads on this topic. That doesn't mean I've understood them, of course. 

Thanks.

What does the log say?  Could you post it?

Kevin

---

### Post by WelterPelter on 2007-11-06
Which particular log, located where?

---

### Post by kshane on 2007-11-06
> **WelterPelter said:**
> Which particular log, located where?

It should have told you when you got the error.  I believe it is  /var/log/fsck/checkfs

Kevin

---

### Post by WelterPelter on 2007-11-06
Here it is:

```
[Log of fsck -C -R -A -a 
Tue Nov  6 02:02:50 2007

fsck 1.40.2 (12-Jul-2007)
/dev/sda1: Superblock last mount time is in the future.  FIXED.
/dev/sda1: Superblock last write time is in the future.  FIXED.
/dev/sda1: clean, 561807/36634624 files, 34709405/73258400 blocks
/home: clean, 87510/1245184 files, 681804/2486058 blocks

Tue Nov  6 02:02:51 2007
----------------
```

---

### Post by kshane on 2007-11-06
I don't really see a problem there.  Do you mount a partition from your /home directory?  That strikes me as a little odd.  It says there are some fixed errors.  How many times did you get the actual error that halted the boot?

Kevin

---

### Post by WelterPelter on 2007-11-06
Got it at least 10 times in a row. Maybe more.

---

### Post by kshane on 2007-11-06
Could you post /etc/fstab and /boot/grub/menu.lst ?

Kevin

---

### Post by WelterPelter on 2007-11-06
[CODE
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hdb1       /windows    vfat    umask=000 0
/dev/sda1       /data        ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

[/CODE]

```

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro

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

title        Ubuntu 7.10, kernel 2.6.22-14-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-386

title        Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro single
initrd        /boot/initrd.img-2.6.22-14-386

title        Ubuntu 7.10, kernel 2.6.20-16-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-386

title        Ubuntu 7.10, kernel 2.6.20-16-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro single
initrd        /boot/initrd.img-2.6.20-16-386

title        Ubuntu 7.10, kernel 2.6.20-14-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-14-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro quiet splash
initrd        /boot/initrd.img-2.6.20-14-386

title        Ubuntu 7.10, kernel 2.6.20-14-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-14-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro single
initrd        /boot/initrd.img-2.6.20-14-386

title        Ubuntu 7.10, kernel 2.6.20-13-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-13-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro quiet splash
initrd        /boot/initrd.img-2.6.20-13-386

title        Ubuntu 7.10, kernel 2.6.20-13-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-13-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro single
initrd        /boot/initrd.img-2.6.20-13-386

title        Ubuntu 7.10, kernel 2.6.20-12-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-12-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro quiet splash
initrd        /boot/initrd.img-2.6.20-12-386

title        Ubuntu 7.10, kernel 2.6.20-12-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-12-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro single
initrd        /boot/initrd.img-2.6.20-12-386

title        Ubuntu 7.10, kernel 2.6.20-12-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-12-generic root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro quiet splash
initrd        /boot/initrd.img-2.6.20-12-generic

title        Ubuntu 7.10, kernel 2.6.20-12-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-12-generic root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro single
initrd        /boot/initrd.img-2.6.20-12-generic

title        Ubuntu 7.10, kernel 2.6.20-11-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-11-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro quiet splash
initrd        /boot/initrd.img-2.6.20-11-386

title        Ubuntu 7.10, kernel 2.6.20-11-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-11-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro single
initrd        /boot/initrd.img-2.6.20-11-386

title        Ubuntu 7.10, kernel 2.6.17-11-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-11-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro quiet splash
initrd        /boot/initrd.img-2.6.17-11-386

title        Ubuntu 7.10, kernel 2.6.17-11-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-11-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro single
initrd        /boot/initrd.img-2.6.17-11-386

title        Ubuntu 7.10, kernel 2.6.15-28-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-28-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro quiet splash
initrd        /boot/initrd.img-2.6.15-28-386

title        Ubuntu 7.10, kernel 2.6.15-28-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-28-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro single
initrd        /boot/initrd.img-2.6.15-28-386

title        Ubuntu 7.10, kernel 2.6.15-27-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-27-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro quiet splash
initrd        /boot/initrd.img-2.6.15-27-386

title        Ubuntu 7.10, kernel 2.6.15-27-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-27-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro single
initrd        /boot/initrd.img-2.6.15-27-386

title        Ubuntu 7.10, kernel 2.6.15-26-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-26-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro quiet splash
initrd        /boot/initrd.img-2.6.15-26-386

title        Ubuntu 7.10, kernel 2.6.15-26-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-26-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro single
initrd        /boot/initrd.img-2.6.15-26-386

title        Ubuntu 7.10, kernel 2.6.15-25-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-25-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro quiet splash
initrd        /boot/initrd.img-2.6.15-25-386

title        Ubuntu 7.10, kernel 2.6.15-25-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-25-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro single
initrd        /boot/initrd.img-2.6.15-25-386

title        Ubuntu 7.10, kernel 2.6.15-23-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-23-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro quiet splash
initrd        /boot/initrd.img-2.6.15-23-386

title        Ubuntu 7.10, kernel 2.6.15-23-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-23-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro single
initrd        /boot/initrd.img-2.6.15-23-386

title        Ubuntu 7.10, kernel 2.6.15-22-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-22-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro quiet splash
initrd        /boot/initrd.img-2.6.15-22-386

title        Ubuntu 7.10, kernel 2.6.15-22-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-22-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro single
initrd        /boot/initrd.img-2.6.15-22-386

title        Ubuntu 7.10, kernel 2.6.15-19-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-19-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro quiet splash
initrd        /boot/initrd.img-2.6.15-19-386

title        Ubuntu 7.10, kernel 2.6.15-19-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-19-386 root=UUID=c9826c66-802f-4cea-89e6-4da8b7cd7ad3 ro single
initrd        /boot/initrd.img-2.6.15-19-386

title        Ubuntu 7.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST


title        Windows XP
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1




```

---

### Post by WelterPelter on 2007-11-06
It seems that the only reason the fsck log looks OK is because of the check frequency change I made.

As a troubleshooting step, I set the check frequency to "1" and rebooted.
Sure enough, it hung again.
Here is the fsck chkf log from the hung boot:

```

Log of fsck -C -R -A -a 
Tue Nov  6 06:19:17 2007

fsck 1.40.2 (12-Jul-2007)
/dev/sda1 has been mounted 36 times without being checked, check forced.
/home: clean, 87506/1245184 files, 646621/2486058 blocks


```

Since it hangs at that point, something is definitely wrong.

---

### Post by Herman on 2007-11-09
Try running a  file system check manually from a Ubuntu LiveCD.
```
sudo e2fsck -C0 -p -f -v /dev/sda1
```Did that make any difference?

Often a manual file system check with your own options will fix problems that the automatic file system check isn't designed to help with.

Regards, Herman :)

---

### Post by WelterPelter on 2007-11-09
I've run the full e2fsck command several times now.
It passes with flying colors.

Doesn't solve the problem....

---

### Post by Herman on 2007-11-09
Hmmm, :confused:

That is hard to understand then.

I just noticed you don't have anything in the 'pass column in your /ect/fstab file'e entry for your Windows fat32 file system, will fixing that help you at all?
Maybe it's completing the check on your ext3 data partition okay, but it doesn't know what to do when it comes to the missing number in the 'pass' column for /dev/hdb1?
```
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hdb1       /windows    vfat    umask=000 0
/dev/sda1       /data        ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

``````
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hdb1       /windows    vfat    umask=000         0         [COLOR=Red]**0**[/COLOR]
/dev/sda1       /data        ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```
Regards, Herman :)

---

### Post by WelterPelter on 2007-11-09
Thanks, Herman, but no go.
Still dead in the water, unless I change the check frequency.

---

### Post by Herman on 2007-11-10
Well, I'm not sure then.
I wonder if getting more info will reveal any clues?

How about a look at your superblock and your fdisk output?
```
sudo dumpe2fs -h /dev/sda1
```
```
sudo fdisk-lu
```

Regards, Herman :)

---

### Post by WelterPelter on 2007-11-10
Thanks for taking the time, Herman.
Here's the output you asked for:

```
mwt@lapod:~$ sudo dumpe2fs -h /dev/sda1
[sudo] password for mwt:
dumpe2fs 1.40.2 (12-Jul-2007)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          8dc1547b-0d31-43e5-bc69-198376d7e502
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal filetype needs_recovery sparse_super large_file
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              36634624
Block count:              73258400
Reserved block count:     3662920
Free blocks:              38548935
Free inodes:              36072792
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Filesystem created:       Sat Mar  4 17:25:40 2006
Last mount time:          Fri Nov  9 16:27:16 2007
Last write time:          Fri Nov  9 16:27:16 2007
Mount count:              5
Maximum mount count:      500
Last checked:             Fri Nov  9 08:52:20 2007
Check interval:           0 (<none>)
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      2dbc123d-ef6a-46ca-bac1-da393708a4d0
Journal backup:           inode blocks
Journal size:             128M

```

```
mwt@lapod:~$ sudo fdisk -lu

Disk /dev/hda: 20.4 GB, 20489477632 bytes
255 heads, 63 sectors/track, 2491 cylinders, total 40018511 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3db012b3

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    18426554     9213246   83  Linux
/dev/hda2        38315025    40017914      851445    5  Extended
/dev/hda3        18426555    38315024     9944235   83  Linux
/dev/hda5        38315088    40017914      851413+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x73889d3c

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63   156296384    78148161    c  W95 FAT32 (LBA)

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c1b7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   586067264   293033601   83  Linux

```

---

### Post by Herman on 2007-11-10
Your superblock and fdisk output look okay to me. Obviously you have modified a few settings in there but I don't think those would be the cause of the problem.

Now, the automatic file system check is pausing your boot-up, but there doesn't seem to be any actual problem in the file system itself at all does there? The manual file system check completes without any problems.

The automatic file system check at boot-up runs  fsck -C -R -A -a and that runs e2fsck for you, but with whatever options fsck sets for you.

The -A option tells fsck to walk through your /etc/fstab file and check your root file system first, and then the rest of your file systems in the order they are listed in. with the passno 1, followed by those with passno. 2 in the sixth column in your etc/fstab file. Those with a passno. of 2 will be checked in parallel to save time.

The -R option means skip the root file system when the -A option is running.  :confused:

The -C option means to display the progress bar if the file system is ext2 or ext3.

The -a option turns on the -p switch in e2fsck to automatically 'preen' the filesystem, performing any easy repairs that don't require any human intervention.

What could go wrong with that? 
Where is it getting stuck?

If it was failing at the -a option it would give you a message to try running fsck manually, so that probably isn't it.

Maybe it's having trouble walking through your /etc/fstab file for some reason.
Lets' try a couple of experiments to test if that could be true or not.

How about trying 'umount -a' first and then runnning 'fsck -C -R -A -a' in your hard disk installed Ubuntu operating system first and see if that will complete okay or not? It works for me, just that it does skip the root file system, which of course would still be mounted.
```
umount -a
``````
fsck -C -R -A -a
``` What happens?

Another experiment would be to try restoring your old /etc/fstab from a backup if you have one, with the UUID numbers in it like it had when the O.S. was first installed and see if that makes any difference or not.
It shouldn't, according to my logic, but let's just prove it to make sure. 

That's all for now,
Regards, Herman :)

---

### Post by john bledsoe on 2007-11-11
I have had a similar problem with Gutsy and found a way to fix it with some help from this forum.

I had set up a partition to collect downloaded files but found that after I deleted the downloaded files not all the free space was released.  I eventually ran out of space on the partition even though a search with Nautilus indicated that adding the sizes of all  files on the partition did not add up to even half the size of the partition.

I backed up the files I still wanted onto another partition, unmounted and then re-formatted the one that caused the problem.  After that I couldn't get the partition to mount again though Gparted recognized it.

I had lots of trouble rebooting but somehow got the system going again eventually.

The problem partition was:   /dev/sdb9

Eventually found that the UUID in /etc/fstab no longer matched the UUID found from:

sudo  dumpe2fs -h /dev/sdb9

When I copied the UUID value from "sudo  dumpe2fs -h /dev/sdb9" into the fstab file value for that partition I was able to mount the partition and the computer booted normally.

Hope this helps.

jb

---

### Post by WelterPelter on 2007-11-11
John -
Here is the output from the dumpe2fs command.
The UUID looks a little bizarre to me:

```
mwt@lapod:~$ sudo dumpe2fs -h /dev/sda1
dumpe2fs 1.40.2 (12-Jul-2007)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          8dc1547b-0d31-43e5-bc69-198376d7e502
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal filetype needs_recovery sparse_super large_file
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              36634624
Block count:              73258400
Reserved block count:     3662920
Free blocks:              38548935
Free inodes:              36072792
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Filesystem created:       Sat Mar  4 17:25:40 2006
Last mount time:          Sun Nov 11 05:00:02 2007
Last write time:          Sun Nov 11 05:00:02 2007
Mount count:              6
Maximum mount count:      500
Last checked:             Fri Nov  9 08:52:20 2007
Check interval:           0 (<none>)
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      2dbc123d-ef6a-46ca-bac1-da393708a4d0
Journal backup:           inode blocks
Journal size:             128M


```

---

### Post by WelterPelter on 2007-11-11
> **Herman said:**
> 

How about trying 'umount -a' first and then runnning 'fsck -C -R -A -a' in your hard disk installed Ubuntu operating system first and see if that will complete okay or not? It works for me, just that it does skip the root file system, which of course would still be mounted.
```
umount -a
``````
fsck -C -R -A -a
``` What happens?


Herman -
When I run 'umount -a' it tells me that the devices are busy.

---

### Post by Herman on 2007-11-12
Yeah, I get that too.

We aren't supposed to run a file system check on a mounted file system so I guess I better not insist that you try it then.

I tried it myself the first time to make sure it will work before I posted you the idea to try running those commands. It said a few devices were busy in mine too,
```
umount: /dev: device is busy
umount: /var/run: device is busy
umount /: device is busy
```When I run the command it runs okay in my computers.
The output looks something like this:
```
sudo fsck -C -R -A -a
fsck 1.40.2 (12-Jul-2007)
/dev/sda6 is mounted, e2fsck cannot continue, aborting.


dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda1 296 files,  38078/174353 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda2:  30067 files,  446075/735616 clusters
/dev/sda3: clean,  136701/2719744 files,  2590940/5425953 blocks

```The fact that it seems to me to be smart enough to skip my root file system because it can detect that it's mounted makes it seem safe enough, since the 'umount -a' command should unmount everything else. I suppose that's what the  -R switch is for.

However, I don't want you to run the command now since you are reluctant.  It's only for a test anyway, and might not even prove anything.
Cancel that. 

We'll have to think of something else to try instead.

What about where it says 'check interval:   0 (<none>)' in your superblock?
 
```
mwt@lapod:~$ sudo dumpe2fs -h /dev/sda1
dumpe2fs 1.40.2 (12-Jul-2007)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          8dc1547b-0d31-43e5-bc69-198376d7e502
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal filetype needs_recovery sparse_super large_file
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              36634624
Block count:              73258400
Reserved block count:     3662920
Free blocks:              38548935
Free inodes:              36072792
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Filesystem created:       Sat Mar  4 17:25:40 2006
Last mount time:          Sun Nov 11 05:00:02 2007
Last write time:          Sun Nov 11 05:00:02 2007
Mount count:              6
Maximum mount count:      500
Last checked:             Fri Nov  9 08:52:20 2007
[B][COLOR=Red]Check interval:           0 (<none>)

[/COLOR][/B] Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      2dbc123d-ef6a-46ca-bac1-da393708a4d0
Journal backup:           inode blocks
Journal size:             128M
``` Is that the correct way to say you don't ever want it checked? Or will that mean zero check interval, like 'check it right now!'  That might be enough to make the file system check keep repeating itself indefinitley.  I'm just guessing, I would need to try that out myself to find out for sure.

There's a line missing under that one too. I just noticed that now.
Mine has: 'Next check after:  Tue Apr 15 16:58:41 2008' (without the inverted commas), in the line immediately under 'Check Interval:  15552000 (6 months).

I realize you probably made those edits yourself on purpose, but maybe if you try editing everything back to normal, until everything will work normally again you'll find out which edit is causing your problem?

Regards, Herman   :)

---

