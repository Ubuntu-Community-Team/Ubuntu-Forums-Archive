---
title: "grub-install not finding disk"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2007-04-03
I'm having trouble getting grub to boot to the xp partitition.

I've checked with fdisk and this is what I get
sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2550    20482843+  83  Linux
/dev/hda2   *        2551        5167    21013464+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/hda3            5168        6996    14691442+  83  Linux
/dev/hda4            6997        7296     2409750    5  Extended
/dev/hda5            6997        7296     2409718+  82  Linux swap / Solaris


I added the bottom to my menu.lst as such
title		Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-686 root=UUID=07D5-061E ro single
initrd		/boot/initrd.img-2.6.15-27-686
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title		XP
root		(hd0,1)
makeactive
chainloader	+1


but when I try to run grub-install as 

sudo grub-install /dev/hda
Could not find device for /boot: Not found or not a block device.

or

sudo grub-install /dev/hda1
Could not find device for /boot: Not found or not a block device.


can anyone tell me what I've done wrong ... has worked before!

Thanks

Jim

---

### Post by bulldog on 2007-04-03
It's the best thing to do to let windows use the first partition of a hdd,you set linux on that one.
But if this have worked before,who am I to question it.

To install or reinstall grub,you have to use (hd0) instead of hda,GRUB doesn't know what hda is.
The complete install is as follows,
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

---

### Post by mikewhatever on 2007-04-03
I am not quite sure what the command you used does. Try this how-to
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

