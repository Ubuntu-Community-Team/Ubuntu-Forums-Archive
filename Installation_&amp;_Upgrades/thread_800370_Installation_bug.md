---
title: "Installation bug"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by mmacomp on 2008-05-19
Hi,

I am trying Ubuntu for the first time.  After downloading the 8.04 desktop edition, I created a CD from the ISO, and booted off the CD.  As the live CD is loading, after a minute or so the live CD stops with a terminal screen which says:  BusyBox v.1.1.3 (Debian 1:1 1.3-5ubuntu....).  It is then stuck there waiting for some input from me, although I don't know what it wants.  I am trying this on a Pentium 4 single core 3 mhz computer with 1 gb of ram and a 4 hard disks, with windows already installed.

I tried the same exact live CD on a different desktop computer, which worked just fine, and reached the gnome desktop of the live CD.

Any ideas?

---

### Post by EXCiD3 on 2008-05-19
There is a slight conflict with some of your hardware preventing it from booting properly. You can try adding boot parameters. To do this when you pop in the cd and it gets to the first menu and asks you what you want to do, press F6 and add the parameters to the boot line. Some to try are "all_generic_ide" and "irqpoll". Just search for boot parameters and busybox. There are lots of different causes for this problem and some parameters fix it yet sometimes they dont.

---

### Post by mmacomp on 2008-05-19
Hi,

I am trying to install Ubuntu 8.04 desktop.  After burning a CD from the ISO which I downloaded, and attempt to boot up on the CD, choose my language, and choose the first default installation option, which should bring up the live CD desktop.  After a minute of the Ubuntu bar moving back and forth, the installation stops with a terminal screen (black and white), and the BusyBox v. 1.13 (Debian 1:1 1.3-5ubuntu) comes up with a prompt waiting.  I don't know what to type in at this point.  I am attempting to boot on a Pentium 4 single core desktop, with 1 gb of memory, and 4 hard disks, with Windows already installed.

When I try the same exact CD on another desktop, it works fine, and the Gnome desktop of the live CD loads up.

Any ideas?

Thanks

---

### Post by tamoneya on 2008-05-19
what happens if you try the safe graphics mode.  Also it is not uncommon for it to take a couple minutes for loading since it is a LOT slower if it has to read the OS from a cd.

---

### Post by jpeddicord on 2008-05-19
Duplicate threads merged.

---

