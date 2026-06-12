---
title: "GRUB2 and osx86 / Hackintosh"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by slayer^_^ on 2010-02-13
After several attempts I understood that, even though Grub2 is able to automatically recognize the osx86 / Hackintosh partition, it is not able to boot.

I managed to solve it like this:

1) Open a privileged nautilus:

```
 gksudo nautilus 
```

enter your password and hit enter;

2) Navigate to /boot/grub

3) Right click on the file "grub.cfg" and change permissions, so you can write it;

4) Make a backup copy of the "grub.cfg" file before proceeding

5) Double-click on the "grub.cfg" file to open it with gEdit and modify it

6) Scroll down till you find the Osx grub entry that should look like this:

> menuentry "Mac OS X (on /dev/sda1)" {
insmod hfsplus
set root=(hd0,1)
search --no-floppy --fs-uuid --set d8d3935e73aae5d9
insmod vbe
do_resume=0
if [ /var/vm/sleepimage -nt10 / ]; then
if xnu_resume /var/vm/sleepimage; then
do_resume=1
fi
fi
if [ $do_resume == 0 ]; then
xnu_uuid d8d3935e73aae5d9 uuid
if [ -f /Extra/DSDT.aml ]; then
acpi -e /Extra/DSDT.aml
fi
xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
xnu_mkext /System/Library/Extensions.mkext
else
xnu_kextdir /System/Library/Extensions
fi
if [ -f /Extra/Extensions.mkext ]; then
xnu_mkext /Extra/Extensions.mkext
fi
if [ -d /Extra/Extensions ]; then
xnu_kextdir /Extra/Extensions
fi
if [ -f /Extra/devtree.txt ]; then
xnu_devtree /Extra/devtree.txt
fi
if [ -f /Extra/splash.jpg ]; then
insmod jpeg
xnu_splash /Extra/splash.jpg
fi
if [ -f /Extra/splash.png ]; then
insmod png
xnu_splash /Extra/splash.png
fi
if [ -f /Extra/splash.tga ]; then
insmod tga
xnu_splash /Extra/splash.tga
fi
fi
}



7) Modify it like this (or insert a new entry that looks like this) :

```
menuentry "MacOS X, chameleon" {
        insmod hfsplus
        set root=(hd0,1)
        multiboot /boot
}
```

Or if you have several renamed boot files in OS X's partition root you could also do this:

```
menuentry "MacOS X, chameleon" {
        insmod hfsplus
        search --file --set=root /chameleon.rc3.boot
        multiboot /chameleon.rc3.boot
}
```


BE SURE NOT TO CHANGE YOUR "set root=(hdx,y)" STRING, **IT DEPENDS ON YOUR OWN **PARTITION TABLE !!!

8) Reboot and see if the entry works...

9) If you're able to boot your osx86 partition print, save or remember this post... on major kernel updates it is possible that you have to repeat the process...

Cheers :P

**Disclaimer : This post is intended for a better understanding of the GRUB2 bootloader, I don't mean to encourage the use of hacked versions of Apple Software. If you like Snow Leopard you should buy a Mac (I personally own one).**

---

### Post by cdummy on 2010-05-22
This doesn't work for me. File not found error. Where should I have "boot" file? Or "chameleon.rc3.boot"? In linux partition ? OS X partition? All I see there are mach_kernel files.
Thanks for help

---

### Post by slayer^_^ on 2010-05-29
> **cdummy said:**
> This doesn't work for me. File not found error. Where should I have "boot" file? Or "chameleon.rc3.boot"? In linux partition ? OS X partition? All I see there are mach_kernel files.
Thanks for help


Which osx are you using?

---

### Post by cdummy on 2010-05-31
I'm using 10.5.6 on MSI Wind with Ubuntu and windows 7. I found boot, boot0 and chain0 etc files in OS X and copied them all to /
in Ubuntu still grub2  can't open the file(permissions?). Tried to boot with all of them changing the name of the file after /
Thanks for trying to answer to my problems.

---

### Post by slayer^_^ on 2010-05-31
> **cdummy said:**
> I'm using 10.5.6 on MSI Wind with Ubuntu and windows 7. I found boot, boot0 and chain0 etc files in OS X and copied them all to /
in Ubuntu still grub2  can't open the file(permissions?). Tried to boot with all of them changing the name of the file after /
Thanks for trying to answer to my problems.



Grub2 should automatically recognize your osx86 partition and add an entry to the grub.cfg file.

The issue is that it adds a non valid entry for various reasons (it is supposed to start a normal Mac os X partition on a Mac, I suppose...)

You don't need to copy any file from the osx partition to the ubuntu one.

You just need to edit the grub.cfg in the directory /boot/grub as explained in the tutorial.


Try out and let me know, it should work for sure !

---

### Post by bapoumba on 2010-05-31
*Ahem*
Apple policy states that Apple software should be run only on Apple hardware. Not talking about Hackintosh.. Closing the thread.

---

