---
title: "HP 6710b Laptop can't boot 8.04"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by ouchouchouch on 2008-05-25
I've an HP 6710b laptop, completely standard except for 4 Gigs RAM, 200 Gig 7200 RPM SATA drive. It won't directly install either the 8.04/7.10 i86/x64 desktop or alt install CD. 

Initial boot from CD to the install menu is fine. After that all the above fail with exactly the same problem having selected the install option, which is nothing happens where it should go to the installation animation after the kernel becomes alive.

Installs fine from 7.04, and can be upgraded from there all the way to 8.04 no problem. But the end state I really want is an encrypted LVM, with authentication at boot time and I'm not sure this is supported in 7.04?

Is there a way to force a non graphics install or something with the alt CD, which has the utility for doing an encrypted LVM install on it? 

Thanks for your help, any advice, or de-bug options discussion to get more information is very welcome.

---

### Post by Partyboi2 on 2008-05-26
maybe these might help
[https://help.ubuntu.com/community/FeistyEncryptedRootWithInstaller](https://help.ubuntu.com/community/FeistyEncryptedRootWithInstaller)
[https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto](https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto)
[http://packages.ubuntu.com/feisty/admin/cryptsetup](http://packages.ubuntu.com/feisty/admin/cryptsetup)
[http://www.debian-administration.org/articles/577](http://www.debian-administration.org/articles/577)

---

### Post by ouchouchouch on 2008-05-28
> **Partyboi2 said:**
> maybe these might help
[https://help.ubuntu.com/community/FeistyEncryptedRootWithInstaller](https://help.ubuntu.com/community/FeistyEncryptedRootWithInstaller)
[https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto](https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto)
[http://packages.ubuntu.com/feisty/admin/cryptsetup](http://packages.ubuntu.com/feisty/admin/cryptsetup)
[http://www.debian-administration.org/articles/577](http://www.debian-administration.org/articles/577)
Thanks for that information. I don't think I'd be able to make that LVM solution for 7.04 work, I just don't have enough time to experiment unfortunately because I use the laptop every day and can't really have downtime to play with it.

Is there anyone out there who can help me find out why my HP 6710b laptop silently fails to boot any version of Ubuntu greater than 7.04 past the boot menu? 7.04 works just fine (except for the broken graphics and lack of disk encryption out of the box :-)

I'd like to file a bug report so this problem may get fixed one day. But Ubuntu does not report where it fails. I did try booting it from the cd with BOOT_DEBUG=3 added to the grub boot string but it just ends up with a busybox prompt. Also I did read that this HP laptop is fine for Hardy when it was tested by the Ubuntu laptop team. So I really can't understand what is going on :-(

---

### Post by PenguinInAWindowsWorld on 2008-09-13
ouch^3,

I'm looking to do the same thing as you....

HP 6710b - 8.04 w/ disk encryption

[http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/](http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/)

... and I hit the same problem as you.

You choose "Install Ubuntu" and the screen goes blank.

Solution:

Before you choose "Install Ubuntu", press f6 and add vga=771 to the end of the boot options, like such...

blahblahblah/install/initrd.gz quiet vga=771 --

The installer will go through a CD verification and then reboot.  You need to add the vga=771 again and the installer will continue.

---

