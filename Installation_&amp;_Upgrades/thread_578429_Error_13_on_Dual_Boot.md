---
title: "Error 13 on Dual Boot"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by mrvertigo on 2007-10-17
grub cant find my windows partition....... help!!!!!

ok, heres my drive readouts

> Quote:
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 9313 74806641 7 HPFS/NTFS
/dev/sda2 * 9314 9726 3317422+ 83 Linux

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 10199 81923436 7 HPFS/NTFS
/dev/sdb2 10200 10454 2048287+ 5 Extended
/dev/sdb3 10455 19452 72276435 83 Linux
/dev/sdb5 10200 10454 2048256 82 Linux swap / Solaris
and my config looks like

> 
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other Operating Systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Home Edition
rootnoverify (hd1,1)
savedefault
map (hd0) (hd2)
map (hd2) (hd0)
makeactive
chainloader +1
I have little to no idea what any of this means or why i'm getting an error 13 but you guys always seem to be friendly enough,

---

### Post by logos34 on 2007-10-17
if you just have the two hard disks, then try this:
[B]
gksudo gedit /boot/grub/menu.lst[/B]

change windows entry to this:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Home Edition
rootnoverify (hd1,**[COLOR="Red"]0[/COLOR]**)
savedefault
map (hd0) (hd**[COLOR="Red"]1[/COLOR]**)
map (hd**[COLOR="Red"]1[/COLOR]**) (hd0)
makeactive
chainloader +1

---

### Post by mrvertigo on 2007-10-17
I have changed my config to read
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Home Edition
rootnoverify (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

still error 13, I dont get it.................... i'm pulling my hair out on this one!

pre-emptive thanks

---

### Post by Pumalite on 2007-10-17
[http://users.bigpond.net.au/hermanzone/p15.htm#13](http://users.bigpond.net.au/hermanzone/p15.htm#13)

---

### Post by chunchengch on 2007-10-17
post here the complete menu.lst for more useful help.

---

### Post by confused57 on 2007-10-17
You might also try giving the Super Grub Disk a try:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by logos34 on 2007-10-18
If you can boot windows with supergrub disk, then you know the problem is with the grub config files.

Maybe the installer got the wrong ntfs partition...is sda1 your windows system C: drive?  You could try:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

You will also have to flag sda1 as 'boot' (*) using Gparted/Gnome partition editor

>rmenu>Partition>manage flags>check boot box

OTH if you're sure sdb1 is the right one, it may be that /boot/grub/device.map is wrong

---

### Post by mrvertigo on 2007-10-18
I ended up doing a fresh install this fixed my issue ONLY AFTER I disconnected the non sata drive!!!!!

---

