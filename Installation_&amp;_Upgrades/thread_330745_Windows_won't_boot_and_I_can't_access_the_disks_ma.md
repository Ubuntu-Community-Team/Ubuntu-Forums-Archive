---
title: "Windows won't boot and I can't access the disks manager"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by turtlepaul on 2007-01-03
Ok, I'm new to Linux and I don't really know what I'm doing so much, so bear with me. I just installed Ubuntu yesterday from the cd and everything seemed to have gone fine. Then, when I tried to boot Windows XP next time I booted up my computer, I couldn't! It just displays "Starting up..." I left it for over an hour hoping that it was just being slow, but still no luck. Hoping to retrieve the information on the Windows partition(thankfully it wasn't too much) that I hadn't backed up yet (stupid me for not backing it up before trying ubuntu) I went to ubuntu Help. It said I can access my windows partition if I go System-->Administration-->Disks. There is no "disks" under Administration! Can someone help me?

---

### Post by bulldog on 2007-01-03
If you can give us the outcome of ```
sudo fdisk -l (l as in like)
```
And if you do,this one as  well```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by turtlepaul on 2007-01-03
Um... what do I do with that code exactly?

---

### Post by bulldog on 2007-01-03
Hit ALT+F2 and type in the box gnome-terminal.
In this terminal copy paste a command and copy the output on the forum,then copy paste the other and do the same.

---

### Post by turtlepaul on 2007-01-03
out put of first one:
> Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9010    72372793+   7  HPFS/NTFS
/dev/hda2            9011       19269    82405417+  83  Linux
/dev/hda3           19270       19457     1510110    5  Extended
/dev/hda5           19270       19457     1510078+  82  Linux swap / Solaris

the second one brought up a warning and the following in another window:
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
# kopt=root=UUID=7500e8a7-b9cb-49f9-a403-eb009da7475d ro
# kopt_2_6=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


---

### Post by bulldog on 2007-01-03
The warning is of non importance.

I can see nothing wrong with the menu.lst and the entry's,they all pointing to the according partition and so it should work.

Did you get any kind of error message from windows in the past?

It seems there something wrong with the windows boot.
I have to go for now,but will be back in about 18 hours.

---

### Post by Bartender on 2007-01-03
turtle -
Don't panic.  It sure looks like Windows is still there.  You didn't overwrite it.  At this point, probly the worst thing is you may have to fix the Windows MBR and re-install Ubuntu or just GRUB.  
bulldog is pretty sharp with this stuff, so I'd wait unless someone comes along who knows what to do...

---

### Post by turtlepaul on 2007-01-04
Ok thanks. I'll be waiting for a reply then.

---

### Post by turtlepaul on 2007-01-04
Um... Can anyone else please explain to me why my Windows won't boot and why I don't have a disks manager?

---

### Post by confused57 on 2007-01-04
> **turtlepaul said:**
> Um... Can anyone else please explain to me why my Windows won't boot and why I don't have a disks manager?
You can try editing your /boot/grub/menu.lst file and change the line with:
root (hd0,0)
to
rootnoverify (hd0,0)

Also, if you want to access your Windows partition from Ubuntu:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)
You can mount your Windows partition and copy over any files from Windows to Ubuntu.  The directions are for the live cd, but it works with an installed Ubuntu, also.

If you want to restore your Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

If you want to try reinstalling grub to the mbr:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

You could also try booting Windows with the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Hopefully, the rootnoverify will work...at least you have some options.

---

### Post by macguy918 on 2007-01-05
This is obviously a common problem.  I have a Windows XP Home installation and just installed Ubuntu from the downloadable iso image.  The Ubuntu installation went fine and I can boot into Ubuntu without any trouble.  What I can't do is boot into my Windows XP installation at all.

When I try to boot into Windows it just quickly cycles back to the grub menu.  On subsequent attempts to boot into Windows I tried to boot into safe mode but the same problem occurs.

I can see the Windows partition (see the fdisk results below) but can't make it boot.

billd@ubuntupc:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7742    62187583+   7  HPFS/NTFS
/dev/hda2            7743        9644    15277815   83  Linux
/dev/hda3            9645        9729      682762+   5  Extended
/dev/hda5            9645        9729      682731   82  Linux swap / Solaris
billd@ubuntupc:~$ 



I would hate to reinstall Windows XP and I would hate to lose my Ubuntu installation after spending all afternoon getting it set up.

Any suggestions would be much appreciated.

Thanks

:(

---

### Post by bulldog on 2007-01-05
You both can try and reinstall the windows bootloader with the windows install disk.
Boot from it and let it run till you get three options.
1/Install windows
2/Repair a windows
3/Exit
Choose option two and you will be taken to the recovery console.
Choose your windows install,mostly 1,and provide the administration password.
Then type fixboot  and after that fixmbr
You'll get a warning but proceed after that exit the disk and try to boot into windows.
If windows boot again,exit and boot the ubuntu live cd and open a terminal.
Enter the next commands into the terminal and your GRUB is installed again.
This will get you a grub> prompt 
```
sudo grub
```
This will return a location which you have to use in the next command.
```
find /boot/grub/stage1
```
Enter the location given by the previous command in the next command. 
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

---

### Post by macogw on 2007-01-05
If you installed Edgy (6.10) that's why there's no Disks Manager.  It was in Dapper (6.06) but disappeared after that (I, for one, am in favour of its return).

---

### Post by turtlepaul on 2007-01-06
Do I need the same Windows install disk I originally used, or can I use another one? I lost my original a long time ago but have another one. I've never used it though.

---

### Post by Bartender on 2007-01-06
turtle -
As long as it's a genuine Windows CD (or a copy of one) and it's the same OS as the one you have now, you can use bulldog's directions.
There's a lot of confusion over Windows CD's.  Microsoft wants you to think the CD's are magic or something, and the CD knows what PC it was used on.  As long as you have a valid key code it doesn't frikkin matter. 
 
Even the key code doesn't matter until you check in with MS for updates.

There are lots of fixmbr websites.  Check out a couple of them and read them thru.  I find it helpful when a couple of different sources say the exact same thing.

---

