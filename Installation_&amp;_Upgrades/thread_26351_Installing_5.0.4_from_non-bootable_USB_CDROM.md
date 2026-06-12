---
title: "Installing 5.0.4 from non-bootable USB CDROM"
date: 2005-04-12
forum: Installation &amp; Upgrades
---

### Post by rubberband on 2005-04-12
Hi all,

Sorry to make my first post a question, but here goes:

I'm trying to install 5.04 on an older laptop - specifically an IBM Thinkpad 570.  This laptop does not have an internal CDROM drive, and the bios does not support booting from a usb device.

I need a floppy install/boot disk that can recognize my external USB CDROM before starting the install process.  Any thoughts?

---

### Post by KLineD on 2005-04-12
I'm having the same trouble, only that my laptop does have CDROM but its broken. I have an USB CDROM and tried to boot a floppy distribution to read the usb cdrom. I got to the point that dmesg actually shows the cdrom being recognized but for some reason I cant mount it.

I think I'll try a network install using etherboot and I'll post the results.

---

### Post by rubberband on 2005-04-13
The last time I tried this I used Mandrake 9.2 which came with a floppy image called hdcdrom_usb.img that worked a charm - quickly detected the floppy and got eveything underway.  Unfortunatly they don't include that image in the newer 10.x releases.

Not that it would help here, but it's obviously not impossible to build.  I'm sufficiently frustrated at this point that the first distribution that will install from a non-bootable usb drive via a boot floppy I find will be getting installed.  :-|

---

### Post by KLineD on 2005-04-13
I was at it all afternoon. What I did was boot with a tomsrtbt linux on a floppy distribution. From there, I used fdisk to partition the hard drive. The partition table ended up like this:
/dev/hda1   linux
/dev/hda3   swap
/dev/hda5   vfat

with mke2fs I formated hda1 to ext3 and following the guide located [here](http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apcs03.html) 
I had now an ext3 partition in hda1 and swap in hda3.

With the ubuntu iso in hda5 I mounted the image in /mnt/cdrom. Since I couldn't get debootstrap from the image (I couldn't untar it for some reason) what I did is untarred it on another computer, copied it to a floppy and transfered it but that's as far as it went since I was foolish enough to try and mount hda1 on / (I didn't knew about chroot). I tried to boot again but the floppy was ruined and it was too late to go and buy another one. 

I'll try the same tomorrow, I just have one question, does anyone know if I can just copy debootstrap to any directory and run it from there? I mean, copy the usr folder that contains debootstrap in the floppy to any directory in any partition?? I'm asking this because trying to copy it to / so it would be /usr/sbin/debootstrap gives me a "not enough diskspace" so i'm thinking in copying it to the vfat partition and run it from there. 

Any suggestions?

---

### Post by KLineD on 2005-04-14
Does anyone know if I can copy debootstrap to lets say /mnt/ubuntu and then chroot so it would appear as if debootstrap is installed to / and run it from there?

---

