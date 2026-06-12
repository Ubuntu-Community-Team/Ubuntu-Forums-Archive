---
title: "Boot only with install usb key"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by kiki64 on 2010-06-01
Hi all,

I have some issues with a laptop.
I could finally install ubuntu (ubuntu-10.04-desktop-i386.iso) on an external hard drive through usb installation key.

It works fine but doesn't boot on its own, only if the install key is pluged (but really boot form hard drive then. once booted the usb key can be removed, everything works fine).

If the usb key is not here, I just keep a black screen with cursor after the bios, no message.

Any help to make it boot correctly from the hard drive ?

Thanks a lot.

EDIT: after a new install ... now only GRUB loads from the hard drive (without the install key).
When I boot from the install key the main partition is sda1 (bootable), on GRUB the only thing I can do is 'root (hd0,1)' and it tells the fs is ext2  (but I formatted everything in ext4 so I wonder what is this ...)

EDIT2: if I do 'ls' within Grub, it only shows '(hd0) (hd0,1)'.
And if I write : "linux /boot/vmlinuz-[...]-generic root=/dev/" and TAB, it doesn't show any "sdxx", but I can see them in gparted when I boot from the install key. plzzzzzzz

---

