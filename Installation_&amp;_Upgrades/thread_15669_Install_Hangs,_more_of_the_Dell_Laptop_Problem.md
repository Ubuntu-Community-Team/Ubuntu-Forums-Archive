---
title: "Install Hangs, more of the Dell Laptop Problem"
date: 2005-02-15
forum: Installation &amp; Upgrades
---

### Post by Imagist on 2005-02-15
This is my first time trying to install a non-Windows OS, and while I'm pretty comfortable with repartitioning hard-drives etc., I'm a little lost with this.  I had an error when the boot disk was "Loading components of the Ubuntu Installer".  Everything goes fine until it comes to "Retrieving nic-extra-modules-2.6.8.1-3-386-di".  Then the screen flickers (looks like an infinite loop) and I can't do anything except Ctrl-Alt-Delete.

I went back and my other partitions are okay (I'm posting this from the WinXP partition).  So I've been trying different workarounds for the last hour.

I tried the one in the FAQ under Documentation.  It appears that this problem or a similar one is common for Dell laptops (I'm on an Inspiron 1100).  So I tried the workaround they gave there (with nolapic) but it didn't work.  I also tried both solutions [here](http://www.ubuntuforums.org/showthread.php?t=1625) to no avail.  However, I'm not really as comfortable working with the command line as I would like to be, so I may have implemented the workaround incorrectly.  Is there any way somebody could give me a step-by-step "idiot's guide" to one of the workarounds I've mentioned so I can be sure to do it right (not the "linux noacpi pci=noapic" one, I'm pretty sure I did that one correctly)?  Or could someone suggest another way to fix this problem?

Specs, what I remember offhand:
Dell Inspiron 1100
Intel Pentium 4
Chipset Version A06

---

### Post by CyrilleMortreux on 2005-02-16
linux noacpi pci=noapic and try to disable the framebuffer (F7 at the boot should give you more options).

---

### Post by Imagist on 2005-02-16
Okay, I'll try that this afternoon.

---

### Post by Imagist on 2005-02-16
No luck.  What parameter would I pass to prevent the installer from retrieving the "nic-extra-modules-2.6.8.1-3-386-di" at all?

---

### Post by Imagist on 2005-02-16
Also, is it possible to access the grub menu during install so that I can do [this](https://www.ubuntulinux.org/support/documentation/howto/dellat) fix, and if so, how?  I have a feeling that might help the other problem.

---

### Post by Imagist on 2005-02-16
I got it to work.  Thanks for your help, Cyrille.

---

### Post by CyrilleMortreux on 2005-02-17
[QUOTE=Imagist]I got it to work.  Thanks for your help, Cyrille.[/QUOTE]



Well; I 'm not sure to have been usefull !!!

---

