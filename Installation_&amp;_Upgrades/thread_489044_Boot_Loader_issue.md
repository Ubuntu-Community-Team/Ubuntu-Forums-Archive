---
title: "Boot Loader issue"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by Turboaaa2001 on 2007-06-30
Heres a fun one (hopefully easy). In hopes of showing off my linux box I was preparing to move the 30 - 50 pound unit. I ended up having time left over to start phase 2 of my project, I figured I could show that off as well.

Heres the plan I had:

Phase 1
a. Wipe 150GB SATA HD.
b. Install Ubuntu Fiesta on first half of HD w/ 2GB SWAP.
c. Get desktop and drivers working and be online.
d. Enjoy doing everyday Office and internet tasks.

Phase 2
a. Install Windows XP Pro on second partition.
b. Get drivers, updates, anti virus, and gaming software installed.
c. Install my latest games.

I completely forgot the part about Windows having it's own boot loader and that it doesn't like to share. I believe GRUB is used by default in a DEBIAN based distro such as Ubuntu so I need to know how to get it back on the boot sector!

Of course I was very embarrassed when I got to my destination and all I had was XP. Thankfully the guys understood it was not Linux's fault (their Windows and one MAC user) but my own temporary ignorance.

---

### Post by confused57 on 2007-06-30
You can reinstall grub, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Then you'd need to add an entry to boot Windows on the 2nd partition:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

add your Window's entry to the very end of the menu.lst file:
```
title   Windows XP Pro
root  (hd0,1)
savedefault
makeactive
chainloader +1
```
quit & save

---

### Post by Turboaaa2001 on 2007-07-16
I know this reply is long over due but I've been very busy.

I followed the steps in the link from the previous post, but adding XP to the OS list did not work. Of course it lists  XP as an option (from the code "title Windows XP Pro") but I get an error saying that it cannot load the OS. I know the filesystem is intact and I have made no changes to it since .

Here is my partial menu.lst file:

> 
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9563bcb9-539f-4528-beed-89c46ff47e2b ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9563bcb9-539f-4528-beed-89c46ff47e2b ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9563bcb9-539f-4528-beed-89c46ff47e2b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9563bcb9-539f-4528-beed-89c46ff47e2b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP Pro
root		(hd0,1)
savedefault
makeactive
chainloader +1


Please help. I cannot seam to get Outpost2, FF7, or Rome Total War (I figured the last one wouldn't work) to run right. So I need:mad: XP for that.

---

### Post by confused57 on 2007-07-17
Windows can be difficult to boot from grub, if it's physically located on a partition after the Ubuntu partition...you could try this entry:
```
title   Windows XP Pro
rootnoverify  (hd0,1)
makeactive
chainloader +1
```

You can always restore Window's IPL to the mbr by booting up the Window's install cd, press "r" for recovery mode, then enter the command FIXMBR.

I would suggest you try the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

First, I would see if it will boot Windows with your current setup of grub on the mbr...if not, then maybe do the FIXMBR and see if SGD can boot Ubuntu with Window's IPL code on the mbr.

---

