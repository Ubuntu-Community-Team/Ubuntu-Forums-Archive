---
title: "Grub Error 17 - cannot boot my ubuntu"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Houchy on 2010-05-02
Hello,

I have a 80GB Hard Drive with XP installed on it and a 500GB Hard drive with Linux installed in an extended partition.

When I boot on my 80GB Hard Drive, XP starts, no problem.
When I boot on my 500GB Hard Drive, Grub is starting but I cannot get to boot on Ubuntu!! I get the message > Error 17: Partition cannot be mounted

Could anybody help please.

Here's some more information:

```
Disk /dev/hda: 81.9 GB, 81964302336 bytes - Disk identifier: 0xac68976f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *        2048    80766967    40382460    7  HPFS/NTFS
/dev/hda2        80774820   160055594    39640387+   f  W95 Ext'd (LBA)
/dev/hda5        80774883   121740569    20482843+   7  HPFS/NTFS


Disk /dev/sda: 500.1 GB, 500107862016 bytes - Disk identifier: 0x51195119

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   512007614   256003776    7  HPFS/NTFS
/dev/sda3       935802315   976768064    20482875    5  Extended
/dev/sda5       974711745   976768064     1028160   82  Linux swap / Solaris
/dev/sda6       935802441   974711744    19454652   83  Linux

```

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
default		0

## timeout sec
timeout		7

## hiddenmenu
#hiddenmenu

# Pretty colours
color light-blue/black white/blue

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
# kopt=root=UUID=fe298933-90b8-4470-b3e9-be21f2d4a129 ro

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

# on /hda5
title        Windows XP
#hide       (hd1,0)
#unhide     (hd1,4)
rootnoverify (hd1,4)
map        (hd0) (hd1)    
map        (hd1) (hd0)
chainloader	+1	# saut au début de la piste suivante car c’est un OS Microsoft(R)

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=fe298933-90b8-4470-b3e9-be21f2d4a129 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (hd1,4)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=fe298933-90b8-4470-b3e9-be21f2d4a129 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=fe298933-90b8-4470-b3e9-be21f2d4a129 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fe298933-90b8-4470-b3e9-be21f2d4a129 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fe298933-90b8-4470-b3e9-be21f2d4a129 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=fe298933-90b8-4470-b3e9-be21f2d4a129 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=fe298933-90b8-4470-b3e9-be21f2d4a129 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fe298933-90b8-4470-b3e9-be21f2d4a129 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fe298933-90b8-4470-b3e9-be21f2d4a129 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fe298933-90b8-4470-b3e9-be21f2d4a129 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fe298933-90b8-4470-b3e9-be21f2d4a129 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# on /hda5
title        Windows XP
#hide       (hd1,0)
#unhide     (hd1,4)
rootnoverify (hd1,4)
map        (hd0) (hd1)    
map        (hd1) (hd0)
chainloader	+1		# saut au début de la piste suivante car c’est un OS Microsoft(R)

# on /hda1
title        Windows Vista
#hide       (hd1,4)
#unhide     (hd1,0)
rootnoverify (hd1,0)
#makeactive			# cette commande positionne le bit de partition active à 1 (au cas où)
map        (hd0) (hd1) 
map        (hd1) (hd0) 
chainloader	+1		# saut au début de la piste suivante car c’est un OS Microsoft(R)


```

Any help would be greatly appreciated!

Thanks.

---

### Post by oldfred on 2010-05-02
It may be reinstall grub. Did you move partitions or do anything else. If not reinstall grub run the boot info script.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by Houchy on 2010-05-04
Thank you oldfred!

Reinstalling the grub and fixing my menu.lst did the job!

Thanks a lot for you help.

---

