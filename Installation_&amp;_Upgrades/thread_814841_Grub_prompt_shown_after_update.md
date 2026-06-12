---
title: "Grub prompt shown after update"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by freefrags on 2008-06-01
hi all,

i updated my hadry heron now when i boot grub shows me a a prompt grub> instead of just continueing to boot i hope you can help me out with this

i tried the following:

===========================
find /boot/grub/stage1

This will locate your boot partition. If you already know the location, you can ignore this step.

root (hd0,0)

Replace the (hd0,0) by your boot partition number. If your Ubuntu is installed in the second partition, then change it to (hd0,1)

setup (hd0)
quit

Reboot your system. You should be able to access the Grub bootloader now.

=====================

how ever it doesnt work for me

---

### Post by hal8000 on 2008-06-01
What was the output from find /boot/grub/stage1
in your case.

(hd0,0) is the first partition on the first hard drive, so I take it you have no dual boot, no windows and no other OS on your hard drive?

If you run setup (hd0,0) you've told grub to install into the first partition and setup (hd0) to install grub loader code into the mbr.


If you can boot from the Hardy Heron 8.04 Live CD post the following output
please:
fdisk -l

Also output of
dmesg | grep sd

we'll see what happens once we have the extra information.

---

### Post by freefrags on 2008-06-01
yes your right i had a single boot of ubuntu. no other oses were installed i have two hard drives in the computer. i talked to someone he said it might be something with the menu.lst but before he could help me he had to leave maybe this helps? as i cant seem to fint the menu.lst 

thnx for your quick reply!

ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ dmesg | grep sd
[   74.129195] Driver 'sd' needs updating - please use bus_type methods
[   74.129259] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   74.129270] sd 0:0:0:0: [sda] Write Protect is off
[   74.129272] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   74.129288] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   74.129333] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   74.129342] sd 0:0:0:0: [sda] Write Protect is off
[   74.129344] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   74.129359] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   74.129362]  sda:<6>ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   74.199496]  sda1 sda2 < sda5 >
[   74.225296] sd 0:0:0:0: [sda] Attached SCSI disk
[   74.225375] sd 2:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[   74.225396] sd 2:0:0:0: [sdb] Write Protect is off
[   74.225401] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   74.225432] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   74.225502] sd 2:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[   74.225531] sd 2:0:0:0: [sdb] Write Protect is off
[   74.225533] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   74.225548] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   74.225551]  sdb:<6>ata5.00: ATAPI: MATSHITADVD-RAM UJ-846S, F100, max UDMA/33
[   74.568757]  sdb1
[   74.568839] sd 2:0:0:0: [sdb] Attached SCSI disk
[   74.572837] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   74.572857] sd 2:0:0:0: Attached scsi generic sg1 type 0
[  152.140946] sdhci: Secure Digital Host Controller Interface driver
[  152.140949] sdhci: Copyright(c) Pierre Ossman
[  152.310585] sdhci: SDHCI controller found at 0000:06:0b.3 [104c:803c] (rev 0)
[  155.286038] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
ubuntu@ubuntu:~$

---

### Post by freefrags on 2008-06-01
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d706f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00046c01

   Device Boot      Start         Endubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d706f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00046c01

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux
      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

lol sorry this fdisk -l info is more intresting i think ;)

---

### Post by freefrags on 2008-06-01
this might be of some use too i found the menu.lst is on my disk-1

ubuntu@ubuntu:~$ sudo find / -name menu.lst
/media/disk-1/usr/share/doc/grub/examples/menu.lst
/media/disk-1/boot/grub/menu.lst
/usr/share/doc/grub/examples/menu.lst
find: /home/ubuntu/.gvfs: Permission denied
/rofs/usr/share/doc/grub/examples/menu.lst
ubuntu@ubuntu:~$

this is the contents of the menu.lst

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
timeout		3

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
# kopt=root=UUID=056cb1c2-a2be-4ad4-8e49-5d045403b5a6 ro

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

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=056cb1c2-a2be-4ad4-8e49-5d045403b5a6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=056cb1c2-a2be-4ad4-8e49-5d045403b5a6 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=056cb1c2-a2be-4ad4-8e49-5d045403b5a6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=056cb1c2-a2be-4ad4-8e49-5d045403b5a6 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=056cb1c2-a2be-4ad4-8e49-5d045403b5a6 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=056cb1c2-a2be-4ad4-8e49-5d045403b5a6 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by PmDematagoda on 2008-06-01
Post the output of:-
```
cat /media/disk-1/boot/grub/menu.lst
```

---

### Post by freefrags on 2008-06-01
i added the contents of the menu.lst to the previous post i guess i was a bit too slow ;)

---

### Post by PmDematagoda on 2008-06-01
Try recovering GRUB using the SuperGRUB CD found [here]("http://sgd.benjamin-butschko.de/download/binaries/sgd/cdrom/supergrubdisk_0.9677.iso").

---

### Post by freefrags on 2008-06-01
ok i have downloaded the cd and tried to recover grub however it doesnt work it reboots and shows the grub prompt once again. :S

---

### Post by unutbu on 2008-06-01
This is from [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Im_getting_a_black_screen_with_a_grub_](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Im_getting_a_black_screen_with_a_grub_)
> I'm getting a black screen with a grub>_ prompt
Usually this means GRUB's stage1 and stage1_5 files in the MBR and first track of the hard disk are okay, and stage2 in the Linux partition is alright but there is no menu.lst file or if there is one it has been renamed or moved.
Super Grub Disk can help you by booting your Linux kernel and initrd.img directly (via symlinks), so you will be bypassing the menu.lst file.

   1. boot your SGD floppy disk, USB disk or CD-ROM
   2. English Super Grub Disk
   3. Gnu/Linux
   4. Boot Gnu/Linux Directly


Is this what you tried?

---

### Post by freefrags on 2008-06-02
exactly but no cigar.

---

### Post by freefrags on 2008-06-02
My fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=056cb1c2-a2be-4ad4-8e49-5d045403b5a6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=9703eed9-f560-4fd9-8648-d6e757c3d160 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
# /dev/sdb1
#/dev/sdb1	/media/datadisk	ext3	defaults	0	2

---

### Post by unutbu on 2008-06-02
Please post

```
ls -lR /media/disk-1/boot
```

---

