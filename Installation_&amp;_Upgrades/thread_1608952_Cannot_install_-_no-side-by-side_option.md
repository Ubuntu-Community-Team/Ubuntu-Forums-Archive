---
title: "Cannot install - no-side-by-side option"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by andylh on 2010-10-29
I am trying to install ubuntu 10.10 on a hard drive that has Windows2k on the first partition (NTFS) and no other partitions yet assigned. (No other physical hard drives in the system)

When I run the install wizard (from the live CD) I do not get the screen for side-by-side install, it jumps straight to the next screen "allocate drive space" there is no option to change the boot loader from /dev/sda and when I try to continue from there gives me the error "No root file system is defined. Please correct from the partioning menu." No such partioning menu exists, and in gparted there is no option to create a mount point nor a way to install the boot loader. The error message is incorrect, and I still can't install. With some 60 gigs not used or partioned yet on the drive it should have been simple. Also grub-install errors too with message "cannot find a device for /boot/grub, is /dev mounted" - which it is.

Why do I not get the side-be-side install screen?

I have searched with google and all over, and no simple solution was forthcoming. This is not the first time I have installed Linux Ubuntu and have never had problems before on dual/triple boot with multiple OSs.

Can I have some simple instructions on how to proceed, creating partitions if necessary, something which should have been automated.

Thanks

Ah

---

