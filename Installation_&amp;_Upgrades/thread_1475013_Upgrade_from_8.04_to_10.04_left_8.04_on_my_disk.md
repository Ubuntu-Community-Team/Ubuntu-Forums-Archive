---
title: "Upgrade from 8.04 to 10.04 left 8.04 on my disk"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by rsanchez1 on 2010-05-06
My issue is that while I was upgrading from Hardy to Lucid, everything was going fine until the very end when some packages were badly corrupted (according to the installer) and the upgrade could not complete. When I rebooted, it would not load into the login screen, and instead just presented me with a console. However, 10.04 showed up under GRUB, I loaded 10.04, and it worked fine, so I just changed GRUB to load 10.04 by default. I managed to fix the broken package problem from 10.04.

The problem now is that, since it was a "partial" upgrade and terminated before completion, I still have 8.04 on my hard disk. I can still load 8.04 and still get the same console, instead of the login screen. I just wanted to know how I can "complete" the upgrade and get rid of 8.04. Except for that one issue, upgrade was successful. Thanks for the assistance.

---

### Post by kansasnoob on 2010-05-06
First boot into 10.04 and run:

```
sudo update-grub
```

Reboot and see if that changed things. If not please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by rsanchez1 on 2010-05-06
I'm still getting 8.04 on my boot list from grub. Here is the RESULTS.txt file:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   150,255,944   150,255,882  83 Linux
/dev/sda2         150,255,945   156,248,189     5,992,245   5 Extended
/dev/sda5         150,256,008   156,248,189     5,992,182  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        346b36b1-05a6-4be5-b1b8-9d9392a336f2   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

hiddenmenu
default 7
timeout 0

title Ubuntu 8.04.1, kernel 2.6.24-22-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro quiet splash all_generic_ide
initrd /boot/initrd.img-2.6.24-22-generic

title Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro single
initrd /boot/initrd.img-2.6.24-22-generic

title Ubuntu 8.04.1, kernel 2.6.24-21-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro quiet splash all_generic_ide
initrd /boot/initrd.img-2.6.24-21-generic

title Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro single
initrd /boot/initrd.img-2.6.24-21-generic

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro quiet splash all_generic_ide
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin

title Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.32-21-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro quiet splash vga=775
initrd /boot/initrd.img-2.6.32-21-generic

title Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.32-21-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro  single
initrd /boot/initrd.img-2.6.32-21-generic

title Ubuntu 10.04 LTS, kernel 2.6.24-27-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-27-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro quiet splash vga=775
initrd /boot/initrd.img-2.6.24-27-generic

title Ubuntu 10.04 LTS, kernel 2.6.24-27-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-27-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro  single
initrd /boot/initrd.img-2.6.24-27-generic

title Ubuntu 10.04 LTS, kernel 2.6.24-26-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-26-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro quiet splash vga=775
initrd /boot/initrd.img-2.6.24-26-generic

title Ubuntu 10.04 LTS, kernel 2.6.24-26-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-26-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro  single
initrd /boot/initrd.img-2.6.24-26-generic

title Ubuntu 10.04 LTS, kernel 2.6.24-25-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-25-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro quiet splash vga=775
initrd /boot/initrd.img-2.6.24-25-generic

title Ubuntu 10.04 LTS, kernel 2.6.24-25-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-25-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro  single
initrd /boot/initrd.img-2.6.24-25-generic

title Ubuntu 10.04 LTS, kernel 2.6.24-24-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-24-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro quiet splash vga=775
initrd /boot/initrd.img-2.6.24-24-generic

title Ubuntu 10.04 LTS, kernel 2.6.24-24-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-24-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro  single
initrd /boot/initrd.img-2.6.24-24-generic

title Ubuntu 10.04 LTS, kernel 2.6.24-23-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-23-386 root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro quiet splash vga=775
initrd /boot/initrd.img-2.6.24-23-386

title Ubuntu 10.04 LTS, kernel 2.6.24-23-386 (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-23-386 root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro  single
initrd /boot/initrd.img-2.6.24-23-386

title Ubuntu 10.04 LTS, kernel 2.6.24-23-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro quiet splash vga=775
initrd /boot/initrd.img-2.6.24-23-generic

title Ubuntu 10.04 LTS, kernel 2.6.24-23-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro  single
initrd /boot/initrd.img-2.6.24-23-generic

title Ubuntu 10.04 LTS, kernel 2.6.24-22-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro quiet splash vga=775
initrd /boot/initrd.img-2.6.24-22-generic

title Ubuntu 10.04 LTS, kernel 2.6.24-22-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro  single
initrd /boot/initrd.img-2.6.24-22-generic

title Ubuntu 10.04 LTS, kernel 2.6.24-21-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro quiet splash vga=775
initrd /boot/initrd.img-2.6.24-21-generic

title Ubuntu 10.04 LTS, kernel 2.6.24-21-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro  single
initrd /boot/initrd.img-2.6.24-21-generic

title Ubuntu 10.04 LTS, kernel 2.6.24-19-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro quiet splash vga=775
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 10.04 LTS, kernel 2.6.24-19-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro  single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 10.04 LTS, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
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
# kopt=root=UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b

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


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=be1c0d4c-32f1-4a9b-95a1-bed4bbb4273b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=346b36b1-05a6-4be5-b1b8-9d9392a336f2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  30.9GB: boot/grub/menu.lst
  30.9GB: boot/grub/stage2
  31.0GB: boot/initrd.img-2.6.24-19-generic
  30.9GB: boot/initrd.img-2.6.24-19-generic.bak
  30.9GB: boot/initrd.img-2.6.24-21-generic
  30.9GB: boot/initrd.img-2.6.24-21-generic.bak
  30.9GB: boot/initrd.img-2.6.24-22-generic
  31.0GB: boot/initrd.img-2.6.24-22-generic.bak
  30.8GB: boot/initrd.img-2.6.24-23-386
  30.9GB: boot/initrd.img-2.6.24-23-386.bak
  31.0GB: boot/initrd.img-2.6.24-23-generic
  30.9GB: boot/initrd.img-2.6.24-23-generic.bak
  30.9GB: boot/initrd.img-2.6.24-24-generic
  31.0GB: boot/initrd.img-2.6.24-24-generic.bak
  31.0GB: boot/initrd.img-2.6.24-25-generic
  30.8GB: boot/initrd.img-2.6.24-25-generic.bak
  30.8GB: boot/initrd.img-2.6.24-26-generic
  31.0GB: boot/initrd.img-2.6.24-26-generic.bak
  70.4GB: boot/initrd.img-2.6.24-27-generic
  70.4GB: boot/initrd.img-2.6.24-27-generic.bak
  31.0GB: boot/initrd.img-2.6.32-21-generic
  31.0GB: boot/initrd.img-2.6.32-22-generic
  30.9GB: boot/vmlinuz-2.6.24-19-generic
  30.8GB: boot/vmlinuz-2.6.24-21-generic
  30.9GB: boot/vmlinuz-2.6.24-22-generic
  30.9GB: boot/vmlinuz-2.6.24-23-386
  30.9GB: boot/vmlinuz-2.6.24-23-generic
  30.9GB: boot/vmlinuz-2.6.24-24-generic
  30.8GB: boot/vmlinuz-2.6.24-25-generic
  31.0GB: boot/vmlinuz-2.6.24-26-generic
  31.0GB: boot/vmlinuz-2.6.24-27-generic
  31.0GB: boot/vmlinuz-2.6.32-21-generic
  31.0GB: boot/vmlinuz-2.6.32-22-generic
  31.0GB: initrd.img
  31.0GB: initrd.img.old
  31.0GB: vmlinuz
  31.0GB: vmlinuz.old
```

---

### Post by davidmohammed on 2010-05-07
suggest edit your /boot/grub/menu.lst file and change the default value from 7 to 0.

remember to do a sudo update-grub  followed by a reboot to boot into the lucid kernel

---

### Post by rsanchez1 on 2010-05-07
Wouldn't that cause GRUB to boot Hardy by default? I can use Lucid just fine, but I can't use Hardy. I want to get rid of Hardy anyway.

---

### Post by davidmohammed on 2010-05-08
OK, misunderstood what you wanted.  It looks like from the file above that you have just lucid on your PC - correct?  You dont have hardy in a separate partition.

Personnally, I would cleanup your installation by installing ubuntu-tweak (google and add the ubuntu-tweak ppa to your software sources).  In that application there is a nice and easy cleanup utility to delete all the old hardy kernels.  While you are at it cleanup old packages and cache etc.

You could do this via terminal - its just easier this way.

---

### Post by rsanchez1 on 2010-05-10
Thanks for the advice. I've never used Ubuntu Tweak, so I want to get your advice before using it. When I go to Package Cleaner and select Clean Config, Clean Kernels, etc. they all have a Select All option towards the bottom. Now, do those menus only display packages/kernels that are no longer needed by my system, making it safe to select and remove all?

---

### Post by davidmohammed on 2010-05-10
Correct almost - the kernels option doesnt display the current kernel.  As a rule of thumb you should keep the current kernel and the previous kernel that works with your system.

For example, on my system I have .22 and .21.  Both kernels work fine on my system.

Therefore in ubuntu-tweak, I tick all  packages EXCEPT those that end 32-21 i.e. I boot with 32-22 so this isn't displayed.`

I've personally never had any issues with  clean packages, clean cache or clean config.

If you are of a nervous disposition - back-up your system first with something like clonezilla.

---

