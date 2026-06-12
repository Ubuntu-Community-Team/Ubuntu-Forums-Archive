---
title: "Xserver broken after update"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by Jc1991 on 2007-02-17
I've just finished updating my Xubuntu install from 2.6.15-27-386 to 2.6.15-28-386, and updating to the newest nVidia drivers, both via Synaptic. After restarting my computer I can't login to the Xserver at all; when I enter my username and password the Xserver reloads. (The same things occurs even in recovery mode.)
I receive no errors on booting Xubuntu, and no errors when the Xserver reloads.
Does anyone have an idea of what might be wrong, and how I might go about fixing it? Thanks in advance for advice.

---

### Post by K.Mandla on 2007-02-18
Try changing "nvidia" to "nv" in your xorg.conf file, just as a testing measure. You can change it back later if it doesn't help solve the problem.

It's possible that the issue is tied to the latest kernel upgrades; read the sticky announcement in blue at the top of this subforum and see if that sounds like it might be your problem.

---

### Post by Jc1991 on 2007-02-18
Changing nvidia to nv didn't fix the problem.
I'm not entirely sure about the problem listed in the sticky, but that doesn't seem to be what's wrong.

---

