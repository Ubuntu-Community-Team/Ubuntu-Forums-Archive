---
title: "How to stop a text based machine going into graphics mode"
date: 2010-01-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Bike-and-snow on 2010-01-05
Hello

I've been testing Lucid as virtual machines. So far so good.

However, I cannot find a way to stop the machine going into "graphics text" mode after boot. This is making my VNC client **very slow**.

I've tried:
/etc/default/grub

Setting this:
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

That fixes Grub, but after boot it still goes into "graphics text" mode.

Does anyone know how to disable this?
Karmic does not do this - it stays in "proper" text mode.

Thank you

---

### Post by nanog on 2010-01-05
ubuntu server:
[http://cdimage.ubuntu.com/releases/lucid/alpha-1/lucid-server-i386.iso](http://cdimage.ubuntu.com/releases/lucid/alpha-1/lucid-server-i386.iso)
[http://cdimage.ubuntu.com/releases/lucid/alpha-1/lucid-server-amd64.iso](http://cdimage.ubuntu.com/releases/lucid/alpha-1/lucid-server-amd64.iso)

or netboot mini.iso:
[http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/mini.iso)
[http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-amd64/current/images/netboot/mini.iso)

---

