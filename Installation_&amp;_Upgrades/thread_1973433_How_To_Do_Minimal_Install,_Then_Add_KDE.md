---
title: "How To Do Minimal Install, Then Add KDE?"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by buzzingrobot on 2012-05-04
Can someone suggest a way to do a rather minimal 12.04 install with the intent of later installing KDE?

I installed the KDE-Full package  yesterday and like it.  To avoid the mixing and matching of everything, I have been trying repeatedly to install Kubuntu. However, Kubuntu install CD's crash before displaying the grub menu. (So do straight Ubuntu CD's,for that matter.)  The installation starts from a USB drive but the installer either crashes during manual partitioning or when the process indicator displays 86% (it stalls as Ubiquity hits 100% of CPU).  And each failed USB install renders the USB drive unbootable, forcing me to recreate it each time.  So far, I've made 7 attempts.  

Oh, and the installer worked well enough to wipe my Ubuntu install.

I can get Ubuntu 12.04 installed if I install 11.10 first and then dist-upgrade. (A kernel bug crashes installs with my video card.  It doesn't get far enough to add kernel options.)

I don't want to go those lengths again, but I would if I can install a minimal Ubuntu before I add KDE.

---

### Post by zvacet on 2012-05-04
Read [this.]("https://help.ubuntu.com/community/Installation/LowMemorySystems")After installing xorg install KDE by typing

```
sudo apt-get install kubuntu-desktop
```

---

