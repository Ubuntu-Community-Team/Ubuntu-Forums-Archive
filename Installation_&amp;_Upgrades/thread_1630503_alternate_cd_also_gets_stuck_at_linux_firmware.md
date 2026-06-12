---
title: "alternate cd also gets stuck at linux firmware"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by ramaswamyps on 2010-11-25
ubuntu-10.10-desktop failed to boot upto desktop.
i got alternate installer .
even that stops at preparing linux firmware.
first it said could not make group floppy.
i removed the floppy and updated bios settings.
then i got upto preparing linux firmware after that nothing happens.
i have used ubuntu from very early stages versions
never seen any of them giving such a lot of trouble installing to a desktop comp.
any further can i do??

---

### Post by ramaswamyps on 2010-11-25
i am trying salvage the partially installed ubuntu in /dev/sda11
i get these messages.

```
[root@localhost ~]# chroot /mnt/ubuntu /bin/bash
root@localhost:/# apt-get install aptitude
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
root@localhost:/# dpkg --configure -a
Setting up wireless-crda (1.12) ...
Setting up linux-image-2.6.35-22-generic (2.6.35-22.33) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
mktemp: failed to create directory via template `/root/tmp/mkinitramfs_XXXXXX': No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.35-22-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
root@localhost:/# dpkg --configure -a
Setting up linux-image-2.6.35-22-generic (2.6.35-22.33) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
mktemp: failed to create directory via template `/root/tmp/mkinitramfs_XXXXXX': No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.35-22-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
root@localhost:/# apt-get install aptitude
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libboost-iostreams1.42.0 libcwidget3 libept1 libsigc++-2.0-0c2a libxapian15
  linux-firmware
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev xapian-tools
Recommended packages:
  apt-xapian-index libparse-debianchangelog-perl
The following NEW packages will be installed:
  aptitude libboost-iostreams1.42.0 libcwidget3 libept1 libsigc++-2.0-0c2a
  libxapian15
The following packages will be upgraded:
  linux-firmware
1 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/14.7MB of archives.
After this operation, 33.1MB of additional disk space will be used.
Do you want to continue [Y/n]? uy
Abort.
root@localhost:/# apt-get install aptitude
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libboost-iostreams1.42.0 libcwidget3 libept1 libsigc++-2.0-0c2a libxapian15
  linux-firmware
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev xapian-tools
Recommended packages:
  apt-xapian-index libparse-debianchangelog-perl
The following NEW packages will be installed:
  aptitude libboost-iostreams1.42.0 libcwidget3 libept1 libsigc++-2.0-0c2a
  libxapian15
The following packages will be upgraded:
  linux-firmware
1 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/14.7MB of archives.
After this operation, 33.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
in the drive '/media/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
in the drive '/media/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
in the drive '/media/cdrom/' and press enter 
```

why it is asking different cd in rom drive?
i have cd made for ubuntu-10.10-alternate-i386.
why it is not looking at aptsources instead of cdrom?

---

### Post by ramaswamyps on 2010-11-26
finally managed to rescue the partially installed ubuntu chrroting in pclinuxos.
dpkg --configure -a
worked.
commented on sources.list the cdrom
then from upgrade site it worked.

the other thing noticed is we have to accept ext4 format.
otherwise linux image does not load.

---

