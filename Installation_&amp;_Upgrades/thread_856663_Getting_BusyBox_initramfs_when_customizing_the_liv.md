---
title: "Getting BusyBox initramfs when customizing the live CD"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by ramvi on 2008-07-11
I'm building Ubuntu Eee 8.04.1 ([www.ubuntu-eee.com](www.ubuntu-eee.com)). I used Reconstructor for the 8.04 release, but it's just not good enough.

I've followed this howto (which seems really great): [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

I removed every kernel-modules, image etc. from Ubuntu 8.04.1 and followed every part of the howto, especially the "Live CD Kernel" and the "Rebuilding initrd" parts.

When I try to boot the iso however, I don't reach X11 / gnome but I'm getting BusyBox built-in shell (initramfs).

What am I doing wrong?

Jon Ramvi

---

### Post by ramvi on 2008-07-13
bump

---

### Post by nightmarelord on 2008-09-29
I've tried to to install Ubuntu-eee yesterday and ran into the same problem. 

This might be just a wild guess, but haven't you removed the CD-ROM support while customizing? I'm asking because this makes sense, as the eee has no CD drive...

---

### Post by red_team316 on 2008-10-04
I've had a little time testing this problem(up until recently, I could not reproduce the busybox error on any of my customized LiveCD's). I think the problem is due to the version of squashfs used to build the LiveCD. 

The ubuntu hardy repos do not have the latest version of squashfs-tools yet. Try uninstalling squashfs-tools and then downloading:

**for 32-bit:**
[http://ftp.de.debian.org/debian/pool/main/s/squashfs/squashfs-tools_3.3-7_i386.deb](http://ftp.de.debian.org/debian/pool/main/s/squashfs/squashfs-tools_3.3-7_i386.deb)

**for 64-bit:**
[http://ftp.de.debian.org/debian/pool/main/s/squashfs/squashfs-tools_3.3-7_amd64.deb](http://ftp.de.debian.org/debian/pool/main/s/squashfs/squashfs-tools_3.3-7_amd64.deb)

**ftp location:**
[http://ftp.de.debian.org/debian/pool/main/s/squashfs/](http://ftp.de.debian.org/debian/pool/main/s/squashfs/)

from the debian ftp. Then try to rebuild your custom hardy iso and you should not get the busybox error when testing in QEMU/Virtualbox.

To find out if this is your problem, take your borked busybox-ISO and fire up your iso in QEMU/Virtualbox and hit F6 at the boot menu, and then remove the quiet and splash lines. You should see text very similar to this:
```

...
Registering unionfs 20060916-2203
unionfs: debugging is not enabled
loop: loaded (max 8 devices)
squashfs: version 3.2-r2 (2007/01/15) Phillip Lougher


BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) _

```
If you see that, then it is obviously hanging while trying to read the squashfs. I think part of the problem is bugs in squashfs as well as the recently added lzma compression.

I hope this helps.

---

