---
title: "Grub, Ubuntu &amp; Windows - a diffult coexistence?"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by furghella on 2006-08-12
I have tried twice now to install Windows XP and Ubuntu on my PC. I have two hard drives. I have installed Windows XP first, and then Ubuntu. Each time I installed Ubtuntu I was unable to boot Windows XP. Grub is being installed (I believe), but it doesn't give me the option of booting into Windows.

Is there a way to get Windows back? 

Thank you for your support.

---

### Post by Inkyskin on 2006-08-12
Are you sure you didnt overwrite windows instead?

---

### Post by furghella on 2006-08-12
Yes, I am sure of that. I can see the Windows disk from Ubuntu, but I can't open it.

---

### Post by Tomosaur on 2006-08-12
Post your /boot/grub/menu.lst file up here please.

---

### Post by furghella on 2006-08-12
Sorry, but how do you do that?

---

### Post by Tomosaur on 2006-08-12
Open up a terminal, and type 'gedit /boot/grub/menu.lst

Copy the contents and paste onto here.

---

### Post by confused57 on 2006-08-12
Since you have 2 hard drives, and if you can't get your current setup working, you might want to consider this option:

[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

```
cat /boot/grub/menu.lst
```

Tomosaur, didn't realize your command would do the same thing as "cat", to display the file,  learn something new every day.
Edit:  I hope you didn't think I was implying you didn't know about "cat", I was just commenting I wasn't aware that "gedit"(without the sudo) would do the same thing, although it stands to reason it would.

---

### Post by furghella on 2006-08-12
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
# kopt=root=/dev/sda1 ro

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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Tomosaur on 2006-08-12
Yeah, Grub isn't detecting Windows at all there.
Do you know which partition it is installed into?
EDIT: Confused, I know what cat does, but copying from the terminal is often confusing for newbies.

---

### Post by furghella on 2006-08-12
Mmh - I am sure I have seen that, but I have no idea how to find that out again...

---

### Post by Tomosaur on 2006-08-12
Type 'sudo fdisk -lu' into a terminal and copy and paste the results up here then, please :)

---

### Post by confused57 on 2006-08-12
> **furghella said:**
> Mmh - I am sure I have seen that, but I have no idea how to find that out again...

Until Tomosaur gets back, you can enter in a terminal:

```
sudo fdisk -l
```
The -l is a small "L".

This will show your partition table.

You might want to read over the link I gave earlier, you might need a Windows entry similar to that in your menu.lst.

Tomosaur can probably give you some more detailed instructions.

Edit: My reply was a little late, looks like Tomosaur has everything under control...don't want to barge in.

---

### Post by furghella on 2006-08-12
Thank you very much to zou all, folks. Here is the dump:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   389222819   194611378+  83  Linux
/dev/sda2       389222820   390716864      747022+   5  Extended
/dev/sda5       389222883   390716864      746991   82  Linux swap / Solaris

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   160810649    80405293+   7  HPFS/NTFS
ffurger@ffurger-desktop:~$

---

### Post by sebbe1991 on 2006-08-12
Add this to your menu.lst
```

title Windows XP
	root (hd1,0)
	makeactive
	chainloader +1
	boot

```

---

### Post by confused57 on 2006-08-12
Here's a thread with someone with a similar setup as yours, may or may not work with your system:
[http://www.ubuntuforums.org/showthread.php?t=229909&page=3](http://www.ubuntuforums.org/showthread.php?t=229909&page=3)

---

### Post by furghella on 2006-08-12
Ok, thank you. I tried to do that, but Ubuntu won't let me save the modified menu.lst file. Don't have the privileges for that. How do I get around that?

Sorry folks, I realize this is all silly to you, but not to me :-)

---

### Post by Tomosaur on 2006-08-12
Alright well, your NTFS (Windows) partition/disk seems to be intact, but it isn't set to bootable. I am not 100% sure whether this is essential to get Windows to boot from Grub, but my Windows partition is set to bootable, and I have no trouble booting at all, so we'll set yours to be bootable, and give it an entry in Grub.

First of all, you need to input the following command into a terminal:
```

sudo parted -i /dev/sdb

```

At the parted prompt, type the following:
```

set 1 boot on

```

This will give your windows disk a bootable flag. Type 'print' to make sure  it's set properly. Type 'quit' when you're done.

Now, on my system, I DON'T have the linux partition set to boot, and I can boot just fine, so we'll set yours the same way. Type the following:
```

sudo parted -i /dev/sda

```

Now type 'set 1 boot off'
Then type 'quit'.

Now your disks should be set up properly to boot, you just need to give Grub a windows entry in it's menu. Type 'gksudo gedit /boot/grub/menu.lst'
and paste the following into it right at the end of the file:

```

title		Windows XP
root		(hd1,0)
savedefault
makeactive
chainloader	+1

```

Save the file, and reboot. Hopefully, grub will now display a Windows entry at the bottom of its list. Try booting from it, and let us know how it goes :)

---

### Post by sebbe1991 on 2006-08-12
> **furghella said:**
> Ok, thank you. I tried to do that, but Ubuntu won't let me save the modified menu.lst file. Don't have the privileges for that. How do I get around that?

Sorry folks, I realize this is all silly to you, but not to me :-)

use 
```
gksu gedit /boot/grub/menu.lst
```

---

### Post by confused57 on 2006-08-12
I believe you'll need the mapping commands to boot Windows with your system:

```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

---

### Post by furghella on 2006-08-12
mmh - something did change - now I get an error message:

"NTLDR is missing
Press Ctrl+Alt+Del to restart"

Any thoughts?

---

### Post by Tomosaur on 2006-08-12
Sounds like a windows error message to me. It's possible that your windows boot files have gotten messed up. [This page](http://www.computerhope.com/issues/ch000465.htm) may be of some use to you.

---

### Post by furghella on 2006-08-12
You guys are amazing - yes, earlier I did fool around with the Windows XP installation disk, but I wouldn't have thought anybody could tell me exactly what to do about this error. I am going to follow the instructions there and let you know. In the meantime thank you so much to everybody for their wonderful help, I have really appreciated that.

Franco

---

### Post by Tomosaur on 2006-08-12
Heh, that's why we're here :P
Hope you get your problem sorted.

---

### Post by furghella on 2006-08-12
Ok, it looks like I can't fix the problem in Windows. The Recovery Mode didn't let me write new ntflr files onto the boot disk, and "fixboot" and "fixbmr" (or something like that) didn't make any difference.

Now, one last question: If I go ahead and re-install Windows, am I messing up the Ubuntu installation, by any chance?

---

### Post by Tomosaur on 2006-08-12
Nope, but you will lose Grub, because Windows will overwrite the MBR. You will need to reinstall Grub yourself, there's a howto on the forum somewhere.

---

