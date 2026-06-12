---
title: "NTDLR missing on linux only install?"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by yellekc on 2007-09-03
I am a little confused here. I have my PC set up with a single 250GB IDE hard drive that used to have windows on it. But I directed the Ubuntu 7.04 installer to automatically partition the whole hard drive for itself. So why would I be getting NT Loader errors? Shouldn't Ubuntu of formated the whole disc including the boot sector?

---

### Post by merlinus on 2007-09-03
You might post results of **sudo fdisk -l** and **cat /boot/grub/menu.lst** entered in a terminal.

-merlin

---

### Post by ddrichardson on 2007-09-03
Did grub get installed on the first partition rather than the MBR?

---

### Post by yellekc on 2007-09-03
> **merlinus said:**
> You might post results of **sudo fdisk -l** and **cat /boot/grub/menu.lst** entered in a terminal.

-merlin

Thanks for the reply.

**fdisk:**

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29654   238195723+  83  Linux
/dev/sda2           29655       30401     6000277+   5  Extended
/dev/sda5           29655       30401     6000246   82  Linux swap / Solaris

[B]
menu.lst:[/B]

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
# kopt=root=UUID=c89abcaf-860f-4a2e-b7d9-dc57c7edb9c1 ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=c89abcaf-860f-4a2e-b7d9-dc57c7edb9c1 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=c89abcaf-860f-4a2e-b7d9-dc57c7edb9c1 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by merlinus on 2007-09-03
Looks good to me.  You might try reinstalling grub, in case it did not get installed to the mbr, as ddrichardson said.

```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```Substitute results from find for (hdx,y) and setup (hdx).  It will most likely be root (hd0,0) and setup (hd0).

-merlin

---

### Post by yellekc on 2007-09-03
> **merlinus said:**
> Looks good to me.  You might try reinstalling grub, in case it did not get installed to the mbr, as ddrichardson said.

```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```Substitute results from find for (hdx,y) and setup (hdx).  It will most likely be root (hd0,0) and setup (hd0).

-merlin

Tried that to no avail. Here's what I did in grub in case it is useful at all:

grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,0)
grub> root (hd0,0)       
root (hd0,0)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

This males no sense to me. Where is this ntldr error coming from? There is nothing in the optical drive either.

---

### Post by merlinus on 2007-09-03
The only things I can think of is maybe the OEM created a hidden restore partition, or there is something in the BIOS that is wanting to boot windows.

-merlin

---

### Post by Pumalite on 2007-09-03
I agree Merlin. They probably should have ran DBan before Gparted and install.

---

### Post by merlinus on 2007-09-03
So DBan will wipe out the mbr as well?  Great stuff!

-merlin

---

### Post by Pumalite on 2007-09-03
The best! Have you tried it? It's like scrubbing your teeth; sparkling clean.

---

### Post by merlinus on 2007-09-03
I downloaded the ,iso, but have not had a need for it yet.  Thanks muchly for the info!

-merlin

---

### Post by merlinus on 2007-09-03
nvm -- double post.

---

### Post by Pumalite on 2007-09-03
Anytime, with pleasure.

---

