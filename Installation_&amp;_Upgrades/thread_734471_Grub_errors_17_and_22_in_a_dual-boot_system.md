---
title: "Grub errors 17 and 22 in a dual-boot system"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by Boatswain on 2008-03-24
Hi all,

Thanks in advance for any and all help.

I recently got this computer up and running with a dual-boot XP/gutsy system, with xp on one drive and ubuntu on the other (rather than just on separate partitions on the same drive). Today I used GParted to shrink the partition that Ubuntu is on, and moved it right. The blank space left over I made into an undefined partition, then rebooted the system into XP. All went well, no problems.

In XP, I selected the undefined partition and formatted it as NTFS, Easy.

Then I rebooted and saw "Grub Error 17."

Hmm, thinks I, that must be because Grub no longer knows where the boot sector is. I'd best go change that. So I do, changing the (1,0) that used to point to the Ubuntu partition to  (1,1) to point to where it is now.

It  doesn't work. Hmmm. Well, maybe I'll change it back, then.

Still  no dice.

Okay, I'll delete the partition I created.

Well, at least now I'm getting a different error--this time it's Grub Error 22.

Here is the current state of my /boot/grub/menu.lst:

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
# kopt=root=UUID=48f1283d-6a00-4d2d-9819-0acc9099b4e0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=48f1283d-6a00-4d2d-9819-0acc9099b4e0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=48f1283d-6a00-4d2d-9819-0acc9099b4e0 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
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
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

and here is the result of fdisk -l:

```
ubuntu@ubuntu:/media/disk$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x83b883b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d9878

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *        4664        9327    37463580   83  Linux
/dev/sdb3            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris

```

As previously mentioned, any and all help is much appreciated.

---

### Post by confused57 on 2008-03-24
If you're getting a grub boot menu, press "c", you should get a grub prompt(grub>), enter:
```
find /sbin/init
```

This "should" show your root partition, i.e. (hd1,0), (hd1,1)...which is what "should' work in your menu.lst.  I don't know if anything you did may have changed the UUID of the partition...you could boot the live cd, enter:
```
blkid
```
compare the UUID from blkid with the UUID in your menu.lst.

Type "quit", without quotes, to exit the grub prompt.

---

### Post by Boatswain on 2008-03-24
Some things I've learned while scouring the net:

Grub Error 17 means that Grub saw the partition it was pointed at, but couldn't access it due to filesystem issues. This makes sense, as before I deleted that new partition, it was NTFS, which Grub might have had trouble with.

Grub Error 22 means that Grub couldn't find a partition where it was being pointed at. This makes sense too, given that it showed up after I deleted the partition that caused the problems in the first place.

What I don't understand is how to fix the problem. I've edited menu.lst so that the default grub root device is (1,1). I've even tried (1,2), and of course (1,0) doesn't work. Each time I try that I also change the root locations for the kernel, for generic, recovery mode, and memtest.

From the fdisk -l, it looks to me like the boot partition should be (1,1)--I'm assuming that that's what /dev/sdb2 translates to in Grubspeak. So why isn't it working? Does the boot partition have to be the first one on the disk?

Again, any help would be great.

---

### Post by Boatswain on 2008-03-24
Thanks for the response--you added that while I was adding my second post. I'm running all of this off the live CD--the Grub error happens at 1.5, so before the Grub menu comes up.

find /sbin/init returns:
 (hd1,1)

and blkid returns:

```
/dev/sda1: UUID="6C1834001833C7BA" TYPE="ntfs" 
/dev/sdb2: UUID="48f1283d-6a00-4d2d-9819-0acc9099b4e0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="fda5b973-611d-4680-8cca-828ee81c80ee" 
```

So to me it still looks like (1,1) should do the trick. But it doesn't....

---

### Post by confused57 on 2008-03-24
You might want to use the live cd to run a filesystem check:
[http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_](http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_)

You can either use the GUI method or command line.

---

### Post by Boatswain on 2008-03-24
Well, I went the GUI route and ran GParted, unmounted the drive, and checked the partition (sdb2), and got green check marks and assurances that all was well as far as the partition goes.

Sadly, when I rebooted, I still got 

GRUB 1.5
Error 22

so I don't really know what to try now. I'm considering just using GParted to move the boot partition to the "left", so that it's the first thing on the drive, but I'm leery of adding more complications.

---

### Post by confused57 on 2008-03-24
> **Boatswain said:**
> Well, I went the GUI route and ran GParted, unmounted the drive, and checked the partition (sdb2), and got green check marks and assurances that all was well as far as the partition goes.

Sadly, when I rebooted, I still got 

GRUB 1.5
Error 22

so I don't really know what to try now. I'm considering just using GParted to move the boot partition to the "left", so that it's the first thing on the drive, but I'm leery of adding more complications.
About the only thing I can suggest is to try reinstalling grub:
```
sudo grub
find /boot/grub/stage1
```
this should return "root (hd1,1)", then enter:
```
root (hd1,1)
setup (hd0)
quit
```

---

### Post by Boatswain on 2008-03-25
> **confused57 said:**
> About the only thing I can suggest is to try reinstalling grub:
```
sudo grub
find /boot/grub/stage1
```
this should return "root (hd1,1)", then enter:
```
root (hd1,1)
setup (hd0)
quit
```

OK, thanks for the suggestion. Before I execute that though, what will the consequences be? Does that set up hd0 as the boot disk, and if so, will that work given that I'm on a 2-drive dual-boot system? Just want to know what I'm getting into before I carry on.

---

### Post by confused57 on 2008-03-25
> **Boatswain said:**
> OK, thanks for the suggestion. Before I execute that though, what will the consequences be? Does that set up hd0 as the boot disk, and if so, will that work given that I'm on a 2-drive dual-boot system? Just want to know what I'm getting into before I carry on.
If grub was installed to the mbr of your Windows hard drive, designating (hd0) would install grub to your Window's drive's mbr...this would work if you were booting first to your Windows drive when you first installed Ubuntu and booted both OSes from grub.

Alternatively, if you get a functional Windows bootloader when you boot first to your Windows drive, then you would issue "setup (hd1)", which would install grub's IPL(Initial Program Loader) to the 2nd drive's mbr(Ubuntu drive).  You would then need to change your root in your menu.lst to (hd0,1), if you boot first to your Ubuntu drive.

Yes, in answer to your question "setup (hd0)" would install grub to the Windows drive's mbr...Is that what you want to do?

---

### Post by Boatswain on 2008-03-25
> **confused57 said:**
> If grub was installed to the mbr of your Windows hard drive, designating (hd0) would install grub to your Window's drive's mbr...this would work if you were booting first to your Windows drive when you first installed Ubuntu and booted both OSes from grub.

Alternatively, if you get a functional Windows bootloader when you boot first to your Windows drive, then you would issue "setup (hd1)", which would install grub's IPL(Initial Program Loader) to the 2nd drive's mbr(Ubuntu drive).  You would then need to change your root in your menu.lst to (hd0,1), if you boot first to your Ubuntu drive.

Yes, in answer to your question "setup (hd0)" would install grub to the Windows drive's mbr...Is that what you want to do?

OK, sounds good, thanks for the explanation. I'm going to try that out now and see what happens,

EDIT: Hey, it worked!  Thanks a million, you are my new favorite person (for at least the next five minutes)!

---

### Post by confused57 on 2008-03-25
> **Boatswain said:**
> OK, sounds good, thanks for the explanation. I'm going to try that out now and see what happens,

EDIT: Hey, it worked!  Thanks a million, you are my new favorite person (for at least the next five minutes)!
With my 20/20 hindsight, I should have suggested to reinstall grub initially...glad it worked.

---

