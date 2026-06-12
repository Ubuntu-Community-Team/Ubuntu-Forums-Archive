---
title: "After upgrade - laptop needs power plugged in!"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by Thorney on 2010-10-07
Hi all,

I upgraded Ubuntu and now it will "sometimes" boot if I choose an old kernel - but often will either freeze or restart if I don't have the power plugged in.

Whenever I'm away from a power chord I have to use windows! This upsets me!

Any ideas?

---

### Post by cgroza on 2010-10-07
Did you upgraded using a Live CD or via Update Manager?

---

### Post by Thorney on 2010-10-07
> **cgroza said:**
> Did you upgraded using a Live CD or via Update Manager?

Update Manager

---

### Post by mörgæs on 2010-10-07
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by Thorney on 2010-10-31
Well still no luck but I might as well document my trials...

I initially thought it must have been the NVIDIA binary drivers not talking with the new ubuntu default kernel - so I've got the latest drivers and that didn't seem to change anything.

Currently without power this is what happens for each kernel:

2.6.35-22-generic: loads with the Ubuntu 10.10 screen, then stops at a text login on tty1. Ctrl Alting to F7 shows coloured log messages with a few fails visible - VirtualBox kernel modules not found and check syslog for diagnostics. The last entry is "Starting TiMidity++ ALSA midi emulation.


2.6.35-23-generic: Boots through to gdm login screen. I enter my password and click login and the computer freezes (No mouse or keys, can't change tty, screen just stays the same). Sometimes the login audio starts playing and it loops over and over a small section of it.

2.6.36 mainline (30/10/2010): Gets to the text login. Just logged in and did a dmesg|tail - NVRM errors abound (mismatched of course). Uninstalling NVIDIA driver, doing a dpkg-reconfigure xorg, Xorg -configure (+move) gets me to the login screen. I enter my password etc and am in to my desktop... I open rhythmbox play a song and it cuts out midway through. I open a terminal, although  I can't type into it... can't switch between windows, can't see them in the taskbar... although they both seem responsive (menus in the terminal app worked, music will play)

With power going to the "normal" kernel that is default in the repos (2.6.35-23) now without NVIDIA works fine.

Without power in the normal kernel (without NVIDIA) it freezes (still).

Without power using the mainline kernel (without NVIDIA) it works FINE - no problems at all.


I tried each of these 4 or 5 times without the power cable plugged in, the default kernel would get sometimes right into gnome but it never "worked", and the mainline kernel never failed.

---

