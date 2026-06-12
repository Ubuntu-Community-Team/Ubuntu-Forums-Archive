---
title: "dual boot xp and ubuntu 7.1"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by gorlando on 2007-11-30
I've installed 7.1 using the defaults selected for partitioning my one drive.  

ubuntu comes up fine but i can't get my windows xp to boot up.  i hope the installation didn't blow windows away?

i've tried several recommended changes to menu.lst, with and without the map commands but since i'm not sure if windows is there and if so where it is, i'm not sure what to do.  help please.

---

### Post by Pumalite on 2007-11-30
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by jken146 on 2007-11-30
In a terminal, type ```
sudo fdisk -l
``` to show which partitions you have.

edit:  I was sooo slow there!

---

### Post by gorlando on 2007-11-30
the below contains the windows code at the end which is one of my attempts to fix the problem.  original code did not have windows portion of course.
thanks


Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeb275b50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   306439874   153219906   83  Linux
/dev/sda2       306439875   312496379     3028252+   5  Extended
/dev/sda5       306439938   312496379     3028221   82  Linux swap / Solaris


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
# kopt=root=UUID=f4dbf0b3-ca3d-44af-b6b2-4e284a39c606 ro

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
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f4dbf0b3-ca3d-44af-b6b2-4e284a39c606 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f4dbf0b3-ca3d-44af-b6b2-4e284a39c606 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

title           Windows XP
root            (hd0,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Pumalite on 2007-11-30
According to your fdisk, you have only one drive and there is no Windows in it.

---

### Post by Cariboo1938 on 2007-11-30
I think you could find some help  [HERE]("http://users.bigpond.net.au/hermanzone/")
I attached a file from my archive, showing what I did quite a time ago when I made a boot floppy for my system.

EDIT: I was probably too slow here too!!!
Anyway, Good Luck

---

### Post by gorlando on 2007-11-30
> **Pumalite said:**
> According to your fdisk, you have only one drive and there is no Windows in it.

i'm surprised that the ubuntu installation overwrote windows without mentioning this somewhat important fact to me.  i suppose i didn't take enough time to understand the installation options.    all my files are gone too and unaccessible?

---

### Post by rsambuca on 2007-11-30
You may be able to save some of the files that were there.  The files that weren't overwritten are still there, but the filesystem doesn't know where anything is located.  You will have to try some disk file recovery software to save them.  Do not use your drive, as any use will cause further data loss.

---

### Post by Pumalite on 2007-11-30
You can go to a Hard Drive Recovery Shop, but is VERY expensive.

---

### Post by gorlando on 2007-12-02
thank you all so much for your help.  i only lost about a thousand home videos.  geez, what an idiot.  i think i got a little excited and accepted the default without thinking it through.  

i love ubuntu/linux.

i had tried mandriva and it wasn't nearly as easy.

i'm installing another copy of ubuntu on a friends machine and it's going fine so far.

QUESTION,  if i had wanted to keep my windows version 
should i have selected the "install in the largest continuous free space" option?

i think it's the third option on screen during the 7.1 install, right before the manual option.

thanks

---

### Post by Pumalite on 2007-12-02
For control is better to use Manual.

---

