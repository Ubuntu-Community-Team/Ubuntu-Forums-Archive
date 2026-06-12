---
title: "Kernels 2.6.38-10 no go with grub: Error 16 &amp; Error 13"
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by AcidumIrae on 2011-07-18
Hello,

suddenly after upgrade :confused:

2.6.38-10-generic-pae ===> Error 16: Incosistent filesystem structure
2.6.38-10-generic-pae (recovery mode) ===> Error 13: Invalid or unsupported executable format
2.6.38-10-generic ===> Error 13: Invalid or unsupported executable format
2.6.38-10-generic (recovery mode) ===> No installtion signature
2.6.38-8-generic-pae ===> works just fine...

```
Distributor ID: Ubuntu
Description:    Ubuntu 11.04
Release:        11.04
Codename:       natty
```

I have two HDDs mirrored in NVIDIA host raid with dm_raid45
Here is my /boot/grub/menu.lst
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
# kopt=root=UUID=b08e48b7-1194-49c1-a743-91e7ee90334e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b08e48b7-1194-49c1-a743-91e7ee90334e

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
# defoptions=ipv6.disable=1 acpi=off

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title           Ubuntu 11.04, kernel 2.6.38-10-generic-pae
uuid            b08e48b7-1194-49c1-a743-91e7ee90334e
kernel          /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=b08e48b7-1194-49c1-a743-91e7ee90334e ro ipv6.disable=1 acpi=off crashke
rnel=384M-2G:64M,2G-:128M
initrd          /boot/initrd.img-2.6.38-10-generic-pae
quiet

title           Ubuntu 11.04, kernel 2.6.38-10-generic-pae (recovery mode)
uuid            b08e48b7-1194-49c1-a743-91e7ee90334e
kernel          /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=b08e48b7-1194-49c1-a743-91e7ee90334e ro  crashkernel=384M-2G:64M,2G-:12
8M single
initrd          /boot/initrd.img-2.6.38-10-generic-pae

title           Ubuntu 11.04, kernel 2.6.38-10-generic
uuid            b08e48b7-1194-49c1-a743-91e7ee90334e
kernel          /boot/vmlinuz-2.6.38-10-generic root=UUID=b08e48b7-1194-49c1-a743-91e7ee90334e ro ipv6.disable=1 acpi=off  crashkerne
l=384M-2G:64M,2G-:128M
initrd          /boot/initrd.img-2.6.38-10-generic
quiet

title           Ubuntu 11.04, kernel 2.6.38-10-generic (recovery mode)
uuid            b08e48b7-1194-49c1-a743-91e7ee90334e
kernel          /boot/vmlinuz-2.6.38-10-generic root=UUID=b08e48b7-1194-49c1-a743-91e7ee90334e ro  crashkernel=384M-2G:64M,2G-:128M s
ingle
initrd          /boot/initrd.img-2.6.38-10-generic

title           Ubuntu 11.04, kernel 2.6.38-8-generic-pae
uuid            b08e48b7-1194-49c1-a743-91e7ee90334e
kernel          /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=b08e48b7-1194-49c1-a743-91e7ee90334e ro ipv6.disable=1 acpi=off  crashke
rnel=384M-2G:64M,2G-:128M
initrd          /boot/initrd.img-2.6.38-8-generic-pae
quiet

title           Ubuntu 11.04, kernel 2.6.38-8-generic-pae (recovery mode)
uuid            b08e48b7-1194-49c1-a743-91e7ee90334e
kernel          /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=b08e48b7-1194-49c1-a743-91e7ee90334e ro  crashkernel=384M-2G:64M,2G-:128
M single
initrd          /boot/initrd.img-2.6.38-8-generic-pae

title           Ubuntu 11.04, kernel 2.6.38-8-generic
uuid            b08e48b7-1194-49c1-a743-91e7ee90334e
kernel          /boot/vmlinuz-2.6.38-8-generic root=UUID=b08e48b7-1194-49c1-a743-91e7ee90334e ro ipv6.disable=1 acpi=off  crashkernel
=384M-2G:64M,2G-:128M
initrd          /boot/initrd.img-2.6.38-8-generic
quiet

title           Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid            b08e48b7-1194-49c1-a743-91e7ee90334e
kernel          /boot/vmlinuz-2.6.38-8-generic root=UUID=b08e48b7-1194-49c1-a743-91e7ee90334e ro  crashkernel=384M-2G:64M,2G-:128M single
initrd          /boot/initrd.img-2.6.38-8-generic
title           Ubuntu 11.04, memtest86+
uuid            b08e48b7-1194-49c1-a743-91e7ee90334e
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

b08e48b7-1194-49c1-a743-91e7ee90334e is a link to /dev/dm-2 which is my root partition on nvidia raid

**PS:** At first it did not boot at all dropping out to grub shell, but I managed to boot it with gparted live usb stick and chroot to Ubuntu and re-install grub, but now 2.6.38-8 kernel works and 2.6.38-10 is not :confused:

---

### Post by AcidumIrae on 2011-07-18
Solved. I don't know what was it, here is what I did:

```
sudo apt-get clean
sudo apt-get remove linux-image-2.6.38-10-generic
sudo apt-get remove linux-image-2.6.38-10-generic-pae
sudo apt-get install linux-image-2.6.38-8-generic-pae
sudo apt-get install linux-image-2.6.38-8-generic
sudo update-grub 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-image-2.6.38-10-generic linux-image-2.6.38.10-generic-pae
sudo apt-get install linux-headers-2.6.38-10-generic linux-headers-2.6.38-10-generic-pae

```

---

