---
title: "GUI Won't Load"
date: 2005-02-03
forum: Installation &amp; Upgrades
---

### Post by Marlin1060 on 2005-02-03
First, I'm brand new to Linux and don't know much about how to edit files, find things, etc., so keep this in mind when making any replies or suggestions.

This is a new install on a very old machine. When I boot I get through everything until it says starting GNOME, then the screen goes blank, the monitor goes into sleep mode, and the keyboard is unresponsive (ctrl+alt+del doesn't reboot). If I run gdm from a prompt in recovery mode the same thing will happen.

In another post about gui problems it was suggested to sudo X -configure, so I tried that and it returns that it "Couldn't load shared library file for Glide,: "libglide2x.so".

The obvious questions are will fixing Glide fix my problem and if so, how do I get and install this file or package.

I believe that my install was default except that I had to manually partition the drives due to bios constraints.

Thanks
Marlin1060

---

### Post by Marlin1060 on 2005-02-06
Just to post the things I've done and the lack of progress.

apt-cache search glide listed the package for me to apt-get. Once it got installed I quit getting the error message when I'd run X -configure, but it hasn't fixed the problem of the system freezing.

---

### Post by Buffalo Soldier on 2005-02-06
[QUOTE=Marlin1060]This is a new install on a very old machine.[/QUOTE]How old are we talking about? Maybe telling a bit more about your system spec will make it easier for other people to help.

But I must say you're doing quite well alone. Most newbies would be screaming hell if no one answered their post in 10 minutes.

---

### Post by dsauxier on 2005-02-08
I had the same issue on a new (by my cheap standards) PC (Duron 1800)

I also went with the manual partition option since I have a couple of other OS's on this PC.

I was able to get it to work by re-installing ubuntu.

The installer asks about what resolutions you would like to have available.  The first time, I had selected a few in addition to the defaults.  When I reinstalled ubuntu, I left the defaults on that screen, and the GUI worked. :D

---

