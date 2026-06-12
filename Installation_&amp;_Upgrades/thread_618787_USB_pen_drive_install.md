---
title: "USB pen drive install"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by klange on 2007-11-20
Ok, so I have Ubuntu 7.10 installed on my 2gb USB stick as per the instructions at [PenDrive Linux](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/). I have no idea if the installation itself is set up properly, because I have no way to directly boot from it (technically, I could stick it in my laptop, but I'm too lazy). Anyway, my desktop won't boot directly to my USB stick, so instead I'm using a Grub floppy to boot it.
It does, technically, boot, however I get stuck on ASH with the "(initramfs)" prompt, and the file system isn't very complete, so I don't think I've got it quite right.
I'm currently using the following commands for grub:
```
root (hd1,0)
kernel /vmlinuz root=/dev/sda1 rw 
initrd = /initrd.gz
boot
```
Anyway, I get the following error messages before it pops into BusyBox:
```
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory.
mount: Mounting /proc on /root/proc failed: No such file or directory.
Target filesystem doesn't have /sbin/init
```

After that, I'm in a BusyBox prompt with virtually nothing in the root file system (save the /root directory, which has the contents of the USB stick)

Any ideas? I'm going to go try and boot the USB stick in my laptop and see if it works.

---

### Post by Pumalite on 2007-11-20
Try a different guide:

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by klange on 2007-11-20
Ok, the stick itself works perfectly, it's the whole "booting from Grub" thing that's not quite working, however I know it is booting to the USB stick, just not correctly.
Hmm: This is odd. For some reason, with my Grub floppy in the drive, my Live CD is booting - to initramfs? Odd.
Removing the disk boots normally. Something tells me the way things are set up may require me to remove the disk once Grub loads...

---

