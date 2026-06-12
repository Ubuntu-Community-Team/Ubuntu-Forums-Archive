---
title: "after screensaver auto-complete entries NOT shown"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by GeorgeVita on 2009-09-30
Auto-complete entries (overlays?) disappear after resuming screensaver.

I am using:
EeePC 1000H which has: Intel Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
Ubuntu 9.10 (fully updated)
System > Preferences > Screensaver set to 1 minute (for faster tests)
running Firefox

Usually pressing any key into a field like 'address', 'google search', 'ubuntuforums search', 'login fields', etc. auto-complete feature suggests some entries from history. After resuming screensaver this feature does NOT show the suggested entries. You can see cursor flickering which means 'box is drawing but not shown'.

Minimize - Maximize (or close and run again) firefox solves this problem.

Do you have the same problem?

To test it: run firefox, wait for the screensaver to appear, leave it running for a minute, move mouse/touchpad to resume, type any letter into 'firefox address field', auto-complete works or not?

Thanks in advance,
George

---

### Post by GeorgeVita on 2009-10-01
... the same on old P4 desktop after 9.10 beta (new installation) with:
VGA: ATI Technologies Inc RV350 AS [Radeon 9550]

Problem appears with 'normal' or 'extra' visual effects on both PCs tested.
NO problem using 'none' visual effects.

EDIT: [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/440784](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/440784)

G

---

### Post by GeorgeVita on 2009-10-07
The same problem exists on today's **UNR** live (+recent updates) using:
System > Appearance > Visual Effects > Normal OR Extra

pc: EeePC 1000H
kernel: 2.6.31-12-generic #39
gnome-screensaver: 2.28.0-0ubuntu1
netbook-launcher: 2.1.10-0ubuntu1
firefox: 3.5.3+build1+nobinonly-0ubuntu3

---

