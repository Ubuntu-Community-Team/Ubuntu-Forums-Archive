---
title: "switch kernel to  2.6.22-14-generic"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by davidshere on 2008-02-11
I would like to switch my kernel from 2.6.22-14-386 to  2.6.22-14-generic, in order to accommodate vmware-server, which has no vmnet module for 2.6.22-14-386 kernel, as reported here:
[https://bugs.launchpad.net/ubuntu/+source/vmware-server-kernel-modules-2.6.22/+bug/185415](https://bugs.launchpad.net/ubuntu/+source/vmware-server-kernel-modules-2.6.22/+bug/185415)

I must have my virtual machines!  So I'm willing to risk killing my host machine, but of course I would rather not.  The tutorials I've found involve compiling a new kernel, which I would rather not do; I simply want to install a new kernel, like is done during an upgrade, and start using it instead.

Again, my machine is currently using 2.6.22-14-386 and I wish to start using 2.6.22-14-generic instead.  Here is my Automagic Kernels List from grub.  As you can see, no generic kernels available.

```
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
# kopt=root=UUID=a484472c-2d89-4436-88f7-b1cd3663762a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=splash vga=773

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
# howmany=3

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
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-386 root=UUID=a484472c-2d89-4436-88f7-b1cd3663762a ro splash vga=773
initrd          /boot/initrd.img-2.6.22-14-386

title           Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-386 root=UUID=a484472c-2d89-4436-88f7-b1cd3663762a ro single
initrd          /boot/initrd.img-2.6.22-14-386

title           Ubuntu 7.10, kernel 2.6.20-16-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-386 root=UUID=a484472c-2d89-4436-88f7-b1cd3663762a ro splash vga=773
initrd          /boot/initrd.img-2.6.20-16-386

title           Ubuntu 7.10, kernel 2.6.20-16-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-386 root=UUID=a484472c-2d89-4436-88f7-b1cd3663762a ro single
initrd          /boot/initrd.img-2.6.20-16-386

title           Ubuntu 7.10, kernel 2.6.17-11-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=a484472c-2d89-4436-88f7-b1cd3663762a ro splash vga=773
initrd          /boot/initrd.img-2.6.17-11-386

title           Ubuntu 7.10, kernel 2.6.17-11-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=a484472c-2d89-4436-88f7-b1cd3663762a ro single
initrd          /boot/initrd.img-2.6.17-11-386

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by mikewhatever on 2008-02-11
Why not simply install the desired kernel from the repositories, Synaptic? Once installed, you should have it appear in Grub boot menu. If the new kernel does not work, you could just reboot and choose one of the old ones.

Do you have all of those kernels installed? If looks like you've been upgrading from Edgy to Gutsy, with Feisty in between. Consider uninstalling the ones you don't need to free disk space. That can also be done from Synaptic.

---

### Post by davidshere on 2008-02-11
> **mikewhatever said:**
> Why not simply install the desired kernel from the repositories, Synaptic? Once installed, you should have it appear in Grub boot menu. 

Yes!  That's exactly what I want to do.  I'm not sure why I didn't think of that.  

I shall execute that plan and report back.

---

### Post by davidshere on 2008-02-11
'twould appear that that worked:

```
david@lancer:~$ uname -a
Linux lancer.davidshere.com 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 i686 GNU/Linux

```

```
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-386 root=UUID=a484472c-2d89-4436-88f7-b1cd3663762a ro splash vga=773
initrd          /boot/initrd.img-2.6.22-14-386

title           Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-386 root=UUID=a484472c-2d89-4436-88f7-b1cd3663762a ro single
initrd          /boot/initrd.img-2.6.22-14-386

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a484472c-2d89-4436-88f7-b1cd3663762a ro splash vga=773
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a484472c-2d89-4436-88f7-b1cd3663762a ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.20-16-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-386 root=UUID=a484472c-2d89-4436-88f7-b1cd3663762a ro splash vga=773
initrd          /boot/initrd.img-2.6.20-16-386

title           Ubuntu 7.10, kernel 2.6.20-16-386 (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-386 root=UUID=a484472c-2d89-4436-88f7-b1cd3663762a ro single
initrd          /boot/initrd.img-2.6.20-16-386

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by mikewhatever on 2008-02-11
Great! :)

---

