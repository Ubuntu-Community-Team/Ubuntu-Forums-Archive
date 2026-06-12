---
title: "Remove programs"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by TDragon on 2008-08-18
I would like clean house (only keep applications that I use) and remove the Palm OS and Evolution Mail software (have a corporate Blackberry and only wish to use Thunderbird for personal mail), but I've noticed that there are quite a few packages tied to these installs. Can anyone tell me how I can safetly remove these programs w/o damaging current installs (I have a lot of the base pkgs, including Firefox3, Thunderbird, Compiz-Fusion, Emerald, AWN, wicd)?

---

### Post by mikewhatever on 2008-08-18
You should start with the minimal installation and then add thngs you want on top. Removing Evolution and it's components will uninstall a lot of useful things. That's the way Ubuntu works.

[http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)

---

### Post by TDragon on 2008-08-19
I just recently did a fresh install. Are there any alternatives?

---

### Post by mikewhatever on 2008-08-19
You could remove ubuntu-desktop reducing your system to CLI and then install just the graphics and the programs you need.

Edit: I'd suggest avoiding gnome and going with xfce4.

---

### Post by Cheesehead on 2008-08-19
The three easy steps to cleaning house:

WARNING: Before we start, remember that Ubuntu releases are carefully balanced to provide the majority of apps that people want without a lot of extra bloat, with packages that don't conflict, and the smallest number big bugs. When you change packages, you might degrade the usefulness or stability of your system. Okay, on to the fun....


STEP 1) UNINSTALL ubuntu-desktop. It's just an umbrella to ensure you get the entire Gnome desktop, with all the bells and whistles. Since that's not what you want, you *can* safely remove it. 

Remove it using Synaptic or the command line: ```
sudo apt-get remove ubuntu-desktop
```


STEP 2) REMOVE LOTS OF PACKAGES. This is actually the fun part (no kidding!), though it can be quite time-consuming.

In Synaptic, click on the column header to sort the green boxes (installed packages). Select each package you want to try to remove - Synaptic will warn you before danger occurs...er, I suggest you heed the warnings. Every so often, click 'Apply' to uninstall the packages you're sure you don't want.

If you can't tell the difference, then good riddance to the packages. If you want something back, but can't remember the name, Synaptic has a 'File --> History' function that will tell you what you removed.

If the package starts with 'lib', such as 'libfrobozz', then leave it alone. We'll take care of those in step 3.


STEP 3) CLEAN UP ORPHAN PACKAGES. Synaptic doesn't remove orphaned dependency packages...if application "frobozz" is the only one that requires package "libfrobozz", Synaptic won't remove libfrobozz automatically with frobozz! Cleaning out these orphans can be very satisfying, though most take up little space. Use the command line: ```
sudo apt-get autoremove
```


IF YOU CHANGE YOUR MIND, you can always reinstall the whole Gnome desktop, and all the associated applications, using Synaptic or the command line: ```
sudo apt-get install ubuntu-desktop
```

---

### Post by mikewhatever on 2008-08-20
> Before we start, remember that Ubuntu releases are carefully balanced to provide the majority of apps that people want...

Do you realize this is simply not possible?

---

### Post by Cheesehead on 2008-08-20
> **mikewhatever said:**
> Do you realize this is simply not possible?
No. Because it is possible. The current popularity of the Ubuntu distros reflects that possibility.

---

