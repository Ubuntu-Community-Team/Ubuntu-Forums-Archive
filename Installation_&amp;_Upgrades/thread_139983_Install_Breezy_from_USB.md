---
title: "Install Breezy from USB"
date: 2006-03-05
forum: Installation &amp; Upgrades
---

### Post by jpg on 2006-03-05
I have tried several different ways to install Ubuntu, without much luck. I have a dead ethernet card, and my CD drive works fine to boot, but is not detected when the install process gets to the point of installing the base system.

Right now I am trying to boot and install from a 1GB Sandisk Cruzer Mini USB drive, as described here: [ Installation/FromUSBStick ]("https://wiki.ubuntu.com/Installation/FromUSBStick") 

I can boot from a Ubuntu Live CD, and access the Internet through a USb adaptor (thanks Ubuntu!), and I updated using apt, and then installed mtools and syslinux. I formatted the USB drive as FAT16, made it bootable, and installed syslinux using "syslinux -s /dev/sda1" (it does not work when the USb drive is mounted as the instructions say). It all seems to go well, but when the Pc tries to boot from the drive (I modified the BIOS) it hands at the point of "Verifying DMI Pool Data...".

Then, if I go back and try to mount of cfdisk the USB drive again afterward, it says that the USB drive is inaccesible because the start of the partition is beyond the end of the drive. I can fix this by running mkdosfs on the first partition again, but I am not sure why this happens, or why setting up a dos file system fixes this without modifying the partition table.

Is is something that syslinux is doing when I run it with the -s flag? Should I run it on /dev/sda instead of /dev/sda1?

I guess I will try some experiments, but any help, tips, or suggestions would be greatly appreciated.

---

### Post by jpg on 2006-03-05
This is very frustrating. I can't get the USB to boot, but I still have the equivalent of the CD on the USB drive, where I can get at it. I followed the instructions on the linked page, but instead of booting from the USB drive (which does not work - it hands on the Validating DMI data thing), I booted off the CD. That works fine, up until the point it tries to install the base system, when it fails because it cannot find the CDROM (yeah, go figure).

So, I dropped to a shell, at various points in the process, and mounted the USB drive on /cdrom. It didn't work. I also tried mounting it on /target/cdrom and on /target/media/cdrom (actually, it was already mounted there - or maybe the real CDROM was). So what is the problem? Why can't it find the base files to install? Is there anyone who understands how the installer works? Is there any way to point it toward the files that I have waiting, in two different removable formats, to install?

The worst part is that Fedora installs fine - except that it can't work the USB ethernet gateway. And I really wanted to install Ubuntu.

Help? Anyone?

---

### Post by jpg on 2006-03-06
The second frustrating aspect of this is that the installer knows where the CD is at the start of the process. If I run a CD check before I get to the disk partition stage, it works fine. If the CDROM has not been detected, it runs that process, detects the CDROM correctly, and then does an integrity check.

However, once it has reached the point of trying to install the base system, it complains that there it cannot find any CD or source of information available. Trying to do a validity check at this point fails, even when the CD is mounted at /cdrom. I don't know enough about the installer to know why this happens.

If there were only some way to intervene at this point and force the installer to recheck the system (or, praise be, define a network source for the base system).

Any ideas?

---

