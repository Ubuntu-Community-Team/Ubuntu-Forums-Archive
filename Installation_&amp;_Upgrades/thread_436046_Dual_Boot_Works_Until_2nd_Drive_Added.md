---
title: "Dual Boot Works Until 2nd Drive Added"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by hobie on 2007-05-07
I have a working Kubuntu/XP dual boot on a single drive.  I added a 2nd drive on IDE 2 as a slave and now GRUB can't load either OS (but GRUB itself loads).  Using the geometry command, I can see it has selected the new drive as hd0. Unplugging the new drive restores the normal functions.  
I read parts of the GRUB manual, but I am reluctant to experiment in case I really screw it up.  Do I need to install GRUB on the new drive? Or use the map command to swap drives?  It is unclear in the manual if changing the mapping is permanent, or if changes are not saved  to the GRUB config.
Thanks for any help.

---

### Post by bulldog on 2007-05-07
When you turn the computer on,you boot into GRUB as before?
If so,and your new hdd is seen as hd0,you have to edit the menu.lst.
If you can post your menu.lst to the forum,I can show you what to do.

---

### Post by hobie on 2007-05-07
Thanks for the offer. Here it is, minus the boilerplate:

[HTML]

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=77238a4e-b8bb-450e-8e71-30c9910d95e5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=77238a4e-b8bb-450e-8e71-30c9910d95e5 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=77238a4e-b8bb-450e-8e71-30c9910d95e5 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=77238a4e-b8bb-450e-8e71-30c9910d95e5 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=77238a4e-b8bb-450e-8e71-30c9910d95e5 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=77238a4e-b8bb-450e-8e71-30c9910d95e5 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


[/HTML]

---

### Post by bulldog on 2007-05-09
Copy this menu.lst over your old one,or edit it your self,and it should work again.
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=77238a4e-b8bb-450e-8e71-30c9910d95e5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=77238a4e-b8bb-450e-8e71-30c9910d95e5 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=77238a4e-b8bb-450e-8e71-30c9910d95e5 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=77238a4e-b8bb-450e-8e71-30c9910d95e5 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=77238a4e-b8bb-450e-8e71-30c9910d95e5 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=77238a4e-b8bb-450e-8e71-30c9910d95e5 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
chainloader	+1

```

If you're going to edit the menu.lst your self,just edit the (hd0,1) entry into (hd1,1) for all the lines,except your windows.
Edit the windows entry into (hd1,0)  but that's obvious I think.
Let me know if it works.

---

### Post by hobie on 2007-05-09
Thanks for your help.  Before I try it, I have one more question.  What happens if it doesn't work?  Is there any way to cause the machine to boot so I can edit it back again?

Hobie

---

### Post by hobie on 2007-05-11
Latest development is that I can no longer get back into GRUB, so I can't perform the changes suggested.  The only response I get when trying to boot is "Error loading OS".  I can't change the boot order of hard disks in the BIOS; it only allows Hard Disk or CD Drive.
Even if I swap the 2 hard dirves (Primary Master & Secondary Slave), the error is the same.
I think the only thing to do is to somehow get GRUB onto the new slave drive and have it redirect to the Master. Is this possible?  So far, it has an empty NTFS partition and an unused remainder.

---

### Post by bulldog on 2007-05-12
To reinstal GRUB you have to boot the live cd and perform these commands,
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next command 
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

This would install GRUB on the (hd0),but look for any error you get by installing it.

---

