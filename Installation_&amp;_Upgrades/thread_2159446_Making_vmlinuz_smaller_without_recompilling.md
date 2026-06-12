---
title: "Making vmlinuz smaller without recompilling"
date: 2013-07-03
forum: Installation &amp; Upgrades
---

### Post by e-San on 2013-07-03
Hi!

I'm trying to install Ubuntu 12.04 server on Wyse S10 terminal [Short overview: [http://fijam.eu.org/blog/running-linux-on-wyse-s30/#comment-1085](http://fijam.eu.org/blog/running-linux-on-wyse-s30/#comment-1085) ].
It has limited amount of memory (at the moment) and problems with boot-loaders.

I've tried to install syslinux, grub2, grub-legacy but only grub-legacy from coreboot linux (SIC!) works.

So, I configured grub-legacy and moved files from (VBox) installation to root of filesystem.

It works +/- fine but kernel and initrd loads takes some while (about two minutes before i remade init file).

I compressed init file with xz and was thinking about compressing vmlinux with xz.

Is it possible and how to make it?

Regards!

---

