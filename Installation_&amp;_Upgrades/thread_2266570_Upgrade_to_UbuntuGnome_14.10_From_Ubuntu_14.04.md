---
title: "Upgrade to UbuntuGnome 14.10 From Ubuntu 14.04"
date: 2015-02-24
forum: Installation &amp; Upgrades
---

### Post by benrob0329 on 2015-02-24
So, I’ve been using the Gnome desktop on Ubuntu 14.04 LTS. and I was wondering if there was a way to change what flavor of Ubuntu you upgrade to. So Ubuntu to UbuntuGnome, Kubuntu to Ubuntu, and so on. Right now I have a "Hodge Podge" (Ubuntu with ubuntu-gnome-desktop installed) vertion of Ubuntu.

---

### Post by dino99 on 2015-02-24
After the fresh installation made, you have the choice to choose an other DE via the xxx-desktop meta-package, aka ubuntu-desktop/kubuntu-desktop, ...
Note that you will get a "mixed" installation: the previous DE's installed packages are not automatically purged when you choose an other flavor. So the resulted system will be fatty and might ends with unexpected problems.
So if you want to try an other flavor, either do an additional installation if you have enough free space on hdd/sdd, or install over the installed one.

---

### Post by Bucky Ball on 2015-02-24
I'd go for installing another flavour on another partition. Take note, though: 14.10 is support for a couple more months. Unless you have a specific reason to upgrade to it, I'd stick with 14.04 LTS, supported until April 2019. LTS can upgrades directly to the next LTS, so, 14.04 LTS>16.04 LTS, leapfrogging the interim releases in between. 

Installing *buntu-desktop is NOT a good idea as, as mentioned, you will get all default apps and everything else, creating a real 'dog's breakfast' of a hybrid with bloated menus and a bloated system. It is equivalent to doing a full install of the other flavour ON TOP of the flavour you are already running.

If you want to try just the desktop environment, on the other hand, then just install the desktop environment. For instance, xfce4 for the DE used by xubuntu, lxde for the DE used by Lubuntu. You can try KDE, but I never have, although I know this is more complex than just installing kde from the repos. This won't drag in everything else. Simply log out, choose the DE session from the Sessions menu, login.

Good luck. ;)

---

### Post by benrob0329 on 2015-02-24
I will probably just re-install Ubuntu with the UbuntuGnome flavor then. BTW, I uninstalled all of the Unity specific applications after switching DEs.

---

