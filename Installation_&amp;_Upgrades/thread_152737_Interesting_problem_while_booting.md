---
title: "Interesting problem while booting"
date: 2006-03-30
forum: Installation &amp; Upgrades
---

### Post by Coldie on 2006-03-30
Hi guys,

I installed the Breezy Badger on an external USB-drive (...and yes I read some threads about it!) . This drive is /dev/sdc and my actual linux partition is /dev/sdc1. Booting itself seems to work. So I can see the graphical Ubuntu loading image. But while loading the modules something seems to fail. So here is the message I get:
```

Booting 'Ubuntu, kernel 2.6.12-9-amd64-generic Default'
kernel direct mapping tables upto ffff810100000000 @ 8000-c000
root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz root=/dev/sdc1 ro quiet splash
 [Linux-bzImage, setup=0x1c00, size=0x13e30e]
initrd /boot/initrd.img
 [Linux-initrd @ 0x3faf0000, 0x4ef0d1 bytes]
savedefault
boot
.
Decompressing Linux...done.
Booting the kernel.
Loading, please wait...
FATAL: Module unknown not found.
mount: Mounting /dev/sdc1 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesn't have /sbin/init


BusyBox v1.00-pre10 (Debian 20040623-1ubuntu22) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned of
#

```
I had to include some modules into the boot image to enable ubuntu booting from an usb-hdd, but at the point when the error occurrs, ubuntu should have left this point behind.

So what did I wrong and why did I mess up with my system ;) 

best regards,
Daniel

---

### Post by TheNewGuy on 2006-03-30
if your root filesystem is on a drive that is connected via usb then you'll need to compile the kernel with usb support and usbfs support. I'm not really familiar with the kernel modules you'll need to compile in directly but someone will.

The reason your current setup isn't working is pretty simple. You are booting to a drive that is locatated on a usb connection but you dont have usb drivers built into the kernel (makes it kinda hard to get at the usb modules).

Dan

---

