---
title: "Start installation from Grub"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by oneindelijk on 2010-02-02
Hi, 

I have a pc where I want to install Debian.
On the HD are 3 partitions.
I copied the bootfiles from an existing ubuntu system, unetbootin is there also as well as 4 floppy images (debians boot.img, root.img and two network-related images.
When I start the pc I get grub-rescue.
I manage to start the grub with the menu from the other system  ```
prefix=(hd0,1)/boot/grub
insmod (hd0,1)/boot/grub/linux.mod
```)

After fiddling around I managed to load the kernel with
```
linux /boot/vmlinuz-2;6;31-17-generic
initrd /boot/boot.img
```

that doesn't work (as expected)... 
I get a kernel Panic error
How can I load the disk-images through grub and boot them ?

---

### Post by oldfred on 2010-02-02
Some older instructions here:

[https://help.ubuntu.com/8.04/installation-guide/i386/boot-drive-files.html](https://help.ubuntu.com/8.04/installation-guide/i386/boot-drive-files.html)

---

### Post by oneindelijk on 2010-02-15
Hi, 

This thread isn't helping me any further.
I manage to get into the installation screen, but no drivers are found for the network card and I can't mount any partitions because of an error message in the mount (no specific details).
I've tried to mount the debian-netinstall iso in grub and the launching the install kernel, but once there I don't know how to acces the iso...
(It doesn't show up in the mount list)

I'd be happy with some more help...

---

### Post by oneindelijk on 2010-02-15
Hi, So far I've managed to boot the first of four floppies for a debian-netinstall.
Of course, during the installation it ask for the other floppies as well.
I've tried mounting all of them through
```
loopback /dev/fd0 <path to image>
loopback /dev/fd1 <path to image>
```
and then referring to these devices when the installaer ask for it, but that doesn't seem to work.
Any ideas how I can mount multiple images in grub (before starting the installer-kernel) ?

---

### Post by oneindelijk on 2010-02-19
Okay, I've got this solved eventually.
I put some other initrd.gz and vmlinuz from debian on the HD
along with the debian installer iso and when booting this the installer searches for the iso on the partitions and listo !!
I certainly learned a lot about grub trying to solve this :-)

Thanks for the help !!

---

