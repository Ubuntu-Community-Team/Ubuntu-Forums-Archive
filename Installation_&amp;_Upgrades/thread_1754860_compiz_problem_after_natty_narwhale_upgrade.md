---
title: "compiz problem after natty narwhale upgrade ?"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by thomasbsm on 2011-05-10
Hi

I have updated my Ubuntu installation to natty narwhale and after a reboot the desktop started to look like the attachment Screenshot.jpg

The error does not appear when I choose ubuntu classic instead the windows miss the top bar where the X (close button) is placed.

Alt+Tab does not work, and suddenly I cannot write in the active program.

Thomas

---

### Post by wilee-nilee on 2011-05-10
Since you have installed the config manager what have you changed, are you trying to get the cube?

Do you know the graphic card, and have you in the past had to install drivers, and have you looked in menu-system-admin-additional drivers?

If you don't know the card run this in a terminal and post it, or at least you will know.;)

lspci | grep VGA

---

### Post by thomasbsm on 2011-05-11
Hi wilee-nilee

There are no additional drivers available and I never used additional drivers.

My graphic card is ATI mobility radeon x300.

The cube is deactivated.

---

### Post by thomasbsm on 2011-05-23
I have tried to research the problem a little further.

When I use
```
metacity --replace
```the window title bar recovers but I still have the same problem when I reboot. In earlier versions of Ubuntu you could choose the visual effects level, but I cannot find it after the upgrade to natty narwhale?

Ubuntu unity has the same problem as earlier shown

Thomas

---

