---
title: "XP nor Ubuntu will boot!"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by ubuntoexpert on 2008-03-16
My machine is a Sony Vaio Laptop PCG-FXA36 and I have both XP and Ubuntu installed. However, I cannot boot either OS now.

I was in the middle of backing up my files and I was running out of hard drive space so I used Partition Magic 8.0 to resize my partitions (which had errors in the middle of the operation and did not complete it) and I think that screwed up my MBR.

I've been receiving a Grub Loader Error 17 ever since, which I bypassed by using an XP 3.5 boot disk to boot up my XP OS and worked. However, I moronically, used Partition Magic's PTBooter (?don't remember the name now?) to boot my Linux system and that's when both OS's became unbootable.

It looks like it's going to boot and then it goes to the blue chkdsk screen and says that autochk is not available or something. After that the systems restarts with absolutely no difference.

Also, my CDrom is busted and not working and my BIOS doesn't seem to indicate it can boot from a USB drive. So I feel like I'm up a creek!

I am backing up my files in order to transfer them to an upgraded computer and need to access the rest of my files off of XP AND Ubuntu as soon as possible. And buying a $200 CDrom for this laptop is out of the question! If there is anything you can offer in terms of help, it would be GREATLY appreciated! And please let me know what other necessary information I can provide for you.

---

### Post by thinkdez on 2008-03-17
Wow sounds like your system is really screwed.  It would be nice if you could boot a live CD to just recover the data and be done with it but since your system seems to be dead.  I have two options for you to boot to recover your data.

1.  Use a Floppy disk to boot the system off of a USB disk.  Once this is done you can recover your data to a USB Hard Disk or across the network to your new system etc.
[http://www.pendrivelinux.com/2007/11/21/use-a-floppy-to-boot-usb-pendrive-linux/]("http://www.pendrivelinux.com/2007/11/21/use-a-floppy-to-boot-usb-pendrive-linux/")

2. Purchase a laptop to IDE adapter [provided you have a Desktop to plug it into] and boot up a live CD.  From there you can recover your data and move it to the new system.

I hope this helps you out.  With Option 1 you could possible save the existing system but if your migrating the data anyway you might as well just recover the data and do a fresh install to save the time, although I do find learning to recover from such disaster can be a rewarding and educational experience so if you have the free time I would go that route.  The biggest issue is your dead hardware.

Good Luck

---

### Post by Sef on 2008-03-17
This is what GRUB Error 17 is

> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Partition Magic tends not to play nice with GNU/Linux.   I have an idea that could work, if your Sony has a working usb port and your computer can boot from a usb port.  Download [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/?section=download") which can booted from a usb port.

---

### Post by Pointswest on 2008-03-18
I agree with Sef the Super grub should repair the MBR or boot to either win or linux.  I have used this from a cd to correct boot problems with grub.  Just boot from the cd or usb that has Super grub.  G-parted seems to be a better partitioning program for linux.

Pointswest

---

