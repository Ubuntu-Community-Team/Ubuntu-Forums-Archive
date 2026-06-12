---
title: "[SOLVED] cannot install from [Debian] usb"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by keratos on 2008-03-26
Hi I am trying to setup a USB minimal install from USB following these [less than obvious] yet detailed instructions:


I clearly have something wrong because it doesnt work...

I have downloaded the three files from here
[http://ftp.nl.debian.org/debian/dists/etch/main/installer-i386/current/images/hd-media/](http://ftp.nl.debian.org/debian/dists/etch/main/installer-i386/current/images/hd-media/)
then followed 4.4.1 as detailed here [http://www.debian.org/releases/stable/i386/ch04s04.html.en](http://www.debian.org/releases/stable/i386/ch04s04.html.en)
which effectively creates a VFAT bootable USB with a linux kernel.

The USB boots and loads the installer however, when it gets to searching for an ISO install image it cannot find one despite the fact that I've copied the miniiso.iso from here [http://ftp.nl.debian.org/debian/dists/etch/main/installer-i386/current/images/gtk-miniiso/](http://ftp.nl.debian.org/debian/dists/etch/main/installer-i386/current/images/gtk-miniiso/)

So this doesnt work, the installer cannot find the ISO on the very device it booted from ???
Q. Why can it not see the ISO on the USB drive?

Notwithstanding what I really want to do is put the netinst.ISO on the USB so I can installer using the internet but I cannot find this ISO anywhere?
Q. Where is the NETINST ISO referenced in 4.4.1 (above link)


thanks in advance.

---

### Post by dstew on 2008-03-26
It seems the filename should be **mini**.iso, and you should save it in the USB root directory, I think. And, to install over the network, use the initial RAM disk image from the [netboot directory]("http://ftp.nl.debian.org/debian/dists/etch/main/installer-i386/current/images/netboot/"). It should give you a menu for a network install when you boot up.

---

### Post by keratos on 2008-03-26
> **dstew said:**
> It seems the filename should be **mini**.iso, and you should save it in the USB root directory, I think. And, to install over the network, use the initial RAM disk image from the [netboot directory]("http://ftp.nl.debian.org/debian/dists/etch/main/installer-i386/current/images/netboot/"). It should give you a menu for a network install when you boot up.

CORRECT!

although the mini.iso is irrelevant, makes no difference.

THE essential component is the initrd.gz from the netboot folder. Without this there is no network support hence the install is assumed to be from a media device.

Fixed.

Thanks.

---

