---
title: "Booting without F12 on a dual boot IDE/SATA setup"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by ergonomicben on 2007-11-13
I have two hdd the 1st has XP on (an IDE), the 2nd (a SATA) ubuntu. When booting up I have to select the primary master with F12 for Grub to load up, Is there anyway of getting it to load Grub without F12? I would have thought the bios would look in the primary master first for the OS/Boot loader?! (I've read some threads about this but I'm not quite sure if i can use their solutions)

Any help appreciated!

---

### Post by ergonomicben on 2007-12-07
Bump (sorry i really would like someones opinion on this! thanks)

---

### Post by Pumalite on 2007-12-07
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by ergonomicben on 2007-12-07
Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  de  Dell Utility
/dev/sda2   *       96390   234372284   117137947+   7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5661c1fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   386138339   193069138+  83  Linux
/dev/sdb2       386138340   398283479     6072570    5  Extended
/dev/sdb5       386138403   398283479     6072538+  82  Linux swap / Solaris

---

### Post by Pumalite on 2007-12-07
Where is menu.lst?

---

### Post by ergonomicben on 2007-12-07
Sorry my bad!

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
# kopt=root=UUID=b3bf2544-3ad0-4a0d-a52f-7a7c0dd2c5bb ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b3bf2544-3ad0-4a0d-a52f-7a7c0dd2c5bb ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b3bf2544-3ad0-4a0d-a52f-7a7c0dd2c5bb ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

---

### Post by Pumalite on 2007-12-07
Change this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Home Edition
root (hd0,1)
savedefault
makeactive
chainloader +1
To this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Home Edition
rootnoverify (hd0,1)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1
Save, exit, reboot.
Make sure to backup first.

---

### Post by ergonomicben on 2007-12-07
Thanks for the replies!
If this didn't work would there still be a way of booting through f12 for example? i don't want to be stuck without being able to boot an OS!!

---

### Post by Pumalite on 2007-12-07
Yes

---

### Post by ergonomicben on 2007-12-07
Cheers
Sorry to be a total noobie but how do i alter the file menu.lst? i don't know how to log in as root so i can't save any changes!

---

### Post by Pumalite on 2007-12-07
At the Terminal:
backup first
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back
gksudo gedit /boot/grub/menu.lst
Make the changes, save, exit, reboot.

---

### Post by ergonomicben on 2007-12-07
i made the changes and it saved fine. restarted and still didn't boot properly, i had to select the primary master with F12 still. any ideas what's wrong?

---

### Post by Pumalite on 2007-12-07
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

### Post by ergonomicben on 2007-12-07
> **Pumalite said:**
> [http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

I don't think those can help me because i don't think the problem is with grub because it works fine when the bios knows where to look for it.(i tell it to look in the primary master drive) so I think the problem is with the bios.

What doesn't make sense to me is i set the bios to look in c: which is the primary master  but it can't seem to find it. Similarly if through f12 i tell it to look at c: it can't find it. Only when i tell it through f12 to look at the primary master it finds it. To me that seems like a contradiction, the primary master is the c: drive !

---

### Post by Pumalite on 2007-12-07
The problem is the mix of SATA and IDE. I would install everything in the SATA drive (keep it as Master) and keep the IDE for storage.

---

### Post by ergonomicben on 2007-12-07
That would be the sensible thing to do, but unfortunately i think it's going to be too much hassle for me to reinstall everything on both os's, looks like i'm stuck with f12!

---

### Post by Pumalite on 2007-12-07
Well; you can't say we didn't give it a go.

---

### Post by lha on 2007-12-07
> **ergonomicben said:**
> I don't think those can help me because i don't think the problem is with grub because it works fine when the bios knows where to look for it.(i tell it to look in the primary master drive) so I think the problem is with the bios.

I agree.

> **ergonomicben said:**
> That would be the sensible thing to do, but unfortunately i think it's going to be too much hassle for me to reinstall everything on both os's, looks like i'm stuck with f12!

You're not stuck with F12. It sounds you have used some sort of 'boot once from this hard drive' -option. Usually, you can set bios to boot from a given hard drive on each boot. Try if you find such a setting. If such an option is not available, there's still a way for convenient dual boot. You can add grub into Windows' boot loader. It can be done manually or with software such as [BootPart]("http://www.winimage.com/bootpart.htm").

---

### Post by froy02 on 2007-12-08
grub may not be installed in the  any of your drives because they look like they start booting from from sector 63. instead of sector 1. 
_____________
when you boot from ubuntu does it show the menu to choose the os to boot?
If it does show the entry for the menu.lst then the entry for root should be change from "root (hd0,1)" to '"root (hd0,0) since linux start counting from 0 and not 1.  

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Home Edition
root (hd0,1)
savedefault
makeactive
chainloader +1

If in case you want to install both os in 1 hard drive put them on the ide and make the sata your data drive put all your data on the sata drive and you can mount and unmount it from both windows and linux which make it safer since if it is not mounted nobody can read it unless you mount it again.
_____________

---

