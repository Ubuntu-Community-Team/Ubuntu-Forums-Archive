---
title: "GRUB won't load after dual boot (recurring issue)"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by Mongoose088 on 2009-12-08
Hi all, 

I have a Dell Vostro 1320, dual booting Windows 7 (on hd0,0) and Ubuntu 9.04 (on hd 0,1). Both partitions are running the OSes perfectly.

However, sometimes when I boot Windows and shut down, then turn the computer back on the next day, the computer begins to boot getting as far was "Grub stage 1.5.." then it reboots. It will continue this cycle endlessly until I put in the Super GRUB disk to automatically restore GRUB on my Linux partition. I'm not exactly sure what causes this issue, so I'm not sure what code yo would need, if any, nor am I too familiar with dual boot setups.

Any light on the issue would be appreciated. I'll update this post soon with the grub menu.lst file.

Thanks!
Mongoose

EDIT:
Here's the file:

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=83d2d302-d7c0-493f-b6b6-c12fb2e44c40 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=83d2d302-d7c0-493f-b6b6-c12fb2e44c40

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

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		83d2d302-d7c0-493f-b6b6-c12fb2e44c40
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=83d2d302-d7c0-493f-b6b6-c12fb2e44c40 ro quiet splash i8042.reset 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title 		Windows 7 
root (hd0,0)
savedefault
makeactive
chainloader +1

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		83d2d302-d7c0-493f-b6b6-c12fb2e44c40
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=83d2d302-d7c0-493f-b6b6-c12fb2e44c40 ro  single i8042.reset
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		83d2d302-d7c0-493f-b6b6-c12fb2e44c40
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=83d2d302-d7c0-493f-b6b6-c12fb2e44c40 ro quiet splash i8042.reset
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		83d2d302-d7c0-493f-b6b6-c12fb2e44c40
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=83d2d302-d7c0-493f-b6b6-c12fb2e44c40 ro  single i8042.reset
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		83d2d302-d7c0-493f-b6b6-c12fb2e44c40
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=83d2d302-d7c0-493f-b6b6-c12fb2e44c40 ro quiet splash i8042.reset
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		83d2d302-d7c0-493f-b6b6-c12fb2e44c40
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=83d2d302-d7c0-493f-b6b6-c12fb2e44c40 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		83d2d302-d7c0-493f-b6b6-c12fb2e44c40
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by phillw on 2009-12-08
Yeah, it is a pain in the ****

[http://ubuntuforums.org/showthread.php?p=8433673#post8433673](http://ubuntuforums.org/showthread.php?p=8433673#post8433673)

You're not alone. It looks like there is a backup utility running that causes part of MBR to be over-written. The above thread has further details on how to 'tame' that backup system that is running within the Win boot.

Regards,

Phill.

---

