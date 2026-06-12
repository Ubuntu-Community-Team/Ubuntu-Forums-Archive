---
title: "amd dual core problem"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by TOOOL on 2007-11-12
when running 7.4 it showed 2 cpu boxes in the system manger display
since upgrading to 7.10 it now only shows 1, when i look at the system info its says i have a amd 4000+ dual core ship but on the screen with the usage graphs only displays 1 not 2 as it us to
is there a setting for this
cheers

---

### Post by bulldog on 2007-11-12
Try in a terminal```
cat /proc/cpuinfo
```
You should see two different cpu's

---

### Post by TOOOL on 2007-11-14
this is the out put i get

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
stepping        : 1
cpu MHz         : 1000.000
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge 
mca cmov
pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps
bogomips        : 2011.04
clflush size    : 64


still only shows one cpu working on system tray where it shows graphs of cpu memory and internet speed

---

### Post by zdude on 2007-11-14
You need to run the 'generic' kernel not the 386 one. When I upgraded, I got both the generic and 386 kernels. If your grub menu shows both select the generic one.

---

### Post by TOOOL on 2007-11-15
how do you do this as i don't have a grub menu, as it is the sole operating system on the machine
cheers

---

### Post by bulldog on 2007-11-15
You have certainly a GRUB menu,otherwise you couldn't boot ubuntu.

Boot ubuntu and open a terminal.
Have a look in the menu.lst which kernels are installed
```
cat /boot/grub/menu.lst
```
Copy the output to the forum please.[copy/paste]

You can install from synaptics the generic kernel 
linux-image-2.6.22-14-generic
linux-restricted-modules-2.6.22-14-generic
linux-headers-2.6.22-14-generic

Take a look in synaptic for those packages,install and reboot,choose the new kernel.
With ```
uname -r
``` you can see which kernel you're running.

---

### Post by TOOOL on 2007-11-16
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
# kopt=root=UUID=530dd468-4f7c-43fa-95c7-32341e1b56ba ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-386 root=UUID=530dd468-4f7c-43fa-95c7-32341e1b56ba ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-386
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-386 root=UUID=530dd468-4f7c-43fa-95c7-32341e1b56ba ro single
initrd          /boot/initrd.img-2.6.22-14-386

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=530dd468-4f7c-43fa-95c7-32341e1b56ba ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=530dd468-4f7c-43fa-95c7-32341e1b56ba ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=530dd468-4f7c-43fa-95c7-32341e1b56ba ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=530dd468-4f7c-43fa-95c7-32341e1b56ba ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by TOOOL on 2007-11-16
tryed the code for selecting kernal but just gives a number out put

---

### Post by zdude on 2007-11-16
You need to delete this section of the menu.lst

title Ubuntu 7.10, kernel 2.6.22-14-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-386 root=UUID=530dd468-4f7c-43fa-95c7-32341e1b56ba ro quiet splash
initrd /boot/initrd.img-2.6.22-14-386
quiet

title Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-386 root=UUID=530dd468-4f7c-43fa-95c7-32341e1b56ba ro single
initrd /boot/initrd.img-2.6.22-14-386

These are the 386 kernels and you will not get both cpus running if you select them. Since they are the first item in your menu.lst they boot automatically (well, the first item does). I removed these from my menu.lst.

---

### Post by TOOOL on 2007-11-18
cheers for that seems to have fixed it, now shows 2 cpu's

---

