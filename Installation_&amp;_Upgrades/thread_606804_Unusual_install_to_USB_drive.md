---
title: "Unusual install to USB drive"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by evilpenguin on 2007-11-08
I'm doing something unusual, and I think I have a way out if I must (namely getting a USB CD/DVD drive to boot the install disk from).

Let me back up a bit.

I'm trying to create a sort of appliance box using Ubuntu Server as a base. I have a box intended as a thin client that has a VIA 32-bit Intel-like CPU, 128M RAM, 512M built-in flash disk, and no OS of any kind on it.

I had the bright idea of using my laptop to install Ubuntu server to a 4G USB flash drive and then to boot from that on my thin client machine. Good news is, it works!

Almost.

Because my laptop is an AMD-64 (which I use 32-bit because of certain minor niggly problems) it appears that the installer selects an improper kernel. When I boot from the USB drive on the thin client box, GRUB does its thing, the kernel is uncompressed and it starts, but then I get a kernel panic that says (sorry I don't have exact text) PANIC: This processor is too old for this kernel.

Is there a way to boot the Ubuntu Server installer with a parameter that would force a CPU selection instead of an autodetect?

My other thoughts on how to deal with my problem are:

1. Compile my own kernel, setting the CPU possibly even down to a 486 and then to install it on the USB stick.

2. Get a USB-CDROM/DVD drive and boot the Ubuntu installer from the actual target machine

But I really think I ought to be able to do this the way I'm trying. Any tips would be welcome!

---

