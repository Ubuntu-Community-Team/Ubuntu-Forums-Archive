---
title: "Can't update Ubuntu 10.04"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by Lapland on 2010-07-22
Hi,

I just installed Ubuntu 10.04 in computer where is already Windows XP. This is my first Ubuntu installation. Everything went fine until Ubuntu update manager started to upgrade some files. Something happened and I can't install any new packages.

Synaptic Package manager says that I have 2 broken packages (libc6 and libc6-dev). If I try to upgrade these packages using Synaptic Package manager, error appears and it says:

(Reading database ... 
dpkg: warning: files list file for package `gnome-power-manager' missing, assuming package has no files currently installed.
...
... 
(long list of warnings that files are not installed)
...
dpkg: warning: files list file for package `xserver-xorg-input-vmmouse' missing, assuming package has no files currently installed.
(Reading database ... 46 files and directories currently installed.)
Preparing to replace libc6 2.11.1-0ubuntu7 (using .../libc6_2.11.1-0ubuntu7.2_i386.deb) ...

A non-dpkg owned copy of the libc6-i686 package was found.
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library and try again.
dpkg: error processing /var/cache/apt/archives/libc6_2.11.1-0ubuntu7.2_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.11.1-0ubuntu7.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: failed to open package info file `/usr/local/var/dpkg/status' for reading: No such file or directory


Can anyone help me to fix this problem? Or should I reinstall Ubuntu?

---

### Post by ronparent on 2010-07-22
You might try booting to the rescue mode and running 'dpkg' in the menu - it might give you more than you bargained for but it should fix the dependencies.

---

### Post by Lapland on 2010-07-24
Do you mean booting from Ubuntu CD? I tried to boot from cd, but I can't boot from CD drive for some reason. I also checked BIOS settings to boot from CD drive, but couldn't change any settings from BIOS. It just said that "The number of disks is not adequate to create a RAID!!!" Should I check the CD drive jumpers? Or is there any other way to boot from CD drive?

---

### Post by Lapland on 2010-07-24
I managed to boot from CD. I followed the instructions from here: [http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/](http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/)
 
but I didn't see any selection like "**Recover a broken system".**
 
It was like new installation process and I stopped it. Can someone help how to recover a broken system?

---

