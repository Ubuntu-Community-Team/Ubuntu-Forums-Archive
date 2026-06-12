---
title: "How to Install Server 9.10 from hard drive?"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by sanigo on 2009-11-21
As I know, we can install desktop 9.10 from hard disk.
But how to do the same for server edition?
How can I boot the server iso image by grub/grub4dos?

---

### Post by gnappoman on 2009-11-21
:popcorn:Hello I am solving this problem right now since I have a sun netra x1 server and a ubuntu 9.10 alternate sparc iso laying around...
first I must say I had a previous installation of debian 3.0 for sparc on another drive, with SILO (boot manager for linux on sparc) installed.
this is what I done:
-attached the old hard drive (with silo boot manager installed) to a linux box

-downloaded vmlinuz and initrd.gz from here [http://ports.ubuntu.com/ubuntu-ports/dists/karmic/main/installer-sparc/current/images/cdrom/](http://ports.ubuntu.com/ubuntu-ports/dists/karmic/main/installer-sparc/current/images/cdrom/)

-downloaded ubuntu 9.10 alternate sparc iso (or server version if u like)

-placed these three files into /tmp/ directory of the disc (could be an /ANY/ directory of the drive) renaming initrd.gz --> initrd.img

-edited silo.conf now looking like this
```
root=/dev/hda1
partition=1
default=Linux
read-only
timeout=100
image=/tmp/vmlinuz
        label=Linux
        initrd=/tmp/initrd.img
```
note that "root=/dev/---your hd---"
& that "partition=---partition number where is placed /tmp/vmlinuz---"

connected both hard drives (the new and the old) to sun server
booted and voilà

---

