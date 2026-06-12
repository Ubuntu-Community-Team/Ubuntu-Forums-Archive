---
title: "Dude, Where's my Vista!?"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by HimK12 on 2007-09-16
Ok...so I followed these instructions to install ubuntu 7.10 on my hp desktop.

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

But with 1 minor difference...I already had 2 partitions...with one being used for storage...so I just formatted it and installed ubuntu on it. 

My ubuntu is running fine, but now when the boot menu comes up, I see the 3 ubuntu related choices..but no vista in that list. What am I missing?

Thanks,

---

### Post by forestpixie on 2007-09-16
Open a terminal and post the output of these

```
sudo fdisk -l
```

```
cat /boot/grub/menu.lst
```

---

### Post by happy-and-lost on 2007-09-16
Are you sure one of those partitions wasn't an HP recovery partition?

---

### Post by forestpixie on 2007-09-16
> **happy-and-lost said:**
> Are you sure one of those partitions wasn't an HP recovery partition?

mmm - bet it was, we'll find out soon :(

---

### Post by HimK12 on 2007-09-16
Device Boot      Start         End      Blocks   Id  System
/dev/hda2               1        9728    78140128+   f  W95 Ext'd (LBA)
/dev/hda5            4463        9728    42299113+   7  HPFS/NTFS
/dev/hda6               1        3647    29294433   83  Linux
/dev/hda7            3648        4462     6546456   82  Linux swap / Solaris

Partition table entries are not in disk order

_____________________________________________________________________________________
title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=bfd8dc03-5eae-4d18-a463-4e30cd7de2fb ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=bfd8dc03-5eae-4d18-a463-4e30cd7de2fb ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=bfd8dc03-5eae-4d18-a463-4e30cd7de2fb ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=bfd8dc03-5eae-4d18-a463-4e30cd7de2fb ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet



It wasnt rcovery partition...I had formatted my 80 gig hard drive once before into 45 and 35 gig before.

---

### Post by insane_alien on 2007-09-16
looks like you maybe formatted the windows partition instead of the storage partition.

---

### Post by HimK12 on 2007-09-16
Nope...I can still see the partition in linux with all the windows directories, program files, .... but obv..cant access any file.

---

### Post by Pumalite on 2007-09-16
Looks like your Widows is in sda5, but your recovery partition might be gone. If I'm right you just need to chainload windows in your menu.lst

---

### Post by HimK12 on 2007-09-16
ok...how do I do that?

My vista is in hd 0,5.

---

### Post by Pumalite on 2007-09-16
Backup your menu.lst first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back, then:
Add this to the end of your menu.lst:

tittle    Windows Vista
rootnoverify  (hd0,4)
makeactive
chainloader     +1

---

### Post by forestpixie on 2007-09-16
you might need to have > title Windows Vista

don't know enough to know if the typo would make a difference

---

### Post by HimK12 on 2007-09-16
Yeah...I saw that typo. But still..I get windows vista to show up in my grub menu..but when I enter it, I get the following error:

Error 12 : Invalid Device requested.

---

### Post by Pumalite on 2007-09-16
[http://users.bigpond.net.au/hermanzone/p15.htm#12_](http://users.bigpond.net.au/hermanzone/p15.htm#12_)

Post you new menu.lst

---

### Post by HimK12 on 2007-09-16
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
# kopt=root=UUID=539dbaf5-1bf6-4de6-b759-a2713a73d947 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=539dbaf5-1bf6-4de6-b759-a2713a73d947 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=539dbaf5-1bf6-4de6-b759-a2713a73d947 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=539dbaf5-1bf6-4de6-b759-a2713a73d947 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=539dbaf5-1bf6-4de6-b759-a2713a73d947 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

title           Windows vista
rootnoverify    (hd0,4)
makeactive
chainloader     +1

---

### Post by Pumalite on 2007-09-16
Get Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
And place a boot flag in sda5 and sda6
(it bothers me not to see an sda1 in your fdisk)

---

### Post by HimK12 on 2007-09-16
I can only flag one partition as boot. so ...its either gonna be hda5 or hda6. I tried doing it both ways..and vista still does not boot up.  Do I need to modify :

title Windows vista
rootnoverify (hd0,4)
makeactive
chainloader +1

---

### Post by Pumalite on 2007-09-16
No. (hd0,4) is right. The problem is the missing sda1. I would save all data and start fresh. I would DBan: [http://dban.sourceforge.net/](http://dban.sourceforge.net/) the drive, then use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) to prepare the drive, then install.
Before you do all that try re-installing Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Or use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Read more on error 12:

I received this error while trying to boot Windows XP in a logical partition. Normally, Windows is only bootable in a primary partition, because only a primary partition can be set  as 'active'. However, the Windows  default method of dual booting more than one Windows system installs the boot-up files in the previously existing Windows installation, and the subsequent Windows installation boots via the original installation. In this case, Windows users call their original installation their 'boot partition'.
Unfortunately for a some unlucky Windows users, once the installation has been completed that way, it means if they delete thier original installation, it becomes impossible to boot their new installation, which may be in a logical partition.

---

### Post by HimK12 on 2007-09-18
Got it to work. Read here how:

[http://ubuntuforums.org/showthread.php?t=552832](http://ubuntuforums.org/showthread.php?t=552832)

Post # 36.

---

### Post by Pumalite on 2007-09-18
Thank you for posting your solution.

---

