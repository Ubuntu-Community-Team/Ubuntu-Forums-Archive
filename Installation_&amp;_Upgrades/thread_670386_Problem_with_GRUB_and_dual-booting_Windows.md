---
title: "Problem with GRUB and dual-booting Windows"
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by BatPenguin on 2008-01-17
I've been trying to get dual-booting working with Ubuntu and Windows XP Home. My Ubuntu machine works great but the problem is that so far I have been unable to boot into Windows without restoring its MBR (fixboot / fixmbr commands from recovery CD) first. And when I do that, GRUB of course gets erased and wll have to be restored for me to be able to boot back into Ubuntu. Not very handly.

I've seen instructions on restoring GRUB / editing menu.lst but haven't been succesful in getting the machine to work.

Here's all the important data as far as I can tell:

the output of "sudo fdisk -l":

$ sudo fdisk -l
```

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24e924e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       18237   146488671    7  HPFS/NTFS
/dev/sda2   *       18238       30395    97659135   83  Linux
/dev/sda3           30396       32827    19535040   82  Linux swap / Solaris
/dev/sda4           32828       91201   468889155   83  Linux

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003e6dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux

```

My /etc/fstab:

$ cat /etc/fstab ```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=9f3c0793-db7e-4293-ae29-40ea5912ffc0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=22b7addf-ff3f-4c71-9028-0582775ac861 /home           ext3    defaults        0       2
# /dev/sdb1
UUID=17e8be2a-5bf0-4eb2-9753-033b10b5b308 /myth           xfs     defaults        0       2
# /dev/sda1
UUID=5A98C0F198C0CCA7 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=8b9375f1-a449-4c7b-b9fe-eab2f5c1e245 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

and finally  /boot/grub/menu.lst in all its glory:

```
$ cat /boot/grub/menu.lst
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
default         2

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
# kopt=root=UUID=9f3c0793-db7e-4293-ae29-40ea5912ffc0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
# defoptions=quiet splash irqpoll

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

title           Ubuntu 7.10, kernel 2.6.22-14-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-386 root=UUID=9f3c0793-db7e-4293-ae29-40ea5912ffc0 ro quiet splash irqpoll
initrd          /boot/initrd.img-2.6.22-14-386
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-386 root=UUID=9f3c0793-db7e-4293-ae29-40ea5912ffc0 ro single
initrd          /boot/initrd.img-2.6.22-14-386

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=9f3c0793-db7e-4293-ae29-40ea5912ffc0 ro quiet splash irqpoll
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=9f3c0793-db7e-4293-ae29-40ea5912ffc0 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
rootnoverify            (hd0,0)
makeactive
chainloader     +1

# XP: 0,1
title           Microsoft Windows XP 0,1
rootnoverify            (hd0,1)
makeactive
chainloader     +1

# XP: root, not noverify (0,0)
title           Microsoft Windows XP root 0,0
root                    (hd0,0)
makeactive
chainloader     +1

# XP: root, not noverify (0,1)
title           Microsoft Wndows XP root 0,1
root                    (hd0,1)
makeactive
chainloader     +1
```


As you can see, I've tried a bunch of different setups for Windows XP at the end there but none of those work. I was thinking the "rootnoverify" option might be a problem so I tried it with just "root", no go. After some more surfing today, it looks like rootnoverify is correct for NTFS but anyhow, I've tried all of the boot options listed above.

This is the normal error message i get when trying to boot Windows: (just black screen with a few lines of text):


```

Windows could not start because the following file is missing or corruput:

\<windowsroot>\system32\ntoskrnl.exe

```

...as far as I can tell, that's Windows error message nonsense, the problem seems to be that the Windows drive is not being mounted or it looks at the wrong partition for Windows files etc...I guess? If I fix it with the recovery CD, everything works great but when GRUB is restored, it breaks again.

All suggestions are welcome and I'd be happy to give you more information if I omitted something. Thanks!

---

### Post by Pumalite on 2008-01-17
Tell us a little bit more about the story of your installations. Ubuntu first? Windows first? Where did you install Grub? Were both drives connected when you installed?

---

### Post by BatPenguin on 2008-01-18
Thanks for the reply. OK, now that I think of it...yes, the installations were a bit "funny", I had to reinstall a few times because of a hard drive / motherboard problem. The SATA drives weren't being detected properly and both Ubuntu and Windows installs kept crashing until I reflashed the BIOS and found a nice BIOS setting for it (some IDE mode thing) AND set "noirqpoll" as a kernel boot option for Linux even pre-install. That took me a day or two to figure out (with the help of these great forums and plenty of other frustrated QuadGT motherboard owners on various forums) so there were a few missed installs that hang the machine. I was thinking/hoping that whatever failures would've been erased by the later successful installs and wouldn't at least affect the boot sectors. Perhaps I was wrong and this is all due to those failures.

But basically I did it "Windows first, Ubuntu second". All drives connected I just put in Windows CD first and installed it (didnt touch hard drive 2, left it unformatted). After this I booted to Ubuntu and used Gparted in the installer to first resize Windows down to a more reasonable size, created the other partitions on that disk, formatted the second disk as well, and installed. And it worked fine. I didn't specify the location of Grub manually at any point, I think, I thought it would just *ummm* be fine wherever it decided to go and it's better if I not try to be cute and touch it. Frankly, I wasn't expecting problems and was just clicking through defaults because I've done similar "install linux after Windows" type things before with no problems.

Doesn't it look like grub and Windows boot / mbr / whatever I should call it are both on the first partition here? Or am I interpreting this wrong? Is this the problem that they don't like sharing a partition and should I somehow try to move grub onto another partition, set that as the first boot partition, and then restore the Windows mbr so that the grub "chainloader" setting would know how to start that? Or am I making no sense at all anymore :)

Edit: actually, I guess it doesn't look like they're both on first partition since "fdisk -l" says sda2 is the boot disk so I guess they seem to be on different partitions already.

---

### Post by Pumalite on 2008-01-18
Use Gparted and changr the boot flag from sda2 to sda1

---

### Post by wieman01 on 2008-01-18
Hello, 

According to "fdisk -l" I conclude the following:

A. Windows resides on "/dev/sda1" -> [COLOR="Blue"]root (hd0,0)[/COLOR]
B. Linux boot partition is on "/dev/sda2" -> [COLOR="Blue"]root (hd0,1)[/COLOR]

So please make a safety copy of your GRUB configuration file first:
> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
The change the relevant section so that it reads (you can restore the original file anytime you like):
> ## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
[COLOR="Blue"]root            (hd0,1)[/COLOR]
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=9f3c0793-db7e-4293-ae29-40ea5912ffc0 ro quiet splash irqpoll
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
[COLOR="Blue"]root            (hd0,1)[/COLOR]
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=9f3c0793-db7e-4293-ae29-40ea5912ffc0 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
[COLOR="Blue"]root            (hd0,1)[/COLOR]
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

title           Microsoft Windows XP
[COLOR="Blue"]root (hd0,0)[/COLOR]
[COLOR="Red"]savedefault[/COLOR]
makeactive
chainloader +1

That should do. Please restart the PC & let me know how you go. I don't think we have a 'mount' problem here as you have suggested above.

---

### Post by sandysandy on 2008-01-18
> **BatPenguin said:**
> I've been trying to get dual-booting working with Ubuntu and Windows XP Home. My Ubuntu machine works great but the problem is that so far I have been unable to boot into Windows without restoring its MBR (fixboot / fixmbr commands from recovery CD) first. And when I do that, GRUB of course gets erased and wll have to be restored for me to be able to boot back into Ubuntu. Not very handly.

I've seen instructions on restoring GRUB / editing menu.lst but haven't been succesful in getting the machine to work.

Here's all the important data as far as I can tell:

the output of "sudo fdisk -l":

$ sudo fdisk -l
```

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24e924e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       18237   146488671    7  HPFS/NTFS
/dev/sda2   *       18238       30395    97659135   83  Linux
/dev/sda3           30396       32827    19535040   82  Linux swap / Solaris
/dev/sda4           32828       91201   468889155   83  Linux

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003e6dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux

```

My /etc/fstab:

$ cat /etc/fstab ```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=9f3c0793-db7e-4293-ae29-40ea5912ffc0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=22b7addf-ff3f-4c71-9028-0582775ac861 /home           ext3    defaults        0       2
# /dev/sdb1
UUID=17e8be2a-5bf0-4eb2-9753-033b10b5b308 /myth           xfs     defaults        0       2
# /dev/sda1
UUID=5A98C0F198C0CCA7 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=8b9375f1-a449-4c7b-b9fe-eab2f5c1e245 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

and finally  /boot/grub/menu.lst in all its glory:

```
$ cat /boot/grub/menu.lst
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
default         2

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
# kopt=root=UUID=9f3c0793-db7e-4293-ae29-40ea5912ffc0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
# defoptions=quiet splash irqpoll

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

title           Ubuntu 7.10, kernel 2.6.22-14-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-386 root=UUID=9f3c0793-db7e-4293-ae29-40ea5912ffc0 ro quiet splash irqpoll
initrd          /boot/initrd.img-2.6.22-14-386
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-386 root=UUID=9f3c0793-db7e-4293-ae29-40ea5912ffc0 ro single
initrd          /boot/initrd.img-2.6.22-14-386

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=9f3c0793-db7e-4293-ae29-40ea5912ffc0 ro quiet splash irqpoll
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=9f3c0793-db7e-4293-ae29-40ea5912ffc0 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
rootnoverify            (hd0,0)
makeactive
chainloader     +1

# XP: 0,1
title           Microsoft Windows XP 0,1
rootnoverify            (hd0,1)
makeactive
chainloader     +1

# XP: root, not noverify (0,0)
title           Microsoft Windows XP root 0,0
root                    (hd0,0)
makeactive
chainloader     +1

# XP: root, not noverify (0,1)
title           Microsoft Wndows XP root 0,1
root                    (hd0,1)
makeactive
chainloader     +1
```


As you can see, I've tried a bunch of different setups for Windows XP at the end there but none of those work. I was thinking the "rootnoverify" option might be a problem so I tried it with just "root", no go. After some more surfing today, it looks like rootnoverify is correct for NTFS but anyhow, I've tried all of the boot options listed above.

This is the normal error message i get when trying to boot Windows: (just black screen with a few lines of text):


```

Windows could not start because the following file is missing or corruput:

\<windowsroot>\system32\ntoskrnl.exe

```

...as far as I can tell, that's Windows error message nonsense, the problem seems to be that the Windows drive is not being mounted or it looks at the wrong partition for Windows files etc...I guess? If I fix it with the recovery CD, everything works great but when GRUB is restored, it breaks again.

All suggestions are welcome and I'd be happy to give you more information if I omitted something. Thanks!

after u have fixed windows MBR (using either FIXMBR command or SGD), i assume u r not getting grub with ubuntu option so u may consider booting using ubuntu live cd, so that the entries of ubuntu can be corrected in the menu.lst file.

use code [COLOR="Blue"]sudo fdisk -lu [/COLOR]in terminal and see output to see which partition is windows and which is ubuntu. (NTFS partition will be windows and ext3 will be ubuntu)

Then mount partition using code
[COLOR="Blue"]sudo mount -t ext3 /dev/sda2 /mnt/ubuntu[/COLOR]

Then use following code
[COLOR="Blue"]
gksudo gedit /boot/grub/menu.lst[/COLOR]


this will open ur menu.lst file.

in menu.lst file check that the ubuntu partition number is set correctly. ( also windows partition entry is set correctly)

eg
title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,1) [COLOR="Red"]<---CHECK THIS[/COLOR]
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=6fe8f4e4-bb66-4c5b-b33c-7a24d4f1cdd8 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

save the menu.lst file.

[COLOR="MediumTurquoise"]boot using super grub disk[/COLOR]. go to linux mbr section and use [COLOR="Blue"]FIX MBR option[/COLOR].

[COLOR="Blue"]reboot.[/COLOR]

grub should come back with both windows and ubuntu option.

do let me know if it works out.

regards

---

### Post by BatPenguin on 2008-01-18
> <That should do. Please restart the PC & let me know how you go. I don't think we have a 'mount' problem here as you have suggested above.

Unfortunately that didn't work. I used what you suggested and had the same problems.

Should I try what sandysandy is suggesting? Thanks for the suggestion Sandysandy, but could you please give some reasoning on why do this? This is a well-behaving Ubuntu system and I would really not like to do any partion-changing without knowing exactly whats going to happen. Windows is completely secondary so I'd only like to fix it if it's compltely safe :)

Edit: Actually my comment was meant to be in response to Pumalite's comment as well...both changing boot flag and using super grub to fix this sound like they might work, but is there a reason to believe supergrub disk would fix this any better than the normal "boot with live ubuntu CD and drop to console to fix grub" method that I've been using? I could give this a try but just seems like it'll do the same as what I've been doing before, will it not?

---

### Post by sandysandy on 2008-01-19
> **BatPenguin said:**
> Unfortunately that didn't work. I used what you suggested and had the same problems.

Should I try what sandysandy is suggesting? Thanks for the suggestion Sandysandy, but could you please give some reasoning on why do this? This is a well-behaving Ubuntu system and I would really not like to do any partion-changing without knowing exactly whats going to happen. Windows is completely secondary so I'd only like to fix it if it's compltely safe :)

Edit: Actually my comment was meant to be in response to Pumalite's comment as well...both changing boot flag and using super grub to fix this sound like they might work, but is there a reason to believe supergrub disk would fix this any better than the normal "boot with live ubuntu CD and drop to console to fix grub" method that I've been using? I could give this a try but just seems like it'll do the same as what I've been doing before, will it not?

I have tried Super Grub Disk for fixing the MBR and have been happy with the results. it has various options like - fix MBR of windows, or linux. When u fix MBR of windows, windows should boot ok but u may not find entries for linux. When u choose fix MBR of linux u will be shown the various linux OS installed on your system and u have to choose one of them. Now, depending on what u have chosen, on rebooting, the system (IPL) will look to the menu.lst file of that particular linux OS and show u the options of different OS (which are in the menu.lst file) for selecting which to boot. it is therefore important that the partition entries for different OS eg root (hd0,1) are ok in the menu.lst file. in any case take a backup of your previous menu.lst file as suggested by wieman01.

regards

---

### Post by BatPenguin on 2008-01-21
> **sandysandy said:**
> I have tried Super Grub Disk for fixing the MBR and have been happy with the results.

OK, thansks for the explanation: I'll give this a try (don't have time tonight, but hopefully tomorrow). So just to clarify, I'll be doing this:

- boot with SGD to fix Windows boot
- boot with Ubuntu Live CD and check that menu.lst is fine, if not, edit
- boot with SGD and fix Linux boot

Please give me a kick if that's not what you meant :). I appreciate all the help, I'll post with results once I get the chance to try this.

---

### Post by sandysandy on 2008-01-22
> **BatPenguin said:**
> OK, thansks for the explanation: I'll give this a try (don't have time tonight, but hopefully tomorrow). So just to clarify, I'll be doing this:

- boot with SGD to fix Windows boot
- boot with Ubuntu Live CD and check that menu.lst is fine, if not, edit
- boot with SGD and fix Linux boot

Please give me a kick if that's not what you meant :). I appreciate all the help, I'll post with results once I get the chance to try this.

steps 2 and 3 should be fine.

regards

---

### Post by JonUK76 on 2008-01-22
Hi, I had exactly the same issue on my install. Grub and even Supergrub would not boot Windows regardless of what options I put in. I *could* boot Windows using a utility called Smartboot (comes with the Ultimate Boot CD) but that seemed a temporary solution. I was given this solution by someone on another forum and it works (hope he does not mind me re-posting here)

It involves copying Grub onto the Windows partition, and using the Windows bootloader to either start windows or to load Grub.

> Ubuntu is supposed to detect a Windows install and sort that out for you, I guess it's not perfect yet However you can sucessfully boot into Ubuntu?

If so, do you have write access to the drive containing your windows install?

I'm going to assume the answer to all the above is yes, and that your windows install is mounted at /mnt/c which should mean you have a file called /mnt/c/boot.ini. This file controls the Windows bootloader.

do the following as root:

dd if=/dev/hda of=/mnt/c/bootsect.lin bs=512 count=1

This will create a file called bootsect.lin on that drive. In that file is a copy of the grub bootloader that was installed by Ubuntu. Note: if you have SATA then you may need to use /dev/sda instead of hda.

Note: If you do not have write access to that C: drive then you will need to write it to a floppy disk or USB flash memory and then copy it over once you have Windows working again.

Now, reboot and insert your Windows XP CD, boot off it and when prompted, go into the Recovery Console. Issue the following commands:
FIXBOOT
FIXMBR
EXIT

Remove the XP CD and reboot again. Windows should load normally.

Do Start \ Run \ CMD.EXE
CD \
ATTRIB -R -S -H boot.ini
NOTEPAD boot.ini
at the end of the file add the line:
C:\BOOTSECT.LIN="Ubuntu Linux"
Save it and reboot

You should now get the XP bootloader when you boot. If you pick the Ubuntu option, the XP bootloader will load the Grub bootloader from which you can load Ubuntu. You may want to configure Grub to load Ubuntu without any further prompting.

There is a way to have Grub load the XP bootloader instead, but I can't remember how to do that.

Note that on mine, the Windows C drive was not mounted at /mnt/c but something like /media/disk

Hope this helps

---

### Post by BatPenguin on 2008-02-03
OK, been a while but I finally got around to trying the SuperGrub disk. It was a mixed success:

It's able to fix both Windows and Linux boots, similar to (but much faster!)  than running Windows rescue disk (to fix Windows MBR) or Live CD to fix Grub. Very nice. But still the same result: if Windows MBR is fixed, Grub is gone for good, if Grub is restored (made sure all the settings were the same as mentioned above, tried this by first fixing Windows MBR and not doing that), then Windows will not start through it, same error as before.

However, I did find a solution that's good enough: the SGRUB disk has the option of "boot windows" which amazingly enough worked just fine without restoring MBR first. So actually, this is good enough for me. I've decided to give up on messing with the boot sectors and just use the CD to boot when I need Windows. Realistically, I never need Windows unless I pick up some brand new game (didn't need to boot into it once between last message and this, it's truly once a month unless some new game lures me into buying it), so this is just fine for me...when I need Windows, I put in the CD and boot to Windows through that. Not the most convenient solution but it'll do. The option of getting Windows bootloader to load GRUB might work here, I suppose, but I rather not do that.

Thanks everybody, all the advice was very helpful and my Windows is "useable enough" again :)

---

