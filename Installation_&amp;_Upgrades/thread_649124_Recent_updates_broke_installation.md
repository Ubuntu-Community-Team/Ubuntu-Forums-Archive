---
title: "Recent updates broke installation"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by AndyBMcC on 2007-12-24
So I'm joining everyone with all of the recent update problems.  I'm using Kubuntu 7.10 and just did all of the kernel updates via Synaptic.  When I tell grub to boot normally I just end up with a blank screen.  I can boot into the recovery mode just fine.  I did this to check my /boot/grub/menu.lst

It it fine, I know other people had problems with this.  Another odd thing I've noticed, I tried to boot using the live CD and it will only boot in the safe graphics mode.  I just get a black screen if I say to do so normally.

Anybody have any ideas or where to start my search?  It would be much appreciated.

---

### Post by AndyBMcC on 2007-12-24
Nevermind, fixed.  I'm an idiot.  I had been messing around with this forever and a simple

sudo dpkg --configure -a

fixed the problem.

---

