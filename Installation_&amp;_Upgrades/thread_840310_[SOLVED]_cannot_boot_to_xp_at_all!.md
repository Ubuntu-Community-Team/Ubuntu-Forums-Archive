---
title: "[SOLVED] cannot boot to xp at all!"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by bamboo_albion on 2008-06-25
hi!i did some reading but still stuck.
i installed ubuntu on dell desktop today.160 gb hdd,1 gb ram.
the problem is the window xp that is installed earlier than ubuntu feisty cannot be boot even after up and down the grub and choose window xp.
what i did was.
1.insert the livecd and reboot.
2.partition it manually.i leave the ntfs(80+gb) for window as it be.
3.create swap,/ and /home with the rest.
4.1st problem:it has c: 83gb, d:76gb and vfat 48mb(not assign any drive)
THEN i delete the D: and the 48mb vfat.but the amount does not sum up.why?(p/s:mine laptop will sum up all the spaces. )
5.then i create swap(logical),/ and /home(both primary and ext3)
6.then follow the step normally till step 7.
7.at the 7 of 7:click advance and then choose where it should installed.
i change hd0 to hd(0,1).
8.installed ntfs-3g.

i can boot to ubuntu as usual.but cannot boot to windows xp at all.at first the drive c appear at the desktop of ubuntu.but the next time login,the 80 gb does not appear at all.try fdisk -l but has no effect at all.
tried reboot with livecd at it show that ntfs formatted partition with ! sign on it.the flag say boot.had tried to check and unchecked the boot.but has no effect at all.

the other problem is.the desktop cannot be restart.it will hang!to restart,need to shut down and on again.

what should i do to get the xp active?crucial data in it.
thanks in advance.

---

### Post by logos34 on 2008-06-25
> **bamboo_albion said:**
> what i did was.
1.insert the livecd and reboot.
2.partition it manually.i leave the ntfs(80+gb) for window as it be.
3.create swap,/ and /home with the rest.
4.1st problem:it has c: 83gb, d:76gb and vfat 48mb(not assign any drive)
THEN i delete the D: and the 48mb vfat.but the amount does not sum up.why?(p/s:mine laptop will sum up all the spaces. )
5.then i create swap(logical),/ and /home(both primary and ext3)

post the output of these commands:

**sudo **fdisk -l [B]

cat /etc/fstab

cat /boot/grub/menu.lst 

[/B](maybe the windows stanza in menu.lst has a typo)
Swap should by formatted type "**linux-swap**", not ext3.  

Although you didn't need to resize/shrink windows, you might want to run **chkdsk /r **from the windows installation CD recovery console. (if you have one, that is).  Maybe even run **fixboot c:** for good measure.

> i can boot to ubuntu as usual.but cannot boot to windows xp at all.at first the drive c appear at the desktop of ubuntu.but the next time login,the 80 gb does not appear at all.try fdisk -l but has no effect at all.
tried reboot with livecd at it show that ntfs formatted partition with ! sign on it.the flag say boot.had tried to check and unchecked the boot.but has no effect at all.

I get the "yellow bang" symbol every once in a while.  You should still be able to mount it, though. And it definitely should be marked 'boot'.

Did you install and run the ntfs-3g gui config tool?

[B]sudo apt-get install ntfs-config

sudo ntfs-config[/B]

OR add a line to fstab manually:

[B]sudo mkdir /media/windows

gksudo gedit /etc/fstab

add:

[/B]> /dev/sda1 /media/windows ntfs-3g defaults 0 0

(to use 'UUID=' format, find with **sudo blkid**)
[B]
sudo mount -a[/B]

---

### Post by lfsim on 2008-06-25
sudo fdisk -l: 
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1           10206       13852    29294527+  83  Linux
/dev/sda2   *           7       10205    81923467+   7  HPFS/NTFS
/dev/sda3           13853       14217     2931862+   5  Extended
/dev/sda4           14218       19452    42050137+   b  W95 FAT32
/dev/sda5           13853       14217     2931831   82  Linux swap / Solaris

cat /etc/fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9e043e98-0507-47c6-919a-e99f7872b38b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=8703-305D  /media/d        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=80C2F69090FA0800 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=840cd2a4-11d6-4a9a-acc0-ba4d78787544 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

cat /boot/grub/menu.lst

 menu.lst - See: grub(8), info grub, update-grub(8)
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=UUID=9e043e98-0507-47c6-919a-e99f7872b38b ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=9e043e98-0507-47c6-919a-e99f7872b38b ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=9e043e98-0507-47c6-919a-e99f7872b38b ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

this is the result after reinstalling ubuntu feisty.after failing to boot to any os.
warning was: missing operating system.error loading os.

by the way this is bamboo_albion.borrowing other id

after installing ntfs-config
Mounting /media/sda2 failed.

Unexpected clusters per mft record (-1).
Failed to startup volume: Invalid argument
Failed to mount '/dev/disk/by-uuid/80C2F69090FA0800': Invalid argument
The device '/dev/disk/by-uuid/80C2F69090FA0800' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

---

### Post by logos34 on 2008-06-26
I see now what happened:

> **bamboo_albion said:**
> 
i change hd0 to hd(0,[COLOR=Red]**1**[/COLOR]).
...i can boot to ubuntu as usual.but cannot boot to windows xp at all.

grub starts counting from 0 not 1, so you overwrote the bootsector of the windows partition on sda2...should have put '(hd0,0)'--sda1, linux root--or let it overwrite the previous grub on the mbr. 

Use Super Grub Disk or Windows XP installation CD (recovery console>fixboot c:) to repair bootsector of sda2.  And chkdsk.  After that maybe windows will mount in linux.

>  Unexpected clusters per mft record (-1).
Failed to startup volume: Invalid argument
Failed to mount '/dev/disk/by-uuid/80C2F69090FA0800': Invalid argument
The device '/dev/disk/by-uuid/80C2F69090FA0800' doesn't have a valid NTFS.
It's complaining either about bad blocks (hopefully error checking will fix them) or maybe the uuid is wrong.

Verify with the command I gave above, or use **sudo vol_id /dev/sda2**

Or try using '/dev/sda2' in place of UUID= in fstab.

---

### Post by bamboo_albion on 2008-06-26
thanks logos34.
the earlier tips is working.
i & the desktop owner did manage to recover the windows at last after rebooting with windows installation cd.:)did the chckdisk,fixboot and also fixmbr.
i did fixmbr yesterday,but with other cd(which is not together with the desktop).it seem like it fancy dell's windows xp sp2 after all.
but i lost the ubuntu.but still i didn't mind installing it again.
i have other problem right now which is menu.lst is empty.but try to some research after this.
again mucha gracias.

---

### Post by togo59 on 2008-06-27
I hope you don't mind me tagging on but I have a similar problem. I installed ubuntu (Hardy) on a separate disk to windows but also (I think) managed to overwrite the windows boot sector. Symptom is the same as bamboo BUT Ubuntu can only see my (let's call it the C: drive but it's actually /dev/sda: ) from the command as follows:
```
roger@roger-ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0d930d92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156280319    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000660ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   224829674   112414806   83  Linux
/dev/sdb2       224829675   234436544     4803435    5  Extended
/dev/sdb5       224829738   234436544     4803403+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcbe423ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   976768064   488384001    7  HPFS/NTFS

```

If I go to Places/Computer -- the drive is missing.

When I install the Windows CD for recovery, what was previously a D: drive is now called C: and there's no OS there. It can't see my original C: drive.

In the bios,  have tried swapping the Boot Priority and the Disk Order (or whatever it's called -- I'm sure you know what I mean :)) and it makes no difference, what was a D; drive is now a C:.

Here is the menu.lst, should it prove interesting.
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-19-rt
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=89d635d1-d2ea-44a7-8095-70e4fd64b242 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-rt (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=89d635d1-d2ea-44a7-8095-70e4fd64b242 ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=89d635d1-d2ea-44a7-8095-70e4fd64b242 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=89d635d1-d2ea-44a7-8095-70e4fd64b242 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=89d635d1-d2ea-44a7-8095-70e4fd64b242 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=89d635d1-d2ea-44a7-8095-70e4fd64b242 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1

```

Any help would be greatly appreciated. If you want me to start another thread I will do so.

---

### Post by logos34 on 2008-06-27
> **bamboo_albion said:**
> thanks logos34.
the earlier tips is working.
i & the desktop owner did manage to recover the windows at last after rebooting with windows installation cd.:)did the chckdisk,fixboot and also fixmbr.
i did fixmbr yesterday,but with other cd(which is not together with the desktop).it seem like it fancy dell's windows xp sp2 after all.
but i lost the ubuntu.but still i didn't mind installing it again.
i have other problem right now which is menu.lst is empty.but try to some research after this.


glad to hear the windows fix worked.

What, you reinstalled ubuntu but can't boot it because the menu.lst is empty/missing? What error messages? Don't hesitate to post if you need help.

---

### Post by logos34 on 2008-06-27
> **togo59 said:**
> I hope you don't mind me tagging on but I have a similar problem. I installed ubuntu (Hardy) on a separate disk to windows but also (I think) managed to overwrite the windows boot sector. Symptom is the same as bamboo BUT Ubuntu can only see my (let's call it the C: drive but it's actually /dev/sda: ) from the command as follows...

If I go to Places/Computer -- the drive is missing.

When I install the Windows CD for recovery, what was previously a D: drive is now called C: and there's no OS there. It can't see my original C: drive.

In the bios,  have tried swapping the Boot Priority and the Disk Order (or whatever it's called -- I'm sure you know what I mean :)) and it makes no difference, what was a D; drive is now a C:...

Is sda1 supposed to be your 'original C: drive' (menu.lst/grub thinks so at least)?  Is that the one you can't see?  And sdc1 is (or was) D:, a non-bootable windows data partition?

Run the following command in a terminal and post output:

[B]mount

[/B]If one or both windows partitions fail to show up, try to manually mount them:

[B]sudo mkdir /media/sda1

sudo mount -t ntfs /dev/sda1 /media/sda1[/B]

do you see any files like ntldr, boot.ini, ntdetect.com, autoexec.bak?  If so, that's the system partition (C:\) even if it's now called D:\, and you should be able to fix the boot using the recovery console on the windows cd or Super Grub Disk

---

### Post by togo59 on 2008-06-27
Thanks for the reply. I thought that my request would be ignored so I started a new thread ( with a little bit more information) [http://ubuntuforums.org/showthread.php?t=842772]("http://ubuntuforums.org/showthread.php?t=842772")

```
roger@roger-ubuntu:~$ sudo mount
[sudo] password for roger: 
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/roger/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=roger)

```
Then I did this..
```

roger@roger-ubuntu:~$ sudo mkdir /media/sda1
roger@roger-ubuntu:~$ sudo mount -t ntfs /dev/sda1 /media/sda1
Unexpected clusters per mft record (-127).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
roger@roger-ubuntu:~$ 

```

Just to note, I have three hard disks: one for ubuntu, which is working OK, and two for windows. sda1 (was C: ), which has become invisible except using fdisk -l, and I have now physically unplugged the third to try to force the windows recovery to find the C: drive (which it didn't -- it said I don't have any disks!) The BIOS disagrees, however.

What a mess.

---

### Post by logos34 on 2008-06-27
> **togo59 said:**
> 
Then I did this..
```

roger@roger-ubuntu:~$ sudo mkdir /media/sda1
roger@roger-ubuntu:~$ sudo mount -t ntfs /dev/sda1 /media/sda1
Unexpected clusters per mft record (-127).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
roger@roger-ubuntu:~$ 

```Just to note, I have three hard disks: one for ubuntu, which is working OK, and two for windows. sda1 (was C: ), which has become invisible except using fdisk -l, and I have now physically unplugged the third to try to force the windows recovery to find the C: drive (which it didn't -- it said I don't have any disks!) The BIOS disagrees, however.

well, neither is mounting (the latter maybe because of bad blocks/cluster errors).  Normally I'd recommend running **chkdsk /r** from the recovery console on the xp cd, but you can't do that if it doesn't even see it (at least I don't think so--you could try and see if you get a C:\ prompt).  Fdisk and the Bios do, which I agree is odd.  

I'd try [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") to fix any errors in the partition table.

**sudo apt-get install testdisk **
(if it fails, enable universe repository)

sudo testdisk

---

### Post by togo59 on 2008-06-27
Now I don't even see my replies to this forum?? (and I hit refresh..)

Yes, I tried testdisk, it saw the 80Gb drive, I selected it, I hit Proceed, it hung. Nothing happened, no choice of partition or anything.

:(:(:(

P.S. I am hitting the sack now (it's late and I've been up for a while) thank you for you help, I log in tomorrow.

---

