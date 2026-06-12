---
title: "OSX Apps."
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by ErusGuleilmus on 2007-07-03
Is it possible to run some OSX applications on Ubuntu? And if so, how? I apologize if this is in the wrong forum, but I was just curious.

---

### Post by Lord Illidan on 2007-07-03
I don't think it can be done. I know OSX can be run in Qemu on Linux, and that you can run linux apps on OS X, but not what you are asking for. Did you have any specific apps in mind?

---

### Post by ErusGuleilmus on 2007-07-03
Nothing to in particular. I am just messing around with Safari on Windows (I'm at work) and was wondering if some Mac Apps. run on Linux. I don’t know much about programs, so forgive my ignorance, but why don’t really any OSX apps run on Linux? Aren’t both partially or totally based off of UNIX?

---

### Post by thully on 2007-07-03
You can't run OS X apps on Linux because while both are based on Unix, both are quite different.  For one, they use different kernels (Linux vs. Mach) , binary formats (ELF vs. Mach-O), and APIs (Carbon/Cocoa vs. X11).  Many open source applications used on Linux DO run on both operating systems, since they are ported to run in both environments (MacPorts/Fink are the two well known collections of OSS apps ported to OS X).  However, you generally can't run OS X apps in Linux- even virtualization isn't much of an option here, as you can't run OS X reliably in a VM as you can Windows.  

So, what I'd say is - if you want to use OS X apps, you pretty much are limited to looking for open source equivalents, running Windows versions of said apps in a virtual machine, or dual-booting OS X and Linux.  I do the latter on my MacBook, and it works quite well.

---

### Post by eros82ca on 2007-07-03
I have seen a video and I'm trying to figure this one out myself.  I think that if you install a form of VMware that you can actually run the entire OS X operating system in ubuntu (if you have a OS X disc).

---

