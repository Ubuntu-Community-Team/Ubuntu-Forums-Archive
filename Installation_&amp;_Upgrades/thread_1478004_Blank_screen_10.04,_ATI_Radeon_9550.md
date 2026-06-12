---
title: "Blank screen: 10.04, ATI Radeon 9550"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by sumindless on 2010-05-09
Hey guys, just thought I'd throw in some extra information.  I too am having the same problem, as soon as X tries to load my screen just goes blank. I have an ATI Radeon 9550.  At first I tried switching between VGA and DVI as well but upon ruling that out, I switch to my on-board video card and that is working thus far, but I'm trying very hard to figure out a way to be able to switch back.  Anyways I'll check back in later on if I have any new information I will post, and thanks in advance to anyone else who does the same.

Mindless

---

### Post by Iowan on 2010-05-09
Moved to new thread.
[Original]("http://ubuntuforums.org/showthread.php?t=1477923")

---

### Post by Catharsis on 2010-05-09
Did you try booting with "nomodeset"?
1) Hold down Shift while booting to get the grub menu.
2) Press 'e'. Type "nomodeset" after "quiet splash".
3) Ctrl+x to boot.

---

### Post by Red3 on 2010-06-03
I have a 9550 as well, and after installing 10.04 encountered similar problems when using the radeon driver.  The following settings worked well for me:

/etc/X11/xorg.conf

```
Section "Device"
                    Identifier     "Radeon 9550"
                    Driver         "ati"
                    BusID          "PCI:1:0:0"
                    Option         "XAANoOffscreenPixmaps"
                    Option         "EnablePageFlip"
                    Option         "TripleBuffer"    "true"
EndSection

Section "Monitor"
                    Identifier      "LG"
EndSection

Section "Screen"
                    Identifier      "Default Screen"
                    Device          "Radeon 9550"
                    Monitor         "LG"
EndSection
```/etc/modprobe.d/radeon.conf

```
options radeon modeset=0
```

---

