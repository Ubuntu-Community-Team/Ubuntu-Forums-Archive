---
title: "Ubuntu installation to usb"
date: 2016-10-27
forum: Installation &amp; Upgrades
---

### Post by james884 on 2016-10-27
Hi,

I am trying (just for fun) to get Ubuntu running from an USB stick.
I have copied all the necessary files/directories from the hard drive (cp -a /lib /bin /sbin ..) to the usb. I am able to chroot into the usb drive just fine.

I have also installed GRUB to the usb, and modified UUID's to reflect the changes(from the fstab copied from hard drive) 

But when i try to boot to the usb stick, for some reason init tries to mount the root file system under /mnt/root

What am i missing here?

---

### Post by yancek on 2016-10-27
Is this an MBR install on the usb stick?
Did you install Grub there?
Are you booting the usb stick directly or from an entry in the Grub menu on the hard drive?
It's simpler to just use the installer to install to the usb drive unless you're just doing it for the challenge?

---

### Post by ajgreeny on 2016-10-27
I think your understanding of creating a full bootable installation on a USB is incorrect.

You need to do what yancek says and install Ubuntu in the usual manner, except that it is very important that you choose "Something Else" at the partitioning stage.

That will allow you not only to choose that USB disk to install to but also lets you choose where to install grub, which in this case is the MBR of the USB disk, ie, possibly /dev/sdb, not to the partition, /dev/sdb1.  Only you will be able to see which is the correct name for you disk, so choose carefully.

Be prepared for the OS on a USB to run quite slowly, particularly if a USB-2 stick; if you have USB-3 ports and stick it will be much faster, so try that if possible, as long as you are sure that your machine will boot from a USB-3 port and stick.

---

### Post by james884 on 2016-10-27
I mounted the root partition on the usb under /mnt/root and the boot partition under /mnt/root/boot, then issued: grub-install --boot-directory=/mnt/root/boot /dev/sdb

---

### Post by Bucky Ball on 2016-10-27
> **yancek said:**
> It's simpler to just use the installer to install to the usb drive unless you're just doing it for the challenge?

Much. Or you could simply clone your install to the USB, tweak the grub and you're done.

---

### Post by C.S.Cameron on 2016-10-27
Did it work?
I don't see why it wouldn't work, what do you have flagged as the boot partition?

---

### Post by james884 on 2016-10-28
No it didn't work. For some reason it tries to mount dev under /root
[ATTACH=CONFIG]271823[/ATTACH]

---

### Post by james884 on 2016-11-02
Any insight to what could be causing this?

---

