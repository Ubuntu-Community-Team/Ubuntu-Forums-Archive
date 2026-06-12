---
title: "Jaunty Booting Verbose"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by vahnx on 2009-03-27
I see the loading bar booting from the live cd, but after I installed I only get a verbose boot and shutdown. How can I enable the splash boot/shutdown? Here's my menu.lst:

```
color cyan/blue white/blue
default		0
timeout		10

title		Windows 7
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Mac OS X
root	        (hd0,2)
chainloader	+1

title		Ubuntu 9.04
uuid		548dcdef-8845-423d-ac2a-d9af4833f6d4
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/sda2 ro quiet splash
quiet


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
# kopt=root=UUID=548dcdef-8845-423d-ac2a-d9af4833f6d4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=548dcdef-8845-423d-ac2a-d9af4833f6d4

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
# defoptions=quiet splash quiet splash

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
```

---

### Post by coffeecat on 2009-03-27
You haven't got an initrd line in your menu.lst. You need something like this, but make sure you've got initrd.img in /boot.

```
initrd        /boot/initrd.img-2.6.28-11-generic
```

---

### Post by vahnx on 2009-03-31
Yeah, I'm missing initrd.img-2.6.28-11 in /boot. Could someone upload theirs? Cannot find it on Google or Synaptics. Thanks.

---

### Post by coffeecat on 2009-03-31
> **vahnx said:**
> Yeah, I'm missing initrd.img-2.6.28-11 in /boot. Could someone upload theirs? Cannot find it on Google or Synaptics. Thanks.

No, you should be able to generate your own with:

```
sudo update-initramfs -c
```

Then simply make sure you've got the initrd line in menu.lst

---

### Post by biji on 2009-03-31
try to remove menu.lst then type update-grub

---

### Post by vahnx on 2009-03-31
> **coffeecat said:**
> No, you should be able to generate your own with:

```
sudo update-initramfs -c
```

Then simply make sure you've got the initrd line in menu.lst

```

$ sudo update-initramfs -k 2.6.28-11 -c
update-initramfs: Generating /boot/initrd.img-2.6.28-11
/etc/initramfs-tools/conf.d/resume: 1: Syntax error: "(" unexpected
```

> **biji said:**
> try to remove menu.lst then type update-grub
Didn't fix it. I notice it says something like 'ext3-fs sda2 could not be mounted due to unsupported features' which is my linux partition and I'm using ext4, and it's obviously mounted when I'm in the OS (duh). During shutdown I see 'nm-system-settings ... ifdown'.

---

### Post by biji on 2009-03-31
Nah..... 
try to remove that file /etc/initramfs-tools/conf.d/resume (backup first)
and run update-initramfs again

---

### Post by vahnx on 2009-04-03
OK I backed up and removed the file, update-initramfs ran successfully (took about 5-10 seconds and I saw HDD activity) then I rebooted and it's still booting in verbose.

---

### Post by dentaku65 on 2009-04-03
Try with startupmanager
```
sudo apt-get install startupmanager
```
Then
```
sudo startupmanager
```
Make sure to set the Color Depth to 16 and the correct Resolution of your monitor; in Appearance choose under Usplash Theme: usplash-theme-ubuntu

---

### Post by vahnx on 2009-04-08
It was set to 8 depth, so I switched to 16 and splash was correct. Saved settings, rebooted, still booting verbose.

EDIT: Solved. Did sudo startupmanager from terminal, and I noticed it prompted me to "overwrite grub" in the terminal after I closed it. So I did so and now it's booting verbose.

---

