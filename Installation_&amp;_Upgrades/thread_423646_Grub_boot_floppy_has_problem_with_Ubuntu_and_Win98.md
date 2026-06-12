---
title: "Grub boot floppy has problem with Ubuntu and Win98"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by fable on 2007-04-26
I have a P4 machine with Ubuntu installed in Primary master drive and Win98 installed in Primary slave drive.  I can use BIOS boot sequence to switch betwen the two Operating Systems.  Both hard disks boot fine.

I want to learn about using Grub to dual boot between the two operating systems.  I was able to build a Grub boot floppy and get the Grub prompt.  I tried some Grub commands and the boot floppy seems to work fine.

Before I created a menu.lst, I decided to test  the Grub boot floppy by manually entering Grub commands to boot either Ubuntu or Win98. 

I was successful in booting Ubuntu by manually entering Grub commands.  The sequence of Grub commands I used to boot Ubuntu successfully is as follows:

```
grub>  root  (hd0,0)
grub>  kernel  /vmlinuz-2.6.15-28-396  root=/dev/mapper/Ubuntu-root  ro  quiet  splash
grub>  initrd  /initrd.img-2.6.15-28-386
grub>  boot
```
Unfortunately the PC hung every time I tried to manually boot Win98 using the following sequence of Grub commands:

```
grub>  rootnoverify (hd1,0)
grub>  makeactive
grub>  chainloader +1
grub>  boot
```
Is the sequence of commands above incorrect for booting Win98?  Why did the PC hang after the boot command?

:confused:

---

### Post by Herman on 2007-04-26
Try these and see if they will work,
```

root        (hd1,0)
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
boot
``` Since you would have the FAT32 filesystem in Windows 98, you can use the 'root' command instead of 'rootnoverify', which is for NTFS partitions. I'm not sure if that's very important though, I don't think it makes much difference.
Something that will make a difference is the pair of 'map' commands, to trick Windows into thinking it's on the first hard disk. That is needed whenever Windows is on a non-first hard disk.

---

### Post by fable on 2007-04-26
Thanks for the excellent instructions.  The map commands did the trick as Herman suggested.  I can now boot Win98 using the Grub boot floppy without any problem.

:)

---

### Post by fable on 2007-04-26
After I manually tested the Grub commands for dual boot between Ubuntu and Win98, I created a menu.lst file with the manual commands I tested.  I copied  the menu.lst file to the Grub boot floppy.  Now every time I boot I can select the operating system using the Grub menu.

My simple menu.lst file contains the following commands:

```
title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,0)
kernel		/vmlinuz-2.6.15-28-386 root=/dev/mapper/Ubuntu-root ro quiet splash
initrd		/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-28-386 root=/dev/mapper/Ubuntu-root ro single
initrd		/initrd.img-2.6.15-28-386
boot

title		Windows 98
root		(hd1,0)
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
boot
```

---

