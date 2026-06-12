---
title: "Ubuntu on 8MB RAM?"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by navilon on 2006-08-22
i have a CTX EZBook 700 laptop.

contains the following hardware specs:

[LIST]
[*]2GB HD
[*]      8MB memory
[*]      Floppy drive
[/LIST]

Sadly, it does not have the following:

[LIST]
[*]NO cdrom drive
[*]      NO usb
[*]      NO ethernet
[/LIST]

Is it possible to put ubuntu on this bad boy?

---

### Post by meng on 2006-08-22
There are a number of reasons why this wouldn't work... not enough RAM, no way of accessing install media, and not enough HDD space. There are versions of Linux that will run on this ... beast ... but I doubt that you'll get a GUI on there.

---

### Post by navilon on 2006-08-22
well, i dont even need a GUI. I'm very comfortable with the terminal, but I would just prefer the debian package system on my laptop if possible.

---

### Post by meng on 2006-08-22
[http://wiki.laptop.org/go/Minimal_Linux_distros](http://wiki.laptop.org/go/Minimal_Linux_distros)
It's a starting point, although it may not suit your needs.
I don't know the minimum requirements for a debian-based system.

---

### Post by az on 2006-08-22
You could install Debian Woody with 8 megs of ram.  After that, you only needed 4 megs of ram to run it.

You can probably install Woody and then dist-upgrade to Sarge.

I think you can still download the thirty boot floppies for Woody.

(I am serious)
[http://www.debian.org/distrib/floppyinst](http://www.debian.org/distrib/floppyinst)

Use the "compact" kernel:
[http://www.debian.org/releases/woody/i386/ch-install-methods.en.html](http://www.debian.org/releases/woody/i386/ch-install-methods.en.html)

---

### Post by navilon on 2006-08-22
thank you very much, now i have a place to start.

---

