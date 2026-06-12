---
title: "Dual Boot Problem"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by trginter on 2008-01-30
So I've got two hard drives, one has Windows XP on it and the other Ubuntu 7.10.  When I boot my computer, I have it set so the Ubuntu HD boots first.  I never get the option to choose either Windows or Ubuntu.  If I unplug the Ubuntu HD and only have the Windows HD in it boots into Windows just fine.  When everything plugged in like normal I can hit ESC and it gives me three options to boot from, all Ubuntu.  One is with Safe Mode and the other is with Memtest.  How do I go about getting it so I can boot from Windows too?

---

### Post by Partyboi2 on 2008-01-30
can you post the output from a terminal (Applications>Accessories>Terminal)
```
fdisk -l
```
```
cat /boot/grub/menu.lst
```

---

### Post by trginter on 2008-01-30
```
tim@desktop:~$ fdisk -l
tim@desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=f7f790ca-2233-4534-9b57-218f6ab99164 ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f7f790ca-2233-4534-9b57-218f6ab99164 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f7f790ca-2233-4534-9b57-218f6ab99164 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
tim@desktop:~$
```

---

### Post by confused57 on 2008-01-30
The entry in this thread might boot your Windows drive, if Windows is on the first partition:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

As Partyboi mentioned you can determine which partition Windows is on with:
```
sudo fdisk -l
```
-l is a small "L"

You can add the Windows entry to the very end of your menu.lst, after the line ###END DEBIAN AUTOMAGIC LIST.

---

### Post by trginter on 2008-01-30
I must of typed it wrong.  Here is the first part.

Bah, now I can't get 1440x900 resolution to work.  I got it working when I installed Linux a few months ago but I can't figure out how to again.  It's going to be a long night...

```
tim@desktop:~$ sudo fdisk -l
[sudo] password for tim:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b0f83a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe84462e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48641   390708801    7  HPFS/NTFS

Disk /dev/sdc: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d040f5c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4499    36138186    7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f2ac6b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       29649   238155561   83  Linux
/dev/sdd2           29650       30401     6040440    5  Extended
/dev/sdd5           29650       30401     6040408+  82  Linux swap / Solaris
tim@desktop:~$ 
tim@desktop:~$ 

```

---

### Post by trginter on 2008-01-31
I just tried adding..

```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

at the end of 

```
gksudo gedit menu.lst
```

and I see the Windows option but when I try and load it it says there's a missing file and I need to reinstall it.  I can run Windows alone no problem, so I don't get why it's telling me that there is a missing file.

```
Windows could not start because the following file is missing or corrupt.

<Windows Root>\system32\ntoskml.exe.

Please Reinstall a copy of the above File.

```

---

### Post by confused57 on 2008-01-31
You could check your device.map to determine how grub recognizes your Windows drive:
```
gedit /boot/grub/device.map
```

Your Windows entry may need to be something like:
```
title              Windows XP
root               (hd2,0)
savedefault
makeactive
map                (hd0) (hd2)
map                (hd2) (hd0)
chainloader        +1
```

or

```
title              Windows XP
root               (hd3,0)
savedefault
makeactive
map                (hd0) (hd3)
map                (hd3) (hd0)
chainloader        +1
```

---

### Post by trginter on 2008-01-31
```
(hd0)	/dev/sda
```

I'll try 2 and if that doesn't work I'll try 3.

With 2, it gave me the following:

```
NTLPR is Missing
```

3 worked great  Boots to Windows no problem.  Thanks for all the help, I really appreciate it.  I'm pretty new to Linux, as well as dual booting.

Now, if you can get me a 1440x900 resolution I would be great.

---

### Post by confused57 on 2008-01-31
What video card are you using and do you have restricted drivers installed?

You could check in your xorg.conf to see what driver & resolutions you have enabled:
```
gedit /etc/X11/xorg.conf
```

---

### Post by trginter on 2008-01-31
I've got a nVidia 7800GTX.  I do have restricted drivers installed.

I tried that last night and deleted everything except for "1440x900" and rebooted and fixed it.

Also got my forward and back buttons on my mouse working too.

Why doesn't Ubuntu support widescreen resolutions and multi-button mice without having to manually change the xorg?

---

