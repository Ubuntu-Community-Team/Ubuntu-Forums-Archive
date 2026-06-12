---
title: "Reinstall Ubuntu with Live CD"
date: 2012-10-01
forum: Installation &amp; Upgrades
---

### Post by agjios on 2012-10-01
Hello all, I have an Acer R3610 (basically a netbook's internals, and you provide your own monitor/keyboard/mouse), and I decided to install Ubuntu onto it. Installed the most recent version onto it, and installation seemed to go ok, installing Ubuntu onto the hard drive from a USB. It loaded up fine, with the username that I chose. However, whenever removing the "LiveCD" USB drive, the startup would hang at a flashing cursor upon turning on the computer. No matter how I chose the boot drive in my BIOS, grub seemed to choose my hard drive installation. So, my question is, how do I start over from the beginning using this bootCD, and just completely ignore the current installation? It seems as if my LiveCD is looking to my hard drive, and trying to use it when booting, instead of just being self-contained. If I am at the grub command line, and echo $root, then it returns hd1,msdos1. The computer will not boot into Ubuntu any more, it gets stuck at the grub load screen.

---

### Post by agjios on 2012-10-01
Well, after burning half the night to get this done, I ended up making a boot USB drive of my Windows 7 DVD, wiping the hard drive, re-making the Ubuntu USB drive on another USB stick just in case the previous one got corrupted, and was finally able to get past the current issue. Annoying, as I was trying not to make a Windows boot drive, but now we're rolling at least. Judging by the last time, install should take another 20 min or so, and hopefully it will be working fine.

---

