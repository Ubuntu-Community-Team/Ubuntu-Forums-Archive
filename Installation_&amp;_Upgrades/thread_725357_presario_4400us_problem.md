---
title: "presario 4400us problem"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by Paul86fxr on 2008-03-15
I have installed 7.04 and 7.10 many times, I have a compaq presario 4400us, everything starts fine, welcome screen, install safemode etc. I have tried to install it using every option listed, I end up with a blank screen, no mouse pointer, no curser, just blank. tried proven distros, i.e mint, gentoo, college linux etc. and it stops at the same spot, I watch everything load through verbose mode and all is well, one part states "FWH not loaded or something close to that , it passes fast so i cant read all of it. Is there any "VESA VGA" problems known?  or anyone had problems with compaq? runs XP fine(sadly):)

---

### Post by Pumalite on 2008-03-15
Memory? Graphics?

---

### Post by Paul86fxr on 2008-03-15
128meg RAM  32MEG vesa adapter

---

### Post by Pumalite on 2008-03-15
Try Xubuntu Alternate CD> [http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)
If that doesn't work, stick to smaller distros like Puppy or DSL
You cannot boot a Live CD with that RAM

---

### Post by ctsdownloads on 2008-03-15
Just a hunch, I bet it relates to this:
[https://bugs.launchpad.net/ubuntu/+bug/82662](https://bugs.launchpad.net/ubuntu/+bug/82662)

I think this is the same integrated card you are using. 

> Between the boot loader and the start of X, there is a blank screen. Switching to a console will show an extremely large font, so the resolution must be off. Also, on a shutdown, after X is closed, the screen goes blank again.

If it was me, I might see if getting a cheap PCI video card might be an option, only to turn off the integrated card from within your BIOS. I only say this for the sake of troubleshooting of course.

---

### Post by Paul86fxr on 2008-03-15
Ok, I appreciate the help!

---

### Post by ctsdownloads on 2008-03-15
Have to agree on the RAM point, I like PuppyLinux myself, it is a great distro for both Notebooks and desktops. Light, fast and very simple to use right out of the gate.

---

### Post by Paul86fxr on 2008-03-15
Ok, its an Intel 82815 adapter, I never thought about the RAM for the live CD, makes sense though. Thanks everyone.

---

