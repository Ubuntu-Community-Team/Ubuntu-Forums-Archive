---
title: "Boot CD from GUB command line"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by _TK_ on 2008-04-16
Whilst Trying to install xubuntu 7.10 onto my laptop, the install went fine (or so I thaught) so I turned the laptop off. When I next try to load up the laptop, all I seem to get is the Grub command line. 

I've tried to insert the live CD to get Grub to load that up and re-install, but to no avail. It automatically comes up to 'grub>'. I was hoping that by doing a reinstall it might solve the problem!

As I'm new to linux in general, Im terrified that Ive managed to brick my laptop in one easy step!

_TK_

---

### Post by dstew on 2008-04-16
If you get the grub command line, you have at least succeeded in loading grub stage2. I suspect that grub is installed correctly, but mis-configured. The problem might be that there is no menu.lst file for grub to load. To figure out what is wrong and fix it, we probably need to boot the Live CD. You might have to change the boot disk order in your BIOS to put the CD before the hard disk, to be able to boot the Live CD

We can also do some work from the grub command line (enter help to see all the grub commands). You can try to get a grub menu by typing **configfile** on the command line, but instead of enter press the Tab key. Grub has an auto-complete feature. You can tab along and look in the different devices, partitions, and folders for the menu.lst file. Usually it will be in /boot/grub directory of the root device.

---

### Post by _TK_ on 2008-04-16
Firstly, the BIOS is already configured to allow the CD to boot beforethe hard disk, yet the GRUB interface still appears, thus not letting me load up the liveCD to wipe the system and start again. Unfortunatly the boot order is about the only thing I CAN change in the BIOS, as I have completely forgotten the password for setup, and have no idea as to how to reset the BIOS!

Secondly, when I type 'configfile ' then [Tab] I get the following error "Error 1: Filename must be either an absolute pathname or blocklist

Thanks

_TK_

---

### Post by dstew on 2008-04-16
Try ```
configfile (hd
```then tab.

---

### Post by _TK_ on 2008-04-16
OK...

The possible partitions are:
    Partition num: 0, Filesystem type is ext2fs, partition type 0x83 (I assume this is (hd0,0)!)
    Partition num: 4, Filesystem type is unknown, partition type 0x82 (I assume this is (hd0,4)!)

What is this really telling me? and how can I use this to help?

_TK_

---

### Post by dstew on 2008-04-16
OK, now add to the line to make it **configfile (hd0,0) /boot/grub/ **then tab again to see if it lists a menu.lst file. If it does, complete the configfile line with it, and press enter.

---

### Post by _TK_ on 2008-04-17
When I type:

'configfile (hd0,0) /boot/grub/'

and press [Tab] I get: "Error 15: File not found"

When I press [Enter] I get: "Error 1: Filename must be either an absolute pathname or blocklist"

_TK_

---

### Post by dstew on 2008-04-17
> and press [Tab] I get: "Error 15: File not found"At configfile (hd0,0)/boot/ and tab, do you see the grub directory in the listing? Anyway, if the grub directory is not there, your system is not installed properly. If it is, you should see a listing of the files in it when you get to (hd0,0) /boot/grub/ and tab.

The complete line, if the menu.lst file is there, would be```
grub> configfile (hd0,0)/boot/grub/menu.lst
```If this command is successful, the menu comes up.

Also, I am not sure if it is important to leave out the space between (hd0,0) and /boot. You can try it both ways, I think it doesn't matter.

---

### Post by _TK_ on 2008-04-17
> **dstew said:**
> At configfile (hd0,0)/boot/ and tab, do you see the grub directory in the listing?

When I hit [Enter] with this line, I get the following:

"Possible files are: System.map-2.6.22-14generic abi-2.6.22-14-generic config-2.6.22-14-generic initrd.img-26.22-14-generic.bak memtest86+.bin vmlinuz-2.6.22-14-generic"

> **dstew said:**
>  Anyway, if the grub directory is not there, your system is not installed properly.

Does this mean that the system isn't installed? If so how do I re-install it?!

Thanks

_TK_

---

### Post by dstew on 2008-04-17
> Does this mean that the system isn't installed?It is not correctly installed. The kernels are there, but not the grub directory. You could try to get it working, but I think you should try to install again from scratch.

If you are really stuck, and cannot get the CD to boot, you could try to boot the partly installed Xubuntu system, again by using the grub command line. To do it, you could put in this series of commands at the grub prompt:```
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sda1 ro
initrd /boot/initrd.img-26.22-14-generic.bak
boot
```
It might be worth googling for your laptop's user or service manual, to see how to get into your BIOS setup to change the boot order, or to enable the CD to boot again. Make sure that the CD you try to boot is truly bootable. Try to boot it in another computer first to see if it works.

---

### Post by _TK_ on 2008-04-17
The GRUB commands helped me to boot to the xubuntu LiveCD boot screen. From here I can perform an OEM install and just wipe the system.

I was paranoid that the laptop woud just refuse to boot!

Thanks for your help

_TK_

---

### Post by dstew on 2008-04-17
It is possible we were looking at the directory in the Live CD, and not in the hard disk! Anyway, glad you got it booted. Good luck.

---

