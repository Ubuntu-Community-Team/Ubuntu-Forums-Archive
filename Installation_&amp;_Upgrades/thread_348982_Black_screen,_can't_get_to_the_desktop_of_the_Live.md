---
title: "Black screen, can't get to the desktop of the Live CD"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by tomzx on 2007-01-29
Hi,

I've  been trying to install Ubuntu 6.10 without any success. The first times I would stop after the "ide:huh?" kind of error (which are still present) but who don't affect the process. The problem is that after all those errors have shown up, the screen turn black for a moment, flash once or twice and stay black.

I've tried CTRL+ALT+F1 and CTRL+ALT+F2 but none of these command worked. I cannot get to the desktop of the live cd...

I do not get any sound during this black screen, I've tried with "vga=771 noapic nolapic" with no success either.

My config
AMD 64 3000+
ATI Radeon 9600 SE
Seagate SATA 400 GB (2 NTFS partitions for windows)
DVD samsung (optical drive)

---

### Post by tomzx on 2007-02-01
Well, I finally got Ubuntu running, here's how:

1. Download the Alternate CD, install Ubuntu.
2. The system will reboot, start in rescue mode (or the safe mode). You should have a console. Type:
> 
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx

This will install ATI drivers which, it seems, we're not installed "by default". At that moment, you got a fully running Ubuntu :) Enjoy.

---

