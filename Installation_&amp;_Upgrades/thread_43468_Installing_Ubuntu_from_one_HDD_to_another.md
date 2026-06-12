---
title: "Installing Ubuntu from one HDD to another"
date: 2005-06-22
forum: Installation &amp; Upgrades
---

### Post by Sidster on 2005-06-22
I'm sorry if this question has been asked already. I've tried searching the forum with no luck. My question is this:

I have two IDE hard drives and no cd writer. I've dowloaded Ubuntu 5.04 and want to know if I can install Ubuntu onto one of my drives from the other one. I can format one of the drives if neccessary. I thought maybe it was a case of copying the boot files to the blank hard drive and booting from that hard drive. 

I'm currently on Windows XP using a P4 2.4Ghz 512Mb Ram on board Graphics. 

Oh yes, to make matters worse I' behind a proxy. I did see something on installing from behind a proxy I'll just have to read up on that.

Once again sorry if my question is daft or has already been answered. I can't wait to get Haory up and running. :-P

---

### Post by uidzer0org on 2005-06-22
you will have to install grub on the second hdd and then copy the files over - modify the bios to boot off hdd2

---

### Post by mingus on 2005-06-23
[QUOTE=Sidster]I have two IDE hard drives and no cd writer. I've dowloaded Ubuntu 5.04 and want to know if I can install Ubuntu onto one of my drives from the other one. I can format one of the drives if neccessary. I thought maybe it was a case of copying the boot files to the blank hard drive and booting from that hard drive. 
. :-P[/QUOTE]

Take a look at the following from the manual:

[http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch02s02.html#id2526441](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch02s02.html#id2526441)
[http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch04s04.html](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch04s04.html)
[http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch05s01.html#boot-initrd](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch05s01.html#boot-initrd)

I haven't done this, so can't speak to all the details.  But basically, in addition to the files, you will need to install a loader to the boot sector (this is true of *any* bootable media) and because this is a Linux installation, the kernel initialization image (the equivalent of Windows install setup.exe).

---

