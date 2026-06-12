---
title: "[SOLVED] Cant find xp in Grub"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by carl_erik on 2008-08-22
Hi!
Ive got this problem. Im new to ubuntu and Linux, and from Norway, so this makes it a bit difficault to explain but i will try. Ive used XP on my computer in 3 years. So some days ago i figured out i should try Ubuntu. And when i rebooted my computer it couldnt find the Hal.dll-file. Googled it and found out it probably had something with Boot.ini to do. So i thougt i could try Grub. And well it works fine, only it cant find XP, well not at first. First I can choose to go to Grub 2, Linux 1, Linux 2 or Windows XP.No mather what i choose i go to grub 2. And in Grub i can only see two versions of linux and one memorycheck or something. But no XP, what can i do?

Ive been googling a lot and here are the files i maybe think you will find interesting: Menu.lst,fdisk -l and one screenshot at the end.

**/boot/grub/menu.lst**

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
default         0

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
# kopt=root=UUID=16fea2e9-d5ae-45b6-a67d-ea00a2721599 ro

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
##      altoptions=(single-user) single
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

title		Chainload into GRUB 2
root		(hd0,2)
kernel		/boot/grub/core.img
savedefault

title		Debian GNU/Linux, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=16fea2e9-d5ae-45b6-a67d-ea00a2721599 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault

title		Debian GNU/Linux, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=16fea2e9-d5ae-45b6-a67d-ea00a2721599 ro single
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault

title		Debian GNU/Linux, kernel memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

**fdisk -l**
```


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09e609e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        4462    35832982+   5  Extended
/dev/sda2   *        4463       28684   194563215    7  HPFS/NTFS
/dev/sda3           28685       30323    13165267+  83  Linux
/dev/sda4           30324       30401      626535   82  Linux swap / Solaris
/dev/sda5               2        4462    35832951    7  HPFS/NTFS



```

And at the end you can see my screenshot. To explain it. My C: is my private files disk. D: is the windows files disk. My boot-file is in C: with my private files. I dont know if this little information helps, but i thought it maybe will:)
Have been googling and tried many thing, but nothing has worked.

Hope on help:)

---

### Post by sandysandy on 2008-08-22
does sda5 or sda2 contain ur windows. sda2 has the boot flag and menu.lst has reference to it.

regards

---

### Post by carl_erik on 2008-08-22
> **sandysandy said:**
> does sda5 or sda2 contain ur windows. sda2 has the boot flag and menu.lst has reference to it.

regards

sda5 contains windows and windows files, but sda2 has the boot-file and all my private files.

---

### Post by sandysandy on 2008-08-22
have u tried super grub disk.

download super grub disk (SGD) from following link and burn as iso image

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

see this link also.

[http://users.bigpond.net.au/hermanzo...bdiskpage.html](http://users.bigpond.net.au/hermanzo...bdiskpage.html)

pop SGD into Cd drive and reboot computer. it will boot into SGD, use the help option. it will guide u step by step.

see if u can boot into XP from SGD


we can then use it further.

regards

---

### Post by manishtech on 2008-08-22
In menu.lst I can see the entry for Windows Vista. Now is it showing in the GRUB listing?

If its showing, what do you get if you select it?

---

### Post by carl_erik on 2008-08-22
> **manishtech said:**
> In menu.lst I can see the entry for Windows Vista. Now is it showing in the GRUB listing?

If its showing, what do you get if you select it?

Well...first of all i hope you see Windows xp:)
Second:
Before i go into Grub2, i can choose between the systems in the menu.lst-file. But if i there choose xp i login or load grub2, there, i cant choose xp. Only the two versions of linux and a memory check.

---

### Post by manishtech on 2008-08-22
> first of all i hope you see Windows xp
Sorry! Typed by mistake, had just answered a question in previous post about Vista! :)

Now what I see it that GRUB2 is being chainloaded.

Now when you are in GRUB 2, press 'c' and you would come to **grub>** prompt
Now here give us the output of the command
**find /boot/grub/stage1**
and
**find /boot/grub/stage2**

Now in this grub> shell, type the following lines one after the another and tell what happens
**root (hd0,1)**
**savedefault**
**makeactive**
**chainloader +1**
**boot**

---

### Post by carl_erik on 2008-09-13
Sorry guys. I gave up, i copied all my files to an external harddisk, and formated my computer. I needed it anyway:)

---

### Post by Palypup on 2008-09-13
After 3 tries with wubi, decided on a permanent install and ended up with the same problem (evidently grub didn't recognize usb keyboard). Just did an uninstall with wubi but it was permanent in the regular install so did an fdisk /mbr and got windows back but no option for the Ubuntu now installed. One solution to above problem.

---

