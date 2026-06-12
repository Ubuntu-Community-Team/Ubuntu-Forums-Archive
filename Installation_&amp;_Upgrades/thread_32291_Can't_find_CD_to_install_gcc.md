---
title: "Can't find CD to install gcc"
date: 2005-05-06
forum: Installation &amp; Upgrades
---

### Post by homecomputeraid on 2005-05-06
I'm trying to install the Gnome C Compiler (gcc).  Whether I try it using Synaptic Package Manager, or the command line sudo apt-get install gcc, I get an error when asked for the Ubuntu CD.  I have it in the CD ROM Drive, but it isn't found.

tleroy@UbuntuDeskTop:/$ sudo apt-get install gcc
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  manpages-dev autoconf automake libtool flex bison gcc-doc
The following NEW packages will be installed:
  gcc
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4892B of archives.
After unpacking 65.5kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter

How do I get past this?  I've tried mounting the drive, but it still isn't found.

Thanks!

---

### Post by Xian on 2005-05-06
[QUOTE=homecomputeraid]How do I get past this?  I've tried mounting the drive, but it still isn't found.[/QUOTE]
Try commenting this line in your /etc/apt/sources.list so Synaptic won't default to the CD when looking for this package:

# deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

---

### Post by homecomputeraid on 2005-05-06
Thanks Xian,  

That did it.  Should I set the value back when I'm done?

---

### Post by Xian on 2005-05-06
You can if you want, but unless you are on a slow internet connection I would just leave it commented.

---

### Post by homecomputeraid on 2005-05-06
I have Cable.  I think I'll leave it.  Thanks for the help!

---

### Post by homecomputeraid on 2005-05-12
Same problem on a different PC.  Should I report this as a bug?

---

