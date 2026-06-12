---
title: "Segmentation Fault During Startup Of Ubuntu VM after Upgrade from ESX 3.5 to 4.1 (vSp"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by derrickonline on 2010-12-15
Under ESX 3.5 my  this virtual machine was running fine.  After upgrading ESX to 4.1, this  single machine running Ubuntu 10.04 will not boot.  The error,  SEGMENTATION FAULT

Gave up waiting for root device
[I][B]
ALERT! /dev/disk/by-label/root does not exist[/B][/I]

Following a bunch of different threads I played around and changed it to /dev/sda1 which is where my Ubuntu seems to reside.  So the error is actually now saying:

[I][B]
 ALERT! /dev/sda1/ does not exist[/B][/I]

Neither change seems to make a difference.

When I run liveCD I can mount the ROOT partition and see my files, I just cannot get the thing to boot.


Here's a copy of my GRUB menu.lst 


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
hiddenmenu

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
# kopt=root=/dev/sda1 ro

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
# defoptions=quiet splash vga=785

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-25-generic root=/dev/sda1 ro quiet splash vga=785
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=9df237ea-9215-43e6-aedd-521b70c738b8 ro  single
initrd        /boot/initrd.img-2.6.32-25-generic

### END DEBIAN AUTOMAGIC KERNELS LIST¿

---

### Post by ishmell on 2011-02-08
I ran into this exact error with Ubuntu 10.4 on ESX 4.1 and here's what I've noticed;

- I only had issues when SAN load was high and virtual disk performance was slow

- During high SAN disk load, I was able to boot past the faults and  busybox shell by disabling acceleration (Properties, Options tab, click  Disable acceleration). 

Once acceleration was disabled, Ubuntu 10.4 booted normally. After the  traffic on the SAN was back to normal, I re-enabled acceleration and  things were fine.

From scanning other forum posts on various websites, the permanent  solution may be to increase the root device detection by adding a  rootdelay=90 line into the grub configuration, but I've not bothered to  try it.

---

