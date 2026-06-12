---
title: "Install fine, but won't load"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by JanosX on 2007-02-24
The install of Ubuntu seemed to go fine, but when I try to boot, it seems to crash.  I get the logo and load bar, everything goes as it should, but when it should load up the desktop I loose the video signal, it might actually be loaded but I can't see it.

I know I have a few obstacles, I run dual monitors, with a nVidia 7300GS, on a dell Dimension 8400 (3Ghz intel, 1 gb ram, blah blah) I am also triple booting XP, Ubunto, & OSX (I don't think triple booting is the issue, cause this was a problem long before that)

Any help would be appreciated, This is my first attempt with Linux, and really appreciate everyone willing to help us noobs out!

---

### Post by NosLycn on 2007-02-24
My first step would be seeing if you have any signal at all.  After it boots, try and alt-ctrl-f1.  If you get a console, you're one step up from where you were before.

After that, you can log in and check your /etc/X11/xorg.conf to make sure your screens are set up properly.

---

