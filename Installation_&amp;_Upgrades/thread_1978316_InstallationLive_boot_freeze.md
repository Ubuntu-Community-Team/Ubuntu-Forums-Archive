---
title: "Installation/Live boot freeze"
date: 2012-05-11
forum: Installation &amp; Upgrades
---

### Post by finalfortune on 2012-05-11
Hi, i currently have windows 7 64-bit installed.  I'm attempting obtain a dual boot system with Linux.

I initially tried to install **Linux mint 12 64-bit**. It gets to the grub interface, i select the live boot, and somewhere along the process of checking of what im guessing are the drivers for sata, usb etc. it just freezes. If i unplug and plug in something like a USB, it detects and prints those events, so it's not completely frozen.

I then tried to install **ubuntu 12.04 64-bit** and the exact same thing happened. I attempted again by removing all USB peripherals, besides the keyboard, but still no avail.

_[SIZE="2"]My System specs:[/SIZE]_
**Motherboard**: Intel DX58SO
**CPU**: Intel Core i7 960
**Graphics **Card: Gigabyte Geforce GTX560
**RAM**: Kingston 1300mhz 2Gb x2
**HDD**: seagate 500Gb SATA

Is it perhaps that linux does not support my motherboard?

---

### Post by cmont899 on 2012-05-11
Depending on where in the installer your system "froze" you may be able to get some error logs from the other ttys. Try switching to the other ttys to see if you have any errors:

CTRL+ALT+F1
CTRL+ALT+F2
CTRL+ALT+F3
CTRL+ALT+F4
CTRL+ALT+F5
CTRL+ALT+F6

The install generally is F1 or F7

---

### Post by finalfortune on 2012-05-11
I just attempted to switch terminals, but nothing happens, i cannot use ctrl+alt+del or the reset button either.  So i guess it is pretty much frozen.  It always dies when it is checking my 500GB HDD though.

[IMG]http://s15.postimage.org/zc91j6fl7/11052012218.jpg[/IMG]

---

