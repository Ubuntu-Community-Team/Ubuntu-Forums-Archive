---
title: "Install Windows XP - cannot launch Windows XP"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by ifthengoto on 2006-12-28
I have seen several posts on this but not exactly my situation. I am obviously a beginner!

I have a Dell desktop with windows XP. I now have a new Western Digital my book USB drive 250GB

I have finally managed to install the ubuntu alternative iso on the USB drive. When I reboot I get a message 

"grub loading 1.5 please wait" - then I get an error message 18.

Using this method I cannot get into windows or ubuntu. 

GOOD news is that when I interrupt the boot process by hitting F12 and select the menu option USB drive - then I am able to load Ubuntu.

Issue is how can I get back to a system where I can choose Windows if I need it?

I have seen people withsimilar problems here and they were asked for the out put of various commends like fdisk

here is mine

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           4       32098+  de  Dell Utility
/dev/hda2   *           5        9725    78083932+   7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+  83  Linux
/dev/sda2            6375        6629     2048287+  82  Linux swap / Solaris
/dev/sda3            6630       30401   190948590    7  HPFS/NTFS
/dev/sda4               1           1           0+  83  Linux
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

My menu.lst is here (apologies if too much code info)

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
# kopt=root=UUID=e18053e0-8c8c-4c9c-aa54-e902d798195e ro
# kopt_2_6=root=/dev/sda1 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


Could anybody help me please configure this or come up with a different solution so I can choose between the two systems WindowsXP or Ubuntu.

If I have to interupt the boot process by hitting F12 this is also no problem.

Thks.

---

### Post by bulldog on 2006-12-28
You have GRUB installed on the external drive.
Nothing wrong with that :D 

The question is what you want to do,install GRUB on the windows disk,so you can choose windows or ubuntu to boot,or leave GRUB where it is and reinstall the windows bootloader.

I should go for reinstalling the windows boot loader.
If you want to boot ubuntu,hit F12 and choose the external drive.

Boot from the windows install cd and go through the steps till you get three options.
1/ Install Windows
2/ Repair a Windows install
3/ Exit

Choose option two which takes you to a console [recovery console].
Here you see your windows listed,choose it,mostly option 1,and provide the administrator password.
If done and you're logged on,type fixmbr,you'll get a warning but proceed,and your windows boot loader should be reinstalled.

---

### Post by ifthengoto on 2006-12-28
> **bulldog said:**
> 

Boot from the windows install cd and go through the steps till you get three options.
1/ Install Windows
2/ Repair a Windows install
3/ Exit

Choose option two which takes you to a console [recovery console].
Here you see your windows listed,choose it,mostly option 1,and provide the administrator password.
If done and you're logged on,type fixmbr,you'll get a warning but proceed,and your windows boot loader should be reinstalled.

@bulldog, Thanks for that, tried your option 2 - issue is the admin password... This is my home PC and I have never used a password - when I try to enter anything (including nothing) I get booted off my own PC. I don't know how to get around that.

---

### Post by bulldog on 2006-12-28
Try ADMINISTRATOR OR administrator if you didn't set a password.

Or reinstall GRUB on the windows disk,so you can boot windows with GRUB.
You need to boot into the live cd for this.
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.
**FORGET THIS ONE**

---

### Post by dasunst3r on 2006-12-28
Windows XP Home unfortunately disables the administrator account, which is an absolute no-no in Linux (you can get the root account in Ubuntu back -- simply *sudo passwd root*).

I never saw putting an OS in a removable device as a good idea, and this is just why it's not a good idea.

---

### Post by bulldog on 2006-12-28
Did read the first post again and I think I misunderstood it the first time.
You boot from your internal disk and see GRUB but it gives an error,till you choose your USB drive.
GRUB is on the first drive with windows,only you haven't a windows entry in your menu.lst.
I will correct this and post your corrected menu.lst for you to copy it.
If you can give me the output of```
gksudo gedit /etc/fstab
``` to see how things are listed overthere.
This is how your menu.lst should be in my opinion
```
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=e18053e0-8c8c-4c9c-aa54-e902d798195e ro 
# kopt_2_6=root=/dev/sda1 ro

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
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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

## ## End Default Options ##


title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot

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
Copy this over yours and see if it works,but for you do so make a safety copy first ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

To find the UUID of your USB disk```
 ls /dev/disk/by-uuid -lh
```

---

### Post by ifthengoto on 2006-12-28
Here is fstab - 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e18053e0-8c8c-4c9c-aa54-e902d798195e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=07D3-091E  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=80C2F69090FA0800 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=e80a0b6b-5c3e-42c5-a91b-39f86b1b54a8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Thanks

---

### Post by bulldog on 2006-12-28
It sure would be nice if you put them between code tags so I can copy and paste them.
To do so open with [code] your fstab here and close with [code]with a / in front of the last code.

**EDIT:**
Well copy and paste the above menu.lst into yours [overwrite after you made the copy]and try to boot again.
If things go well you should  be able to boot windows and ubuntu.
I copied your UUID in the menu.lst as well so that's okay.

No guarantees of course.

---

### Post by ifthengoto on 2006-12-29
> **bulldog said:**
> It sure would be nice if you put them between code tags so I can copy and paste them.
To do so open with [code] your fstab here and close with [code]with a / in front of the last code.

**EDIT:**
Well copy and paste the above menu.lst into yours [overwrite after you made the copy]and try to boot again.
If things go well you should  be able to boot windows and ubuntu.
I copied your UUID in the menu.lst as well so that's okay.

No guarantees of course.

Bulldog, that works perfectly. Many thanks for taking the time to help a noobie. I will save this thread and try to figure out what you did.

Your comment re using the code tag is appreciated - will do next time.

I now have to figure out in the code how to display the grub menu a few more seconds as it goes really fast - like ubuntu!

---

### Post by bulldog on 2006-12-29
That one is easy,alter this section and set the number of seconds as you like.
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0<---This one is for which entry you will boot

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3<---This one is what you asked for,make it what ever you like

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu<---if you remove the # you won't even see your grub anymore
```

---

