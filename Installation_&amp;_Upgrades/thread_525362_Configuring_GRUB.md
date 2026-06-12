---
title: "Configuring GRUB"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by omgblackice on 2007-08-14
I have 2 hard drives, hda and hdb
hda has windows installed (primary boot)
hdb has linux installed (slave)

GRUB is installed on hda

I plan to reinstall windows, so I'm going to use this program called DriveScrubber in which it'll wipe all the information on hda, and it would also remove GRUB, which is the problem.

I tried to boot hdb in BIOS, but only a little blinking underscore appears and it does not boot.
So the problem is how do I boot my linux on hdb? or how do I format hda without having to format ubuntu on hdb (because it doesn't boot).

Thanks

---

### Post by bulldog on 2007-08-14
Just reinstall GRUB from the live cd.
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
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
Grub will be installed to the mbr of the hdd which contains Ubuntu.
If you do it this way,set the hdb as master boot device and your windows as the slave drive.
Map your windows in menu.lst like this,and you never have to worry again when you want to reinstall ubuntu or windows.
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

