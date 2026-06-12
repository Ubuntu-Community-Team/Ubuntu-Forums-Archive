---
title: "ubuntu install renders windows xp partition unbootable?"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by wickstopher on 2007-09-09
I recently installed Ubuntu 7.04 on a friends' machine.  Can't remember all the specs offhand, but it has 512MB ram, an and AMD64 dual-core processor.  It's manufactured by HP.  I used gparted to shrink his windows partition (which has worked fine for me in the past), and installed Ubuntu.  Booting up the computer, we get a grub menu with Ubuntu, Windows XP, and also some sort of PC recovery program that was installed on a separate partition.  The PC recovery program boots, Linux boots and runs beautifully, but when attempting to boot into the XP partition from grub, we get nothing.  It just says "Starting Up..." and hangs indefinitely (he left his computer on all night, woke up, and was still at the same screen.)  Has anybody experienced anything similar and found a solution?

---

### Post by Pumalite on 2007-09-09
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by wickstopher on 2007-09-10
```
 sudo fdisk -lu
Password:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   143364059    71681998+   7  HPFS/NTFS
/dev/sda2       294613200   312575759     8981280    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3       143364060   289844729    73240335   83  Linux
/dev/sda4       289844730   294599969     2377620   82  Linux swap / Solaris

Partition table entries are not in disk order
clay@megaman:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=55f12505-c5cb-4b52-8ec5-9d440b013cfd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##


title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=55f12505-c5cb-4b52-8ec5-9d440b013cfd ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=55f12505-c5cb-4b52-8ec5-9d440b013cfd ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP Media Center Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows NT/2000/XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```

---

### Post by merlinus on 2007-09-10
Comment out these lines (place a # in front of them) and restart.

title           Windows NT/2000/XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```

gksudo gedit /boot/grub/menu.lst

```

---

### Post by Pumalite on 2007-09-10
What is this entry doing in your menu.lst?:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows NT/2000/XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1

You have XP in sda1 and entry in menu.lst seems OK. I would change 'root' to rootnoverify. Maybe I would map it, but lets try that first. Don't forget to backup your menu.lst first.

---

### Post by wickstopher on 2007-09-10
That entry (the one you suggested to comment out) was the aforementioned Disk First Aid or some such utility.  Wasn't even visible pre-Ubuntu install.  I tried taking the steps you suggested,  and am getting the same results.  Thanks for the quick response!

---

### Post by Pumalite on 2007-09-10
I ran out of ideas. Someone will chime in.

---

### Post by merlinus on 2007-09-10
Post revised menu.lst and /boot/grub/device.map.

---

### Post by merlinus on 2007-09-10
I also am suspicious of the fact that sda1 begins at block 63 rather than block 1.  This may mean that some sort of hidden xp boot partition exists which have been overwritten when you installed ubuntu.

> 
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   143364059    71681998+   7  HPFS/NTFS
/dev/sda2       294613200   312575759     8981280    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3       143364060   289844729    73240335   83  Linux
/dev/sda4       289844730   294599969     2377620   82  Linux
 swap / Solaris
I would suggest trying supergrub to boot windows:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Info on its use here:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#situtions_where_sgd_is_useful](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#situtions_where_sgd_is_useful)

If that works, then it may be best to restore the windows bootloader to the mbr, and then reinstall grub to see if that make a difference.

---

### Post by wickstopher on 2007-09-26
Sorry I haven't responded in a while, but I haven't had the chance to go over and mess with this machine.  Anyhow, I am going over there tomorrow to check into it some more.  I've used super grub disk before, but only to restore grub, not to boot windows, and I'm unsure as to exactly how I would go about doing this.  I'm assuming I'll probably be able to figure it out, but if anyone has any suggestions they would be most welcome.  Also, if you don't mind, how would I go about restoring Windows to the MBR assuming I do get it up and running again?  Thanks for any input, and I'll let you know how it goes!

---

### Post by jasnils on 2007-09-27
I seem to have the **same problem**. Have you been able to solve yours?
If anyone knows how to solve this, **please do tell**.



jakob@VAIO-UBUNTU:~$ sudo fdisk -lu
Password:

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     9767519     4883728+   2  XENIX root
/dev/sda2   *     9767520    68372639    29302560    7  HPFS/NTFS
/dev/sda3        68372640   490223474   210925417+   f  W95 Ext'd (LBA)
/dev/sda5        68372703   382957470   157292384    7  HPFS/NTFS
/dev/sda6       382957533   384017759      530113+  82  Linux swap / Solaris
/dev/sda7       384017823   404500634    10241406   83  Linux
/dev/sda8       404500698   490223474    42861388+  83  Linux

Disk /dev/sdb: 65 MB, 65536000 bytes
8 heads, 32 sectors/track, 500 cylinders, total 128000 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          55      127999       63972+   1  FAT12
jakob@VAIO-UBUNTU:~$ cat /boot/grub/menu.lst
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
default         5

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
# kopt=root=UUID=743e2550-7a62-4bec-b737-45b25db0fe89 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
# defoptions=quiet splash boot:rescue

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
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=743e2550-7a62-4bec-b737-45b25db0fe89 ro quiet splash boot:rescue
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=743e2550-7a62-4bec-b737-45b25db0fe89 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=743e2550-7a62-4bec-b737-45b25db0fe89 ro quiet splash boot:rescue
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=743e2550-7a62-4bec-b737-45b25db0fe89 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,6)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows XP Media Center Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

---

