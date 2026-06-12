---
title: "Feisty bit me"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by diskinetic49 on 2007-04-23
I'm not really sure how this problem sprang up, so I'll try to be as methodical in description as possible.  When I have upgraded my Averatec 3700 laptop in the past, I usually do a backup/clean install, but this time, I saw the "upgrade" option on the manager and took it.  the system ran well enough, but the screen resolution was way off.  I read a few posts and re-ran the resolution assignment from the CLI, making no preferential resolution choice, since that has worked in the past.  Well, that TOTALLY fried the install.  So, I thought, "No harm, I'm backed-up, so I'll just clean-install."
Well, now the Live CD won't read properly (if at all) and X seems to be chopping along at one frame every five seconds.  To the point:  After signing in, the main desktop takes ten minutes to load, and the cursor requires serious planning ahead to move accurately.  My CDs (I tried Kubuntu, Xubuntu,and even a reversion to 6.10  too) are good burns from another box, and I'm quite used to installing hitchless, so I hope it isn't just user error (although I'm nowhere near advanced enough to rule it out).
Any hints?

---

### Post by sirrommit on 2007-05-05
I had a similar problem when I upgraded my averatec 3700 to Feisty.  I haven't completely figured it out yet (locks up every time I try to run a graphics intensive package like flightgear) but I got it quite useable by manually changing the /etc/X11/xorg.conf file by replacing:

Section "Device"
        Identifier      "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Driver          "via"
        BusID           "PCI:1:0:0"
EndSection


with

Section "Device"
        Identifier      "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Driver          "via"
        BusID           "PCI:1:0:0"
        Option          "DisableIRQ"
        Option          "VBERestore"    "true"
EndSection

I am not familiar enough with linux to be able to tell you all the repercussions of this, but it did get me back up and running.

---

