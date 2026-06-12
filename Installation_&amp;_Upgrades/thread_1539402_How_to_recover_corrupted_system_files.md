---
title: "How to recover corrupted system files?"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by justgoodin on 2010-07-26
Hi, 
before i proceed,I'll like to say that I'm a complete newbie, but enjoying my time with Ubuntu.

Recently, due to hard disk failure, some of the System files got corrupted, I have no idea to which files, but booting Ubuntu from the latest kernel is not working, instead I have to select the previous version from the grub screen.

How to recover these files?
Is there a way by which Ubuntu automatically scans and repairs the system files.

---

### Post by regneva on 2010-07-26
Since you are saying that previous kernel is booting, I guess most system files, as it were, are fine. Look at the name of the kernel. Then open synaptic using

```
gksudo synaptic

```

In synaptic, search for your kernel with full name. If it says it's installed, right click on it and mark for re-installation, otherwise mark for installation. After it completes, reboot. This should let you boot with the latest kernel again.

---

### Post by justgoodin on 2010-07-26
thanx, i already did that. and its working fine now. 

But STILL I was wondering if there was a way to reinstall system files without having to make a clean install?

---

