---
title: "New installation - goes to BUSYBOX SHELL"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by PogoMonkey on 2008-04-27
Hi,
First of all, im completely new to all of this stuff, the only operating system i've used is Windows, and I thought I might try out ubuntu because it looked pretty good.

I installed it, but not from a disk (i'm not sure if this is what caused it or not..). I extracted the ISO contents onto my flash drive and installed it from there.

I had installed it, and booted my computer, selecting Ubuntu.
It loads the splash screen, the status bar goes back and forward, and then it goes to BusyBox Shell. I downloaded the Desktop edition.

Any idea how I can resolve this?

Thanks.

---

### Post by Pumalite on 2008-04-27
There is a thread going:
[http://ubuntuforums.org/showthread.php?t=765195](http://ubuntuforums.org/showthread.php?t=765195)

---

### Post by PogoMonkey on 2008-04-27
None of that helped, mainly because the solutions said in that thread wouldnt work.
It says to press f6 at the menu, didn't know which, so I pressed it at everything that showed up. Nothing worked.

---

### Post by IT-Joker on 2008-04-28
> **PogoMonkey said:**
> None of that helped, mainly because the solutions said in that thread wouldnt work.
It says to press f6 at the menu, didn't know which, so I pressed it at everything that showed up. Nothing worked.
That F6 thing confused me as well. I suppose it's only there when you boot from the installation CD.

When you start the computer, you should get to the boot menu, which looks like this:
```
Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.22-14-generic
Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 8.04, memtest86+
```
(you'll propably also have Windows option in there)

The key that gets you to the editing mode isn't F6, but E. It should be written at the bottom.
If you don't need to solve this problem and just want to load Ubuntu, you can try selecting the older kernel (2.6.22-14-generic). It worked for me.
If you want to check the cause of the problem, select the option that has "recovery mode" in it. Instead of the loading screen it will show you the messages during start.
If the last one before Busybox is something like:
ata1: /dev/disk/by-uuid/ (some long code) does not exist. dropping to shell
you're propably having the same problem as I was.

---

