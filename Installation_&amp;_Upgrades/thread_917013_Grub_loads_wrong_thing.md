---
title: "Grub loads wrong thing"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by EricDallal on 2008-09-11
I recently installed Ubuntu on my new computer (which worked pretty much flawlessly, except for flash issues, despite concern about the 64 bit Ubuntu). However, when I try to get into Windows, it instead sends me to the windows diagnostics menu (the same menu that you get when trying to load from the backup DVD). Since this was the last way that I had loaded the computer, it is possible that, when Ubuntu installed the grub, it believed that this was the location of the operating system. Is there any way to fix this (short of starting over)?

---

### Post by mikewhatever on 2008-09-11
Can you post the outputs of the following two commands:
> sudo fdisk -l
cat /boot/grub/menu.lst

---

### Post by EricDallal on 2008-09-11
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcedf7477

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             193        6718    52420095    7  HPFS/NTFS
/dev/sda3   *       29499       30402     7254016   17  Hidden HPFS/NTFS
/dev/sda4            6719       29498   182980350    5  Extended
/dev/sda5            6719       27017   163051686    b  W95 FAT32
/dev/sda6           27018       28976    15735636   83  Linux
/dev/sda7           28977       29498     4192933+  82  Linux swap / Solaris

Partition table entries are not in disk order



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
# kopt=root=UUID=f0a0e163-060f-49f5-8045-df9ca03c5d8e ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=f0a0e163-060f-49f5-8045-df9ca03c5d8e ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=f0a0e163-060f-49f5-8045-df9ca03c5d8e ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title           Windows Vista/Longhorn (loader)
root            (hd0,2)
savedefault
makeactive
chainloader     +1

---

### Post by mikewhatever on 2008-09-11
Have you tried both Vista entries in Grub's menu? It looks like Vista is on sda3, while the sda2 is a recovery partition. I am not at all familiar with Vista, but it looks like the first Vista entry should load the recovery program, and the second Vista proper.

---

### Post by EricDallal on 2008-09-11
I tried each entry twice and neither worked.

---

### Post by caljohnsmith on 2008-09-11
> **EricDallal said:**
> ```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcedf7477

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             193        6718    52420095    7  HPFS/NTFS
[COLOR="Red"]/dev/sda3   *       29499       30402     7254016   17  Hidden HPFS/NTFS[/COLOR]
/dev/sda4            6719       29498   182980350    5  Extended
/dev/sda5            6719       27017   163051686    b  W95 FAT32
/dev/sda6           27018       28976    15735636   83  Linux
/dev/sda7           28977       29498     4192933+  82  Linux swap / Solaris
```

That's interesting that fdisk reports sda3 as "hidden" NTFS. Do you know what is on that partition? If you set a partition's "hidden" bit on, then you won't normally have access to it until you unhide it. But a partition with its hidden bit set on normally shows up as "amoeba" file system with fdisk (I know that sounds crazy but it's true). So I don't know if that partition is really hidden in the sense its partition hidden bit is on, but you can "unhide" it to make sure you have access to it:
```
sudo grub
grub> unhide (hd0,2)
grub> quit
```
Doing the above commands certainly won't hurt, because you want to make sure you have access to that partition, whatever is on it. So do you know for sure which partition has your Windows?

---

### Post by EricDallal on 2008-09-11
sda2 has windows on it. It is the only one that is even close to the right size.

---

### Post by meierfra. on 2008-09-11
> But a partition with its hidden bit set on normally shows up as "amoeba" file system with fdisk 

Hiding a partition  just adds "10" to the partition type. So if you hide an NTFS partition (which has type 7) you get a a partition of type "17", which fdisk correctly identifies as  a hidden NTFS partition. 
If you hide it again again, you get "27" which is an unknown type.

If you hide a linux partition (type 83) you  get a partition of type "93" which is the type associated to the "amoeba" file system.

---

### Post by EricDallal on 2008-09-11
It appears that the problem was not with the grub but with windows all along. I fixed the problem by using the windows diagnostic tools to fix boot problems. I didn't want to do it before since I believed that it would overwrite the grub in the mbr. Once I researched how to reinstall the grub, I decided to risk it and it worked without any problems. Thanks to all who tried to help me.

P.S.: Sorry for blaming linux when windows was the problem. I have never done that before.

---

### Post by caljohnsmith on 2008-09-11
> **meierfra. said:**
> Hiding a partition  just adds "10" to the partition type. So if you hide an NTFS partition (which has type 7) you get a a partition of type "17", which fdisk correctly identifies as  a hidden NTFS partition. 
If you hide it again again, you get "27" which is an unknown type.

If you hide a linux partition (type 83) you  get a partition of type "93" which is the type associated to the "amoeba" file system.
Thanks for clarifying that, meierfra, it makes sense now why Linux becomes "amoeba" after hiding it. So would that mean "hiding" a partition is basically just changing its file system type, so that it then seems to be unreadable?

---

### Post by meierfra. on 2008-09-11
> So would that mean "hiding" a partition is basically just changing its file system type, so that it then seems to be unreadable?

Yes.

---

