---
title: "Upgrading to 22.04.3 LTSe from 14.04 LTS"
date: 2024-01-07
forum: Installation &amp; Upgrades
---

### Post by esarratt on 2024-01-07
I am going to upgrade to 22.04.3 LTSe from 14.04 LTS (my current version).

Can I do a upgrade install or do I need to perform an install from scratch?

Thank you for your help.

Here are my computer's specs if interested:

Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Stepping:              10
CPU MHz:               800.000
BogoMIPS:              4521.96
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              3072K

---

### Post by deadflowr on 2024-01-07
Fresh install.
You currently have 32-bit system ( i686)
and Ubuntu has dropped that, so only way for you to get 22.04 is to install it clean.

---

### Post by esarratt on 2024-01-07
Thanks!

---

### Post by oldfred on 2024-01-07
If system is that old, you probably need a lightweight flavor.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

I use Kubuntu which is more of a mid-weight flavor but has worked on older system when I used SSD. Old HDD was slow.

Desktop GUID has changed, so you will get different gui anyway. Ubuntu when from Gnome2, to Unity (2010-2017), to newest Gnome. But that now requires a newer laptop or older one upgraded or with higher specs.

---

### Post by guiverc on 2024-01-07
You didn't specify if this is a Desktop (with GUI) or Server (text only) install, as that can influence options available.

I have a few systems I use in specific roles, eg. as a media player; and I don't *release-upgrade* them very often (*I apply upgrades when the device is next used, but that's about all*), and one of those was running Ubuntu 16.04 LTS which reached EOSS long ago, so my intention was a non-destructive re-install (*as it was a desktop system*)

What I considered was

- I used Ubuntu Desktop, which was the Unity 7 desktop for 16.04 (*same as your 14.04*), so upgrading to the current 22.04 LTS would have a GNOME 4 desktop instead; I was pretty sure I didn't want that, so it was what desktop I'd use instead...

- Ubuntu 18.04 LTS had then still not reached EOSS (*this was last year*) and thus I could *release-upgrade *to 18.04, then reboot & do it again to 20.04, reboot & do it again to 22.04... That would have taken ages (*days with my internet*); where a *non-destructive re-install* would have accomplished what I wanted (*including desktop change*) in under 30 minutes ! (*excluding time for me to decide which flavor/desktop to use*)

I sat on my decision of *what flavor of Ubuntu to install, ie. what desktop to use instead of Unity 7*, for more than nine months, as for that install I actually liked having Unity 7 

In my case I never reached the decision as to what to install, instead using that box as an example in a support question on *askubuntu.com *to prove installs were possible on releases in EOSS (16.04 being EOSS, 18.04 too), but assuming you don't get stuck at what to re-install over your old system as I did, I've written about it [here]("https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533"); I'd recommend a non-destructive re-install to upgrade if desktop system.

Non-destructive re-install is intended for Desktop installs (as system directories get wiped, you'll lose server configs which can get stored in system directories where desktop apps store in those in user directories)... and is easiest with *flavors* (where 'universe' or the community repository is *enabled* by default), but its an option I often use.

What apps you have installed will of course influence this; a lot has changed since 2014 & thus you should deal with these first (python2 is gone, Qt4 gone, etc), and this install method is best without 3rd party apps, so you'll need to consider what 3rd party apps you use, and if they allowed for such upgrades (or not).

---

