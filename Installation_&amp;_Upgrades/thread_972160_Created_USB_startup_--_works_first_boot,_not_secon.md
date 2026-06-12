---
title: "Created USB startup -- works first boot, not second"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by davidshere on 2008-11-05
I'm making a USB startup disk with and for Intrepid. I go to System>Administration>Create a USB Startup Disk.  It works fine and completes the task.  I reboot and the USB disk starts the first time, but when I try to boot it a second time, I get nothing.

I have started over several times, each time creating a new USB Startup Disk from scratch. On the latest one, the USB disk does not boot at all, even on the first try.  On one machine, it just freezes after I select it from the BIOS's boot menu.  On another machine, it gets to a screen that says 

```
SYSLINUX 3.63 Debian-2008-07-15 CBIOS Copyright (C) 1994-2008 H. Peter Anvin
boot:
Could not find kernel image: linux
boot:
```
(I pressed enter at the first "boot:" prompt.)

I have a 4GB Sandisk Cruzer Micro.  I've tried removing all partitions first with Partition Editor, then formating with the Create a USB Startup Disk utility.  I've tried creating a partition with Partition Editor and formating it to FAT32, then running the Create a USB Startup Disk utility.  

I'm going to try again from scratch and see what happens.  Any suggestions would be greatly appreciated.

---

### Post by C.S.Cameron on 2008-11-05
I have had problems installing to a 4G Kingston.
I made a 1G Fat32 partition on the disk (on the left side in gparted).
unplugged the flash drive, plugged it back in and ran Create a USB Startup Disk from the CD.
This worked for me ok.
Made persistence partitions on the rest of the disk.

---

### Post by zwygart on 2008-11-05
Your problem is probably syslinux.
If you have a ext filesystem use extlinux
[http://syslinux.zytor.com/wiki/index.php/The_Syslinux_Project]("http://syslinux.zytor.com/wiki/indx.php/The_Syslinux_Project")
type [www.syslinux.com](www.syslinux.com) in the browser.

If not then type kernel with the correct path to the kernel.
On the link wich I gived it is explained how to do.
You will may be have to edit the configuration file (syslinux.cfg at root or in /boot or /syslinux or /boot/syslinux)
Take a look at the page.


Personnally I prefer GRUB, but syslinux, extlinux can do the job.

If you have problems post back.

---

