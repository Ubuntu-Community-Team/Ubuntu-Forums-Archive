---
title: "Ubuntu 8.04LTS -&gt; 10.4 Upgrade hung, now system unbootable"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by chejrw on 2010-05-04
Hey everybody.  I tried running an upgrade from 8.04 LTS to 10.4 last night, and things seemed to be going smoothly.  The upgrade progress was nearly complete, and I wandered off for a while to let it run.  When I came back, I had nothing but an orange screen and and unresponsive system.  I left it alone all night with the hopes that something would happen, but this morning nothing had changed so I hard restarted the system.

Ubuntu 10.4 appears in GRUB, but the system cannot boot and exits with a kernel panic and the message "vfs unable to mount root fs on unknown-block"

I was able to boot to a 10.4 LiveCD, and I can browse all of my files from there.

What can I do to get this system back up an running?  I have dozens of user account and a lot of customization (it acts as a webserver with a wiki for a gaming website running on it, among other things), so I really really don't want to do a fresh install and lose all my data and customizations.

help?

---

### Post by chejrw on 2010-05-04
More info - I've attached an screenshot of the error messages I get when I try to boot to recovery mode.

---

### Post by lechien73 on 2010-05-04
Which disk/partition is 10.04 on? Were you using a different filesystem (such as Reiser)? It could be a problem with Grub pointing to the wrong partition, or support for the correct filesystem not being compiled in.

---

### Post by chejrw on 2010-05-04
the OS is on sda1 - which should be hd0,0 - it's EXT3, no exotic filesystems

If I try hd0,1, hd1,0, or any others I get "unable to mount" or "partition not found" errors - 0,0 is the only one where it will even attempt to boot

---

### Post by kansasnoob on 2010-05-04
Depending on your skill level you might benefit from this (particularly post #5):

[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Although I can't be quite sure what commands you'd need to run without more info. The output of the Boot Info Script would be a good starting point:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by chejrw on 2010-05-04
I'd consider my skill level "moderate to low" :(

I'll check out the boot info script after work.  Unfortunately I have to head out now.  I'll bump the thread this evening with results

---

### Post by chejrw on 2010-05-04
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   311,082,659   311,082,597  83 Linux
/dev/sda2         311,082,660   312,576,704     1,494,045   5 Extended
/dev/sda5         311,082,723   312,576,704     1,493,982  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 2,045,331,539 2,045,331,477  83 Linux
/dev/sdc2       2,045,331,540 2,930,272,064   884,940,525  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0b32a2cf-dbf9-4fa5-94ce-1e6f0aa4a456   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        eb4317b5-79ba-47a5-be8d-46fbcedba752   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9eaed51b-0147-42b2-8f98-df253b61f783   ext3                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        798c8b78-63d1-4c15-96cd-91ffb9c194c7   ext3                                     
/dev/sdc2        f22d2cd1-9850-4ca1-a87a-fc1c469c7c50   ext3                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
color cyan/blue white/blue

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
# kopt=root=UUID=0b32a2cf-dbf9-4fa5-94ce-1e6f0aa4a456 ro

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=0b32a2cf-dbf9-4fa5-94ce-1e6f0aa4a456 ro quiet splash
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=0b32a2cf-dbf9-4fa5-94ce-1e6f0aa4a456 ro single

title		Ubuntu 10.04 LTS, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0b32a2cf-dbf9-4fa5-94ce-1e6f0aa4a456 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0b32a2cf-dbf9-4fa5-94ce-1e6f0aa4a456 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 10.04 LTS, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0b32a2cf-dbf9-4fa5-94ce-1e6f0aa4a456 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0b32a2cf-dbf9-4fa5-94ce-1e6f0aa4a456 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 10.04 LTS, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0b32a2cf-dbf9-4fa5-94ce-1e6f0aa4a456 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0b32a2cf-dbf9-4fa5-94ce-1e6f0aa4a456 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 10.04 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=0b32a2cf-dbf9-4fa5-94ce-1e6f0aa4a456 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=eb4317b5-79ba-47a5-be8d-46fbcedba752 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
UUID=9eaed51b-0147-42b2-8f98-df253b61f783	/home/xgen/Group_Files	ext3	defaults	0	0
/dev/sda1	/home/xgen/TB_drive	ext2	defaults	0	0

=================== sda1: Location of files loaded by Grub: ===================


    .3GB: boot/grub/menu.lst
    .3GB: boot/grub/stage2
    .2GB: boot/initrd.img-2.6.20-16-generic
    .2GB: boot/initrd.img-2.6.20-16-generic.bak
    .3GB: boot/initrd.img-2.6.22-14-generic
    .3GB: boot/initrd.img-2.6.22-14-generic.bak
    .3GB: boot/initrd.img-2.6.24-16-generic
    .3GB: boot/initrd.img-2.6.24-16-generic.bak
    .3GB: boot/vmlinuz-2.6.20-16-generic
    .3GB: boot/vmlinuz-2.6.22-14-generic
    .3GB: boot/vmlinuz-2.6.24-16-generic
    .4GB: boot/vmlinuz-2.6.32-21-generic
    .3GB: initrd.img
    .3GB: initrd.img.old
    .3GB: vmlinuz
    .3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  d7 83 de 83 0e 28 0a 28  70 07 01 01 0e 2c 10 2c  |.....(.(p....,.,|
00000010  c5 69 a1 82 f9 60 f9 60  f9 60 f9 60 ec 83 d9 60  |.i...`.`.`.`...`|
00000020  d9 60 d9 60 d9 60 d9 60  d9 60 50 72 65 73 73 20  |.`.`.`.`.`Press |
00000030  22 45 6e 74 65 72 22 20  74 6f 20 73 65 6c 65 63  |"Enter" to selec|
00000040  74 0d 74 68 65 20 73 65  74 00 50 72 65 73 73 20  |t.the set.Press |
00000050  18 19 20 66 6f 72 20 6c  6f 67 69 63 61 6c 20 64  |.. for logical d|
00000060  72 69 76 65 0d 69 6e 66  6f 72 6d 61 74 69 6f 6e  |rive.information|
00000070  20 6f 72 20 70 72 65 73  73 20 45 53 43 20 74 6f  | or press ESC to|
00000080  0d 65 78 69 74 00 50 72  65 73 73 20 22 45 6e 74  |.exit.Press "Ent|
00000090  65 72 22 20 74 6f 20 73  65 6c 65 63 74 20 0d 66  |er" to select .f|
000000a0  69 72 73 74 20 64 72 69  76 65 00 66 61 9a 61 cf  |irst drive.fa.a.|
000000b0  61 03 62 38 62 6d 62 50  72 65 73 73 20 22 45 6e  |a.b8bmbPress "En|
000000c0  74 65 72 22 20 74 6f 20  73 65 6c 65 63 74 0d 66  |ter" to select.f|
000000d0  69 72 73 74 20 64 72 69  76 65 20 6f 66 20 74 68  |irst drive of th|
000000e0  65 20 72 61 69 64 0d 73  65 74 00 50 72 65 73 73  |e raid.set.Press|
000000f0  20 22 45 6e 74 65 72 22  20 74 6f 20 73 65 6c 65  | "Enter" to sele|
00000100  63 74 0d 73 65 63 6f 6e  64 20 64 72 69 76 65 20  |ct.second drive |
00000110  6f 66 20 74 68 65 20 72  61 69 64 0d 73 65 74 00  |of the raid.set.|
00000120  50 72 65 73 73 20 22 45  6e 74 65 72 22 20 74 6f  |Press "Enter" to|
00000130  20 73 65 6c 65 63 74 0d  74 68 69 72 64 20 64 72  | select.third dr|
00000140  69 76 65 20 6f 66 20 74  68 65 20 72 61 69 64 0d  |ive of the raid.|
00000150  73 65 74 00 50 72 65 73  73 20 22 45 6e 74 65 72  |set.Press "Enter|
00000160  22 20 74 6f 20 73 65 6c  65 63 74 0d 66 6f 75 72  |" to select.four|
00000170  74 68 20 64 72 69 76 65  20 6f 66 20 74 68 65 20  |th drive of the |
00000180  72 61 69 64 0d 73 65 74  00 50 72 65 73 73 20 22  |raid.set.Press "|
00000190  45 6e 74 65 72 22 20 74  6f 20 73 65 6c 65 63 74  |Enter" to select|
000001a0  0d 73 6f 75 72 63 65 20  64 72 69 76 65 20 6f 66  |.source drive of|
000001b0  20 74 68 65 20 72 61 69  64 0d 73 65 74 00 00 01  | the raid.set...|
000001c0  01 00 83 fe ff ff 3f 00  00 00 15 48 e9 79 00 fe  |......?....H.y..|
000001d0  ff ff 83 fe ff ff 54 48  e9 79 ed 1e bf 34 00 00  |......TH.y...4..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

There's the result of the script.

Help is greatly appreciated.

---

### Post by sysdrum on 2010-05-05
I had the same problem at first I had to do a fresh install of 10.4 to fix it. It hung when trying to rebuild after the upgrade. I am sorry I am still picking up the pieces myself.
I have drive that refuses to stay mounted.

---

### Post by martin9-w on 2010-05-05
I have the save problem. After the kernel panic i start again. Before i activate the grub prompt i edit it and i saw that the root-parameter looks like root=dev/sda1 and not root=/dev/sda1. the "/" was missing before "dev". I correct it and boot directly after pressing "b". 
Now my ubuntu-installation starts. And after correcting the "menu.lst" file in /boot/grub and a "grub-install hd0" all is fixed.

---

### Post by chejrw on 2010-05-05
> **martin9-w said:**
> I have the save problem. After the kernel panic i start again. Before i activate the grub prompt i edit it and i saw that the root-parameter looks like root=dev/sda1 and not root=/dev/sda1. the "/" was missing before "dev". I correct it and boot directly after pressing "b". 
Now my ubuntu-installation starts. And after correcting the "menu.lst" file in /boot/grub and a "grub-install hd0" all is fixed.

I'm referencing my root partition by UUID, which is supposedly the 'preferred' way, but I'll give that a try and see what happens.

---

### Post by javierrivera on 2010-05-05
The fstab file on sda1 seems to be trying to mount the same partition twice, by uuid as / and by /dev/sda1 as /home/xgen...

But I don't really expect this to be the problem.

---

### Post by kansasnoob on 2010-05-05
> **javierrivera said:**
> The fstab file on sda1 seems to be trying to mount the same partition twice, by uuid as / and by /dev/sda1 as /home/xgen...

But I don't really expect this to be the problem.

Actually I think that might be the problem!

I see nothing wrong in the menu.lst, but that fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=0b32a2cf-dbf9-4fa5-94ce-1e6f0aa4a456 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=eb4317b5-79ba-47a5-be8d-46fbcedba752 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
UUID=9eaed51b-0147-42b2-8f98-df253b61f783	/home/xgen/Group_Files	ext3	defaults	0	0
/dev/sda1	/home/xgen/TB_drive	ext2	defaults	0	0

```

I'd bet that's causing a kernel panic. This is a very basic Lucid fstab from a testing install with a separate /home:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda18      /               ext4    errors=remount-ro 0       1
/dev/sda19      /home           ext4    defaults        0       2
# swap was on /dev/sda11 during installation
UUID=bf502251-6ccd-4b66-8f9a-458603a6d2f2 none            swap    sw              0       0
```

You'll notice that CD/DVD drives are no longer mounted in fstab, I believe mountall takes care of that earlier in the boot process now.

So I'd edit that fstab by commenting out that:

```
/dev/sda1	/home/xgen/TB_drive	ext2	defaults	0	0

```

and also the cdrom mounts like this (edits in red):

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=0b32a2cf-dbf9-4fa5-94ce-1e6f0aa4a456 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=eb4317b5-79ba-47a5-be8d-46fbcedba752 none            swap    sw              0       0
**[COLOR="Red"]#[/COLOR]**/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
**[COLOR="Red"]#[/COLOR]**/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
UUID=9eaed51b-0147-42b2-8f98-df253b61f783	/home/xgen/Group_Files	ext3	defaults	0	0
**[COLOR="Red"]#[/COLOR]**/dev/sda1	/home/xgen/TB_drive	ext2	defaults	0	0
```

I'd do it by using nano in a chroot like this:

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
nano /etc/fstab
```

Then comment out the aforementioned lines, save the changes, double check with:

```
cat /etc/fstab
```

Then exit the chroot and unmount:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

But nano can seem complicated if you've never used it before:

[http://www.debianadmin.com/nano-editor-tutorials.html#more-73](http://www.debianadmin.com/nano-editor-tutorials.html#more-73)

---

### Post by chejrw on 2010-05-09
Thanks for the input guys.

I changed root=UID=(the UID of my drive) to root=/dev/sda1 in the boot line and I got a heck of a lot further in the boot process.

Still hangs during boot, but it seems we're making progress.  Now I'm getting the following errors on boot now (see attached image)

I'll try the fstab changes suggested by kansasnoob and report back.

I really appreciate the help.

---

### Post by chejrw on 2010-05-09
After making the changes suggested, I was able to boot into recovery mode.  I ran dpkg to finish the upgrade that failed initially.

The system then failed to boot because of a graphics card issue - booted into Command Line mode and installed new nVidia drivers.

Then apt threw a hissy fit because of the well documented problem with the flashplugin-nonfree package.

Finally got that resolved too.

I still have a few bugs to work out but at least the system boots again.

I'm really glad I only do the LTS release upgrades so I don't have to deal with this every 6 months.

---

