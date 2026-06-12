---
title: "Moving Partition"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by mk04 on 2006-12-23
Newbie here,
I am trying to dualboot WinXP Home and Ubuntu 6.06. My partition table looks like this:

Ext3 (Ubuntu/Root) ---- WinXP (NTFS) ----- Linux Swap

I need for it to look like this:

Linux Swap ----- Ext 3 ---- WinXP

How do I move my partitions around? Any software out there to do that. I have Acronis Disk Director Suite, but when I try to move it, it asks me to move it to an unallocated space, I just want to switch them around. Thanks for the help.  :-D 

](*,) ](*,)


EDIT: When I boot up my laptop, it boots directly into XP, GRUB Bootloader does not show up. I am assuming, this is the reason why. Am I correct, or is there another problem?

---

### Post by shane2peru on 2006-12-23
What would be the purpose of changing where you partitions are located on the disk?  

If it is that important to you 1.  BACKUP BACKUP BACKUP.  It is always important when playing with your partitions that you BACKUP.  After that you can install Gparted  Open **System - Administration - Synaptics**  And search for Gparted.  You should be able to change your partitions around, however you are going to have to have space that is not being used so you can change your partitions around.  Like the problem you ran into in with the other program.  I don't think it is possible to just move a partition without putting it into open space.  

Shane

---

### Post by mk04 on 2006-12-23
> **shane2peru said:**
> What would be the purpose of changing where you partitions are located on the disk?  

Shane

If the order of the partitions don't matter why won't Grub boot up. WinXP boots up right away!

---

### Post by bulldog on 2006-12-23
Just take a look at your menu.lst then.
The place of your partitions has nothing to do with GRUB.

The most used way of partitioning is windows on the first primary,where ubuntu is located is not that important.

Can you boot the live cd and give me the response of```
sudo fdisk -l (l as in like)
```

---

### Post by mk04 on 2006-12-23
I got ubuntu to load, but now at the grub menu, winxp isnt listed. I did a google search, and found that you need to add it to menu.lst

When I do try to add it, I get this error: 
"Could not save the file /boot/grub/menu.lst.
You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again."

I have windows xp in the /dev/hda2 partition, can anyone help? Thanks again.

---

### Post by bulldog on 2006-12-23
Read my previous post please.
To add windows to your menu.lst```
gksudo gedit /boot/grub/menu.lst
```
Add windows to it and save the file.
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Professional
rootnoverify (hd0,1)
savedefault
chainloader	+1
```

---

### Post by shane2peru on 2006-12-23
Also, make sure you put Windows toward the bottom so that when Ubuntu Kernel is updated, it doesn't overwrite your Windows option in your menu.lst.

Shane

Ps, that is odd that you managed to get windows on your second partition and Ubuntu on the first part.

---

### Post by bulldog on 2006-12-23
> **shane2peru said:**
> Also, make sure you put Windows toward the bottom so that when Ubuntu Kernel is updated, it doesn't overwrite your Windows option in your menu.lst.

Shane

Ps, that is odd that you managed to get windows on your second partition and Ubuntu on the first part.

I've seen it before and if we have a bit of bad luck it won't boot either :(

---

### Post by mk04 on 2006-12-23
Sorry, but I am a linux newbie, how do you enter these codes?

gksudo gedit /boot/grub/menu.lst

sudo fdisk -l (l as in like)

When I do enter the info into menu.lst i get an error!

---

### Post by bulldog on 2006-12-23
Hit ALT + F2 and type in the box gnome-terminal.
You enter the commands one by one in this terminal [copy and paste]
and put the output of sudo fdisk -l on the forum to begin.:D

---

### Post by mk04 on 2006-12-23
/boot/grub/menu.lst

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


---

### Post by bulldog on 2006-12-23
Copy this to the end of the menu.lst [what already is listed there you have not to copy]
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Professional
rootnoverify (hd0,1)
savedefault
chainloader	+1
```

And try if it will boot windows,if not I'm afraid you have to make some changes to the boot.ini file in your windows.

---

### Post by mk04 on 2006-12-23
when I try to edit the menu.lst i get this error:

> "Could not save the file /boot/grub/menu.lst.
You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again."

---

### Post by shane2peru on 2006-12-23
Are you booted into a LiveCD, or your actual Ubuntu?

Shane

---

### Post by mk04 on 2006-12-23
Actual Ubuntu

---

### Post by bulldog on 2006-12-23
Use the sudo command as stated in my posting.
```
gksudo gedit /boot/grub/menu.lst
```
Now add the entry to the menu.lst and save it.

That's all you have to do,and reboot to see if this entry works.

If you prefer to do it with a graphical interface and navigate to the file and open it from there,hit ALT + F2 and type in the box gksudo nautilus.
Be careful you're operating as a root than,and if you change anything it could damage your install severe.

---

### Post by mk04 on 2006-12-23
That worked perfectly. Thanks so much for your help. You guys are awesome :D

---

