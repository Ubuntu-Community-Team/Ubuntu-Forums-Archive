---
title: "Dual booting with vista and ubuntu 8.04"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by zanyspydude on 2008-05-14
I'm booting with vista and ubuntu.  Grub shows both but when i try to load vista, it says "loading" and then reboots.  Ubuntu boots fine.


I used vista's console to fix the mbr and boot (
```
bootrec.exe /FixBoot
``` and ```
bootrec.exe /FixMbr
```
) and then restarted.  Vista loaded fine, but there was no grub.

I then used the live cd to restore grub using:
```

sudo grub
find /boot/grub/stage1
root (hd0,4)
setup (hd0)
quit

```

Now vista doesn't work again but ubuntu is fine.

Here are some files you may want.


menu.lst:

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
# kopt=root=UUID=0bdb069b-4b42-463c-92d3-89d4f1b256cf ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0bdb069b-4b42-463c-92d3-89d4f1b256cf ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0bdb069b-4b42-463c-92d3-89d4f1b256cf ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=0bdb069b-4b42-463c-92d3-89d4f1b256cf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=4dd76bf5-db5d-48f4-b807-49a4d142db57 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

any thoughts?

---

### Post by zanyspydude on 2008-05-14
i installed windows first and resized the partition after i'd been using it for a while if that makes any difference.

---

### Post by Pumalite on 2008-05-14
With Vista; you have to allocate free space for Ubuntu first. You cannot partition with the Ubuntu CD. Did you do it that way?

---

### Post by fmartinez on 2008-05-14
> **Pumalite said:**
> With Vista; you have to allocate free space for Ubuntu first. You cannot partition with the Ubuntu CD. Did you do it that way?

I thought that the Ubuntu install allows you resize an existing partition and use that to intsall Ubuntu on? 

hda1: Vista
after installer: 
hda1: Vista / Ubuntu     
Ubuntu's install will allow you choose how much space to allocate for Ubuntu if the scenario is true. 
Also you might want to post the output of: 
sudo fdisk -l
The portion in your menu.lst file that is used to load Vista should point a valid NTFS partition. You can get that information from the output of the above command.

---

### Post by Pumalite on 2008-05-14
Wrong. You can do that with XP, but not with Vista.

---

### Post by zanyspydude on 2008-05-14
> **Pumalite said:**
> Wrong. You can do that with XP, but not with Vista.

That was what i selected and it seemed to work fine.  Vista is working fine when i repair the boot record.

Here is my fdisk -l

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35663566

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28189   226424805    7  HPFS/NTFS
/dev/sda2           35089       38914    30718976    6  FAT16
/dev/sda3           28190       35088    55416217+   5  Extended
/dev/sda5           28190       34801    53110858+  83  Linux
/dev/sda6           34802       35088     2305296   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by zanyspydude on 2008-05-14
> **Pumalite said:**
> With Vista; you have to allocate free space for Ubuntu first. You cannot partition with the Ubuntu CD. Did you do it that way?

yes.  I was running vista.  I popped in the livecd, resized vista, and installed ubuntu

---

### Post by Pumalite on 2008-05-14
Well if you used the Live CD to partition and it works: I eat my words and is new to me.

---

### Post by zanyspydude on 2008-05-14
> **Pumalite said:**
> Well if you used the Live CD to partition and it works: I eat my words and is new to me.

yeah, but it doesn't work perfectly :(  Any idea why grub can't load vista in my case? 

I'd rather not reinstall vista

---

### Post by Pumalite on 2008-05-14
The reason is as I stated it.

---

### Post by fmartinez on 2008-05-14
> **Pumalite said:**
> Wrong. You can do that with XP, but not with Vista.

Hmmm. I have Vista on both a laptop (Toshiba Satelite) and a Desktop (HP Pavilion Elite) and this has worked for me without a hitch!

Vista... Also comes with it's own partitioner if all else fails.

---

### Post by fmartinez on 2008-05-14
When you say "loading". What do you mean? 
When it's loading Vista and you get the green process bar with the micrsoft logo?
or is right after you choose the Vista option in grub?

---

### Post by zanyspydude on 2008-05-15
> **fmartinez said:**
> When you say "loading". What do you mean? 
When it's loading Vista and you get the green process bar with the micrsoft logo?
or is right after you choose the Vista option in grub?

it's right after i choose the vista option in grub.  It's the same textual "loading" that i get when i select ubuntu.

---

### Post by zanyspydude on 2008-05-15
any ideas?

---

### Post by meierfra. on 2008-05-16
Try

title		Windows Vista/Longhorn (loader)
root[COLOR="Red"]noverify[/COLOR]		(hd0,0)
savedefault
makeactive
chainloader	+1

if that does not work you might also try

title		Windows Vista/Longhorn (loader)
root[COLOR="Red"]noverify		(hd0,1)[/COLOR]
savedefault
makeactive
chainloader	+1

And if none of this worked get EasyBCD:
[URL="http://neosmart.net/dl.php?id=1"]
http://neosmart.net/dl.php?id=1[/URL]

(EasyBCD is a nice bootloader for Vista)

---

### Post by zanyspydude on 2008-05-16
> **meierfra. said:**
> Try

title		Windows Vista/Longhorn (loader)
root[COLOR="Red"]noverify[/COLOR]		(hd0,0)
savedefault
makeactive
chainloader	+1

if that does not work you might also try

title		Windows Vista/Longhorn (loader)
root[COLOR="Red"]noverify		(hd0,1)[/COLOR]
savedefault
makeactive
chainloader	+1

And if none of this worked get EasyBCD:
[URL="http://neosmart.net/dl.php?id=1"]
http://neosmart.net/dl.php?id=1[/URL]

(EasyBCD is a nice bootloader for Vista)

trying it out right now.  THanks for the advice!


update:
```
title		Windows Vista/Longhorn (loader)
root[COLOR="Red"]noverify[/COLOR]		(hd0,0)
savedefault
makeactive
chainloader	+1

```
has the same behavior as before, but 

```
title		Windows Vista/Longhorn (loader)
root[COLOR="Red"]noverify		(hd0,1)[/COLOR]
savedefault
makeactive
chainloader	+1

```

gives me "Error 13: invalid or unsupported executable format"

trying bcd now.

---

