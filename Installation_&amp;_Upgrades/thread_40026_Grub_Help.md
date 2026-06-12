---
title: "Grub Help"
date: 2005-06-07
forum: Installation &amp; Upgrades
---

### Post by duffmckagan on 2005-06-07
I have installed the following Operating systems on my HDD.

1. Ubuntu Warty Warthog 4.10

2. Slackware 10.1

3. Simply Mepis 3.3

4. windows XP.

Each and every OS works fine. But, this was only upto I installed Ubuntu (it was installed last and failed to detect Mepis.)

It detected Windows, but it does not boot.

Here is my Grub menu.lst

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# root		(hd0,1)
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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option contols options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## ## End Default Options ##

title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda8 ro single
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Memory test
root		(hd0,7)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title		Linux (on /dev/hda7)
root		(hd0,6)
kernel		/boot/vmlinuz root=/dev/hda7 ro
savedefault
boot


```



I would like to know what should I modify in order to make Mepis and Windows running. ubuntu installation as such has no problems.

Here is the partitioning scheme of my Hdd, so that no info is missed out.

Hda1 Windows FAT32 (Primary partition)

hda2 Extended partition

hda5 Swap

hda6 mepis

hda7 slackware

hda8 ubuntu (This is also the order in which i installed the OSs.)

All Linux partitions are EXT3.


Plz Help.

---

### Post by jkndrkn on 2005-06-07
try rootnoverify instead of root in your windows entry
worked for me

---

### Post by spd106 on 2005-06-07
Hi, for Windows try adding makeactive as follows

rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1


for mepis you will need to mount the partition that contains it and find where the kernel image and initrd are kept. It should be in a similar place to ubuntu's.
Use the entry for slackware as a template but change the title, root, etc
somthing like this should work

title		Mepis3.3 (on /dev/hda6)
root		(hd0,5)
kernel		/boot/vmlinuz-<your-version> root=/dev/hda6 ro
initrd            /boot/initrd-<your-version> 
savedefault
boot 

Good luck

---

### Post by jerome bettis on 2005-06-07
you can edit /boot/grub/menu.lst (as root) and add these lines at the bottom to get a menu option for mepis.

title		Mepis (on /dev/hda6)
root		(hd0,5)
kernel		/boot/vmlinuz root=/dev/hda5 ro
savedefault
boot

and change root to rootnoverify in the windows section.

also if you're running a bunch of different distros on the same machine having shared boot and home partitions is a great idea.  not sure if you're doing that already though.

^ damn they beat me to it..

---

### Post by duffmckagan on 2005-06-08
Thanks for the reply all of you guys.


> also if you're running a bunch of different distros on the same machine having shared boot and home partitions is a great idea. not sure if you're doing that already though.

Actually, till now, I used to only Dual boot a Linux Distro with Windows.
But, I realised that the learning process had become too slow with that, and so, I did this.

I wasn't frankly knowing that we can share a common /boot. I would have tried that. Thanks. will do that next time.

I had opted for a common /home folder, but that gave me a lot of problems. There used to be a lot of conflicts with stuff residing there for different distros. Now, that I understood that i required a lot of tweaking, I did withdraw that idea.
Moreover, when I used to install Ubuntu last, then it would require me to format the /home partition, if not formatted, it would give me a warning, saying that it had some uncorrected errors, and if not formatted, the partition won't be used.

So,finally I made a /home partition in the root folder of each distro.

---

### Post by duffmckagan on 2005-06-08
This is my modified grub/menu.lst

I still can't boot into windows. Any ideas?

Mepis, Ubuntu and Slackware boot fine.

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# root		(hd0,1)
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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option contols options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## ## End Default Options ##

title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda8 ro single
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Memory test
root		(hd0,7)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title		Slackware 10.1(on /dev/hda7)
root		(hd0,6)
kernel		/boot/vmlinuz root=/dev/hda7 ro
savedefault
boot


title MEPIS at hda6, kernel 2.6.10
root (hd0,5)
kernel (hd0,5)/boot/vmlinuz-2.6.10 root=/dev/hda6 nomce psmouse.proto=imps quiet splash=verbose vga=791 
initrd (hd0,5)/boot/initrd.splash 
savedefault
boot

title MEPIS at hda6, kernel 2.4.29
root (hd0,5)
kernel (hd0,5)/boot/vmlinuz-2.4.29 root=/dev/hda6 nomce quiet splash=verbose vga=791 hdc=ide-scsi 
initrd (hd0,5)/boot/initrd.splash 
savedefault
boot

```

---

### Post by spd106 on 2005-06-09
Hi, can you mount the windows partition from linux? 

You need to check that the partition you set as root is the right one. It might be on (hd0,1).

Also try using variations of makeactive and rootnoverify. 

Are there any error codes produced by grub?

Look to the grub website for more info [http://www.gnu.org/software/grub](http://www.gnu.org/software/grub)

---

### Post by duffmckagan on 2005-06-09
[QUOTE=spd106]Hi, can you mount the windows partition from linux? 

You need to check that the partition you set as root is the right one. It might be on (hd0,1).

Also try using variations of makeactive and rootnoverify. 

Are there any error codes produced by grub?

Look to the grub website for more info [http://www.gnu.org/software/grub](http://www.gnu.org/software/grub)[/QUOTE]
 Oh yeah, I can mount the Windows Partition on my Ubuntu.

I do it this way.

sudo su
mount /dev/hda1 /mnt/windows

Does this mean that Windows resides on (hd0, 1)

I have noticed in the grub menu.lst, that if the slackware is on hda6, it is entered as 
(hd0, 5).

So, I thought that it would be a similar case for windows.

Yet, I will change it and post the results here.

Moreover, I don't get any error from Grub.
Grub just shows me the lines used to go to windows i.e. all the makeactive, rootnoverify stuff.
No error yet.

I will be back soon with the new results after changing from (hd0, 0) to (hd0, 1)

---

### Post by bored2k on 2005-06-09
[QUOTE=duffmckagan]Oh yeah, I can mount the Windows Partition on my Ubuntu.

I do it this way.

sudo su
mount /dev/hda1 /mnt/windows[/QUOTE]
That is not 100% right. Read [http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

---

### Post by duffmckagan on 2005-06-09
[QUOTE=bored2k]That is not 100% right. Read [http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)[/QUOTE]
 Is it damn compulsory that i should unmount a partition, that I have manually mounted?

Moreover, the partition was FAT32.

I will try unmounting too, and post the results.

I would also like to ask whether is it necessary to mount the windows partitions in exactly the same way as mentioned in the Guide?
I mean, the way i mount works fine for me.

---

