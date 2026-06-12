---
title: "Help! Package udev half-installed"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by morrisjones on 2010-12-23
Yesterday I had an inadvertent reboot in the middle of Update Manager doing its work, and now I can't boot 10.10 from the hard disk.

When I examine the image from a CD boot, dpkg shows these two packages in half-installed state:

udev
linux-image-2.6.35-24-generic

I've attempted to do:

sudo dpkg --root=/media/<diskId> configure -a

It attempts to configure udev, but fails with about 30 lines of errors, including "/usr/sbin/mkinitramfs: <line> can't create /dev/null: permission denied" and "WARNING: no ldd around - install libc-bin"

"Failed to created initrd image"

My file system is intact.  I badly need suggestions.

Mojo

---

### Post by morrisjones on 2010-12-23
Problem solved!

I needed to remount my hard disk as root so it could be written to:

umount /dev/sda2
sudo mkdir /target
sudo mount /dev/sda2 /target
dpkg --root=/target --configure -a

That allowed the packages to be properly configured, and my hard disk now boots correctly.

Mojo

---

