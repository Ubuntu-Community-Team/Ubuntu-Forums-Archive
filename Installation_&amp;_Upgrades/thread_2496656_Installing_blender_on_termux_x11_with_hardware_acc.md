---
title: "Installing blender on termux x11 with hardware acceleration"
date: 2024-04-07
forum: Installation &amp; Upgrades
---

### Post by danielkotzer on 2024-04-07
Is there a way to install blender on termux x11 with hardware acceleration?
Anyone with experience please help.

---

### Post by Holger_Gehrke on 2024-04-07
Is [this]("https://termux.dev/en/") the termux you're talking about ? If so, then a) this post belongs in "other Discussion/Other OS" and b) "Termux is a terminal emulator application for Android OS which can be extended by packages of ported common GNU/Linux utilities."; to run graphical applications you need an X-Server for Android. There are several, but AFAIK none of them have any hardware acceleration. You'd also have to port Blender yourself since there's no pre-compiled package for it in the repositories on 'packages.termux.dev'.

Holger

---

