---
title: "X.Org can't use my Voodoo2."
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by Pxtl on 2006-06-20
Hey - I have an older machine, and I was elated to find that there is an XFCE version of Ubuntu, so I figured I'd set up that on the old box.   The problem is that the machine has an PCI ATI Rage Pro (which is a middling weak video card) and a 3DFX Voodoo2.  While Ubuntu has no truoble recognizing the old ATI board, the Voodoo2 is causing trouble.  I get "Failde to load module glide" in x.org.  After looking around, I tried to apt-get-install the tdfx driver, but was informed that I've already got that. My Linux console skills are pretty weak, and I don't know a thing about configuring x.org, so I'm pretty lost.  I'm considering pulling out the voodoo and using the ATI on it's own, but I've generally found that (at least on windows) the voodoo makes a much better 3d card than the 

Any help would be greatly appreciated.

---

### Post by dcstar on 2006-06-21
[QUOTE=Pxtl]Hey - I have an older machine, and I was elated to find that there is an XFCE version of Ubuntu, so I figured I'd set up that on the old box.   The problem is that the machine has an PCI ATI Rage Pro (which is a middling weak video card) and a 3DFX Voodoo2.  While Ubuntu has no truoble recognizing the old ATI board, the Voodoo2 is causing trouble.  I get "Failde to load module glide" in x.org.  After looking around, I tried to apt-get-install the tdfx driver, but was informed that I've already got that. My Linux console skills are pretty weak, and I don't know a thing about configuring x.org, so I'm pretty lost.  I'm considering pulling out the voodoo and using the ATI on it's own, but I've generally found that (at least on windows) the voodoo makes a much better 3d card than the 

Any help would be greatly appreciated.[/QUOTE]
Open a terminal, and enter:
```
sudo dpkg-reconfigure xserver-xorg
```
and try and select the other video card (assuming you only have it enabled in your system).

Restart the X-server with CTRL-ALT-Backspace and see what happens.

You can repeat the procedure as many times as you need.

---

