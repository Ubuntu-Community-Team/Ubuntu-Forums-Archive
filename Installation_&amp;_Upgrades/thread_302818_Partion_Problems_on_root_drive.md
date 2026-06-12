---
title: "Partion Problems on root drive"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by taddy_porter on 2006-11-19
I recently put 6.10 on my computer. I was previously using Suse and had a large root drive for Suse. I ran out of space on the Ubuntu portion so I took some empty space from the Suse part. My goal then was to move that over to the Ubuntu root drive.

Unfortunatly I managed to screw up my partition. /DEV/HDD is where my root is. It should be partioned to 1 swap partion, 2 ext3 partions and 1 empty partion. It just shows as unallocated though.

Strangely, the system still boots. Now, is there any way to restore the table?

---

### Post by taddy_porter on 2006-11-19
Running fdisk -l shows the correct partions. It's the gnome partion manager that shows it being unallocuted.

The 4th partition I tried to create is showing as LVN. Can I delete it/modify it using FDISK manually to extend my root drive and fix the partion so it is read correctly in QTPARTED?

---

### Post by hal10000 on 2006-11-19
Hi,

post the output of your partition table: [COLOR="Red"]fdisk -l[/COLOR].
I hope you did partitioning by using your ubuntu live CD or a Knoppix live-CD or a rescue-CD, because its always better if you fiddle around with partitioning. Maybe the program testdisk (which is usually provided on Knoppix live-CD's) can help if you have problems with your partitiom table .

---

### Post by taddy_porter on 2006-11-19
I did use a livecd, PCLINUXOS version. Here's my fdisk:

```
Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdd: 40.9 GB, 40981118976 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1         139     1116486   82  Linux swap / Solaris
/dev/hdd2             140        4982    38901334+   5  Extended
/dev/hdd5            1315        3707    19221741   83  Linux
/dev/hdd6             140        1314     9438124+  83  Linux
/dev/hdd7            3708        4982    10241406   8e  Linux LVM

Partition table entries are not in disk order

Disk /dev/hde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1       19457   156288321   42  SFS

Disk /dev/hdg: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1               1       24792   199141708+  83  Linux
taddy@taddy1:~$ 

```

---

### Post by hal10000 on 2006-11-19
Your fdisk output tells that on disk /dev/hdd the partition table entries are not in disk order. In most cases this is not a problem, but here this may be the reason for fail.

If you look to the output of [COLOR="Red"]fdisk -l[/COLOR] you can see that the "Start" and "End" cylinders of /dev/hdd6 have lower numbers than those of /dev/hdd5. Some Partition-tools have problems with this state.

If you are familiar in using command-line tools, here's a short description of the steps to perform:

1. boot a rescueCD (or better your ubuntu live-CD) and with fdisk fix the partition order of /dev/hdd.
2. mount ubuntu-partition and change /etc/fstab of your ubuntu-system to the demands of your new partition table.
3. mount /dev and /proc under the mountpoint of your ubuntu-system
4. chroot to your ubuntu-system.
5. run grub and on the grub command-line type: root (hd1,5) (if your ubuntu root-partition is /dev/hdd6)
5a. if your ubuntu root-partition is /dev/hdd5, then the appropriate command is: root (hd1,4).
6. still on the grub command-line type: setup (hd0) and quit grub.

That's all.

If you are not used to command-line tools:  

To make further steps, we have to be [COLOR="Red"]absolutely sure[/COLOR] in which partition your ubuntu and SuSE systems reside. Verify it exactly and post it. Also post the content of /boot/grub/menu.lst from your ubuntu system and the content of /etc/fstab from both ubuntu and SuSE systems.

Once we collected these informations, we make a step-by-step instruction of the above mentioned steps. But I can tell you, it's a hard work waiting for us.

So long

P.S.: sorry for my English

---

### Post by taddy_porter on 2006-11-20
Sorry, not familiar enough to do what you mentioned. Here's where my partions are:

HDC1 is /home (weird it shows as HPFS/NTFS it's actually ext3)
HDD5 is Ubuntu /
HDD6 is Suse /
HDD7 is what I took from Suse to try and extend Ubuntu
HDE1 is a faulty harddrive that I have commented out in fstab
HDG1 is a subfolder on /home
HDD1 is my swap
Not sure what HDD2 is

Here's my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd6
UUID=1f8eb8d3-1a28-4178-afb0-0a9ae4c986e2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc1
UUID=7f85abb2-3485-46ef-b0ee-5043d78372e5 /home           ext3    defaults        0       2
# /dev/hdd5
UUID=90f049b3-b580-45aa-b87e-8282d8cb64eb /media/hdd5     ext3    defaults        0       2
# /dev/hde1
#UUID=05ce2db9-ac8a-498f-821b-8dd5b28acb73 /media/hde1     #ext3    defaults        0       2
# /dev/hdd1
UUID=f7026208-4b48-45da-9501-e5b8cd43e3eb none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
//htpc/D /home/taddy/htpc smbfs uid=taddy,gid=users,username=defaults,password=defaults,fmask=666,dmask=777 0 0
//htpc/D /home/taddy/flac smbfs
/dev/hdg1 /home/taddy/download    ext3    defaults        0       2
```

Here's my grub:
```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd6 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd5.
title		SUSE Linux 10.1 (on /dev/hdd5)
root		(hd1,4)
kernel		/boot/vmlinuz root=/dev/hdd6 vga=0x317 acpi=off resume=/dev/hdd1 splash=silent showopts 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd5.
title		linux (/dev/hdd5) (on /dev/hdd5)
root		(hd1,4)
kernel		/boot/vmlinuz root=/dev/hdd5 vga=788 acpi=ht splash=verbose 
initrd		(hd1,4)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd5.
title		Failsafe -- SUSE Linux 10.1 (on /dev/hdd5)
root		(hd1,4)
kernel		/boot/vmlinuz root=/dev/hdd6 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd5.
title		Previous Kernel -- SUSE LINUX 10.1 (on /dev/hdd5)
root		(hd1,4)
kernel		/boot/vmlinuz.previous root=/dev/hdd6 vga=0x317 acpi=off resume=/dev/hdd1 splash=silent showopts 
initrd		/boot/initrd.previous
savedefault
boot
```

Here's my Suse fstab:

```
/dev/hdd6	/	ext3	acl,user_xattr 1 1
/dev/hdc1	/home	ext3	defaults 1 2
/dev/hdd1	swap	swap	defaults 0 0
proc	/proc	proc	defaults 0 0
sysfs	/sys	sysfs	noauto 0 0
debugfs	/sys/kernel/debug	debugfs	noauto 0 0
usbfs	/proc/bus/usb	usbfs	noauto 0 0
devpts	/dev/pts	devpts	mode=0620,gid=5 0 0
//htpc/D /home/taddy/htpc smbfs uid=taddy,gid=users,username=defaults,password=defaults,fmask=666,dmask=777 0 0
//htpc/D /home/taddy/flac smbfs username=defaults,password=defaults 0 0
/dev/hdd5            /home/taddy/PCLOS    ext2       defaults              1 2
```

Thanks for the help.

---

### Post by taddy_porter on 2006-11-22
Here's my grub 
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
# kopt=root=UUID=1f8eb8d3-1a28-4178-afb0-0a9ae4c986e2 ro
# kopt_2_6=root=/dev/hdd6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd6 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd5.
title		SUSE Linux 10.1 (on /dev/hdd5)
root		(hd1,4)
kernel		/boot/vmlinuz root=/dev/hdd6 vga=0x317 acpi=off resume=/dev/hdd1 splash=silent showopts 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd5.
title		linux (/dev/hdd5) (on /dev/hdd5)
root		(hd1,4)
kernel		/boot/vmlinuz root=/dev/hdd5 vga=788 acpi=ht splash=verbose 
initrd		(hd1,4)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd5.
title		Failsafe -- SUSE Linux 10.1 (on /dev/hdd5)
root		(hd1,4)
kernel		/boot/vmlinuz root=/dev/hdd6 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd5.
title		Previous Kernel -- SUSE LINUX 10.1 (on /dev/hdd5)
root		(hd1,4)
kernel		/boot/vmlinuz.previous root=/dev/hdd6 vga=0x317 acpi=off resume=/dev/hdd1 splash=silent showopts 
initrd		/boot/initrd.previous
savedefault
boot

```

/dev/hdd2 seems to be the problem. It has the same start as /dev/hdd6. I have no idea what it is though. I didn't want to delete it because I'm not sure if it would do anything to my Ubuntu root (/dev/hdd6). I think I said hdd5 was Ubuntu before, but that's wrong.

---

### Post by hal10000 on 2006-11-23
Hi taddy_porter,
don't delete or change anything on your /dev/hdd2 partition. This is the extended partition, in which both of your linux-systems reside (it' a "container" for them.
At the moment I don't have time to help you going on, but tomorrow I hope I can.

---

### Post by taddy_porter on 2006-11-23
Well, I want to go ahead and delete my Suse partition. I already deleted my HDD7 partition. What I really want to do is just have Ubuntu on the disk and resize it to fill the disk.

I think I can do this with Parted and Fdisk. My only concern is that if I delete the Suse partition, my Ubuntu partition changes from hdd6 to hdd5. I'm not sure if I need to change the UUID in my fstab file.

Can you also verify for me that I would need to change my grub as well?

---

### Post by taddy_porter on 2006-11-24
I just reinstalled. Turned out to be easier.

---

