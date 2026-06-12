---
title: "Double HD boot, Gutsy and XP"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by dfarce on 2008-01-18
Hello, I have a few questions regarding grub. 
Right now, I have two 250GB sata drives and one 30GB IDE drive that is hooked up with an IDE->Sata connector in my system. I am running XP on one 250, data and backup on the second 250, and I am going to repartition and install Gutsy on the 30 Gb drive. 

When I install, if I am going to configure grub to list XP and Ubuntu, do I just have to install grub to the MBR of the 30GB drive, and leave the MBR of the XP drive untouched? Then set my motherboard to boot from the 30 GB drive only. Will this work? Because i want to be able to boot back to XP if something goes screwy with my linux installation or GRUB on the small drive.

Thanks

---

### Post by logos34 on 2008-01-18
> **dfarce said:**
> When I install, if I am going to configure grub to list XP and Ubuntu, do I just have to install grub to the MBR of the 30GB drive, and leave the MBR of the XP drive untouched? Then set my motherboard to boot from the 30 GB drive only. Will this work? Because i want to be able to boot back to XP if something goes screwy with my linux installation or GRUB on the small drive.

Set the 30 gb IDE drive first in the Bios hard disk boot priority.  Install.  If you're using the live cd to install, you will come to a 'Ready to install' screen.  Click 'Advanced' button lower-right, then replace '(hd0)' with

/dev/sda

or whatever the 30 gb ide is designated.  That will put grub on the mbr of that drive.  The default (hd0) would probably work, but doing it this way will assure that it goes on the correct disk. 

Grub usually does a good job of detecting windows and getting the configuration right, so you should be able to boot XP as well from the grub menu.

---

### Post by dfarce on 2008-01-19
Ok, thanks for the tip. 

Now, one problem, the small drive shows up in windows (the FAT partition, I had a persistent install on it previously) but it doesn't show up under ubuntu. I use fdisk -l and it only lists the two 250GB drives. Any clues of why it isn't showing up? It may be because of the IDE>SATA converter, and for some very strange reason, ubuntu doesnt recognize it. Any ideas?

---

### Post by logos34 on 2008-01-19
check 
[B]
sudo cfdisk [/B]

and

**sudo lshw **(look under IDE>volume, or SCSI)

---

### Post by dfarce on 2008-01-19
ok, for some reason all i needed to do was try loading the liveCD a few more times and the hard drive was detected properly, weird. Anyways, I installed grub the way you said, changing from hd0 or whatever for /dev/sdc. However, Grub doesn't boot any operating systems. The good news, however, is that just as I hoped, I can just change my boot order and bypass grub altogether and get back into XP for trouble shooting. so here is what is said under the grub menu.lst file for what the boot options are. 
## ## End Default Options ##

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=49d6d09c-3c40-4373-9469-ca8fbe2ed5f4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=49d6d09c-3c40-4373-9469-ca8fbe2ed5f4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1


```

My bootable windows drive, is /dev/sda(1) and the ubuntu drive, is /dev/sdc (not sure partition number, left that up to ubuntu) That is as far as I know, the windows drive *might* be sdb, but I doubt it. 

I'm looking up what to edit the grub menu to, but if you could give me it here it would save a loot of looking :p

---

### Post by logos34 on 2008-01-19
Did you set the ide drive first in the Bios boot priority BEFORE installing ubuntu, as I said?  Either you forgot or the ide-sata converter is causing some mischief.  Because grub and the ubiquity installer saw it as third in the bios order.

Anyway, just boot to grub, highlight the ubuntu kernel and press 'e' to edit...change 'root' line to (hd**0**,0).  Then 'enter' and 'b' to boot.  If it works make the change permanent in menu.lst.  (don't forget to change 'groot' line too.)

gksudo gedit /boot/grub/menu.lst

---

### Post by dfarce on 2008-01-20
I'm one step ahead of you, two actually. I figured out out that the ubuntu drive needed to be set to hd0 by trial and error, and changed grub accordingly. This is what the important part of my grub menu looks like:
```
title		Normal OS:
root

#developement branch
title		Ubuntu Hardy
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-4-generic root=UUID=49d6d09c-3c40-4373-9469-ca8fbe2ed5f4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-4-generic
quiet

#Windows XP
title		XP Pro
root (hd1,0)
savedefault
makeactive
map (hd1,hd0)
map (hd0,hd1)
chainloader	+1

```

You'll notice that the distro is Hardy, thats because I had to upgrade to the release candidate due to a weird LCD resolution problem. Anyways, windows will still not boot. Even after the changes to the boot menu. see any problems? The bootable drive IS the second sata drive listed in the boot order, so I don't see why it doesn't work.... WAIT, the bootable partition may be the second on the drive, do i avfe to and how do I configure grub to boot from the second partition?

---

### Post by logos34 on 2008-01-20
you have a typo (parentheses, etc):

> map [COLOR="Red"](hd1,hd0)[/COLOR]
map [COLOR="Red"](hd0,hd1)[/COLOR]

It should be:
> 
#Windows XP
title		XP Pro
root (hd1,0)
savedefault
makeactive
map **(hd0) (hd1)**
map **(hd1) (hd0)**
chainloader	+1


For map commands to work right sometimes you also need to change /boot/grub/device.map to reflect the new disk order--i.e. the windows drive, sda, is now (hd1):
> 
(hd0) /dev/sd? -->linux 
(hd1) /dev/sda -->windows
(hd2) /dev/sd? -->storage

check **sudo fdisk -l **to make sure windows is on fact on the first partition

---

### Post by dfarce on 2008-01-23
Ok, I don't know whats wrong. Heres what my menu file says:

```
title		Normal OS:
root

#developement branch
title		Ubuntu Hardy
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-4-generic root=UUID=49d6d09c-3c40-4373-9469-ca8fbe2ed5f4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-4-generic
quiet

#Windows XP
title		XP Pro
root (hd1,0)
savedefault
makeactive
map (hd0)(hd1)
map (hd1)(hd0)
chainloader	+1
```

and my device file says this:

```
(hd0)	/dev/sdc
(hd1)	/dev/sda
(hd2)	/dev/sdb
```

The linux drive is for sure sdc, the data drive for sure is sdb, and windows for sure is on the first partition of sda. I get an error 11: invalid device string, when i try to boot into windows from grub, if thats any help.

The one thing that I can think of is this: I installed ubuntu and grub with the devices in boot order of sda/sdb/sdc, but to boot from grub I need to switch that to sdc/sda/sdb, maybe something to do with grubs initial configuration? Thanks for the help on this, but while I have someone who can, would you like to give me some help with installing a soundfont for timidity?

---

### Post by logos34 on 2008-01-23
If it's a syntax error somewhere. I can't spot it.

Not sure what's wrong.

---

### Post by dfarce on 2008-01-27
found the problem, and ran into another :-? It turns out that in the map lines, (hd0) and (hd1) had to be two spaces apart where I only put one. Small error, but at least its fixed now. Now, however, I have what looks like a bigger problem. I get the windows loading screen for about a second, and then it blue screens. No really important message either. Just that there has been an error and that windows needed to be shut down. I am guessing that this is because of the fact that grub boots to the windows hard drive mbr which then boots windows. its kinda of annoying though, im so close now. any ideas? all my searching for a solution has been inconclusive as of yet.

---

