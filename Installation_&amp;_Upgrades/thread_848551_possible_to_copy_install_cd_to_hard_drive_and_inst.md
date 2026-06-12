---
title: "possible to copy install cd to hard drive and install from hd?"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by aBitLater on 2008-07-03
is it possible to copy install cd (8.04) to hard drive and install from hard drive?

Here's my problem:
installing on toshiba portege 3500 with cardbus cdrom.  install starts ok with BIOS set to boot from CD.  I press "english", then install ubuntu... then I think my cdrom drive becomes unrecognizable by the second part of the install process.  Casper log says something like "can't find live file system".

So I was thinking that I could boot with the cd, then change the options with F6 to point to "cdrom1", where I copy the install CD, instead of "/cdrom".

My current opensuse 10.3 freezes when copy cd files from nautilus into the "cdrom1" folder i created directly off of "/".

thanks for any help.

---

### Post by avtolle on 2008-07-03
If you have Windows on that computer, take a look at the following Wiki page:

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

---

### Post by avtolle on 2008-07-03
Or, since you have OpenSuse 10.3, what about Lubi?

[http://lubi.sourceforge.net/lubi.html](http://lubi.sourceforge.net/lubi.html)

---

### Post by sisco311 on 2008-07-03
EDIT: [READ THIS]("https://help.ubuntu.com/community/Installation/FromLinux")

You can use the alternate cd to install ubuntu from your hard disk.
Download the alternate cd and move the iso in the "/" (root) directory
of opensuse.

Download initrd.gz and vmlinuz
from:[for 32 bit]("http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/") or [for 64 bit]("http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-amd64/current/images/hd-media/").

Create a new folder in the root of your filesystem (/ubuntu) and move the files in it.

Edit your menu.lst and add this lines:
> title UBUNTU INSTALL
root (hdX,Y)
kernel /ubuntu/vmlinuz
initrd /ubuntu/initrd.gz
replace (hdX,Y) with the root partition of opensuse.
Reboot your computer and select UBUNTU INSTALL from the grub menu.

---

