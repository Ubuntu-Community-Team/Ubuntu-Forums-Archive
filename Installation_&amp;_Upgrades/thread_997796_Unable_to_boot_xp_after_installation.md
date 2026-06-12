---
title: "Unable to boot xp after installation"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by X_Splinter on 2008-11-30
Hi there.

I had a dual boot xp\vista with Vista as bootloader

Now I installed Ubuntu 8.10 in the Vista partition formatting Vista.

The problem is now the Grub detects Ubuntu of course and Windows Vista (I dont know why because ubuntu deleted it and so it doesn't run) and no Xp.

Inside Ubuntu i can see Xp partition which is intact.

Can someone please tell how fix it?
I am new in Ubuntu, i dont know how config Grub.

I want to be able to run Xp and delete any entry of Vista.

Thanks in advance

---

### Post by Pumalite on 2008-11-30
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by X_Splinter on 2008-11-30
> **Pumalite said:**
> Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

sudo fdisk -lu show this:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe9c263ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20466809    10233373+  12  Compaq diagnostics
/dev/sda2   *    20467712   166793215    73162752    7  HPFS/NTFS
/dev/sda3       166802895   195382529    14289817+  83  Linux
/dev/sda4       195382530   312576704    58597087+   5  Extended
/dev/sda5       195382593   203206184     3911796   82  Linux swap / Solaris
/dev/sda6       203206248   312576704    54685228+  83  Linux

```

The cat /boot/grub/menu.lst show this:
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
# kopt=root=UUID=51e8375b-cd1e-424d-a66c-52b8411ce6f5 ro locale=pt_PT

## default grub root device
## e.g. groot=(hd0,0)
# groot=51e8375b-cd1e-424d-a66c-52b8411ce6f5

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		51e8375b-cd1e-424d-a66c-52b8411ce6f5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=51e8375b-cd1e-424d-a66c-52b8411ce6f5 ro locale=pt_PT quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		51e8375b-cd1e-424d-a66c-52b8411ce6f5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=51e8375b-cd1e-424d-a66c-52b8411ce6f5 ro locale=pt_PT  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		51e8375b-cd1e-424d-a66c-52b8411ce6f5
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by X_Splinter on 2008-11-30
It looks like the second Vista boot option goes to my previous dualboot screen (xp\Vista) that way i could boot xp again.

Is there any way i can boot Xp from Grub???

Plus why do i still have Vista boot files?

---

### Post by caljohnsmith on 2008-11-30
> **X_Splinter said:**
> It looks like the second Vista boot option goes to my previous dualboot screen (xp\Vista) that way i could boot xp again.

Is there any way i can boot Xp from Grub???

Plus why do i still have Vista boot files?
You still get Vista's boot menu because Vista normally puts its boot files in the XP partition when you install Vista after XP. To fix it, most likely all you need to do is boot your Windows XP Install CD, go to the "recovery console", and run:
```
fixboot

```
What that does is fix the XP partition boot sector so it boots "ntldr" (Windows XP) instead of "bootmgr" (Windows Vista). If that works OK, you can also remove the following Vista directory and boot file from your XP partition:
```
C:\Boot
C:\bootmgr
```
Let me know how that goes. :)

---

### Post by X_Splinter on 2008-11-30
> **caljohnsmith said:**
> You still get Vista's boot menu because Vista normally puts its boot files in the XP partition when you install Vista after XP. To fix it, most likely all you need to do is boot your Windows XP Install CD, go to the "recovery console", and run:
```
fixboot

```
What that does is fix the XP partition boot sector so it boots "ntldr" (Windows XP) instead of "bootmgr" (Windows Vista). If that works OK, you can also remove the following Vista directory and boot file from your XP partition:
```
C:\Boot
C:\bootmgr
```
Let me know how that goes. :)

Thanks but before acting i want to ask something

XP may/probably overwrite the Grub boot-loader right? How can i backup my grub so i may easily restore it with the live cd?

---

### Post by caljohnsmith on 2008-11-30
> **X_Splinter said:**
> Thanks but before acting i want to ask something

XP may/probably overwrite the Grub boot-loader right? How can i backup my grub so i may easily restore it with the live cd?
Unless you reinstall XP or run "fixmbr" from the XP CD recovery console, your Grub in the MBR (Master Boot Record) should be safe from harm. The "fixboot" command only fixes XP's partition boot sector; it doesn't touch the MBR where Grub is. :)

---

### Post by X_Splinter on 2008-11-30
> **caljohnsmith said:**
> Unless you reinstall XP or run "fixmbr" from the XP CD recovery console, your Grub in the MBR (Master Boot Record) should be safe from harm. The "fixboot" command only fixes XP's partition boot sector; it doesn't touch the MBR where Grub is. :)

Ok Thanks... i am gonna try it :guitar:

---

