---
title: "Can't open a terminal"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by sandys on 2007-08-05
Hi There, 

I have a really odd problem I have installed Unbuntu 7.04 (x64 version) on my system, the install went smoothly etc. but when I try to lauch a terminal nothing happens, I get the 'Starting Terminal' notification in the bottom bar but no terminal ever appears?

Anyone have a clue whats up?

I can launch firefox and other apps no problem but I can't get a terminal up which is a big problem.

System specs are

Socket 754 AMD 64 2800
Mobo is a Nvidia 6100 based board with integrated Audio/video/lan etc.
Nvidia 6200 Turbo cache.

I wonder if the dual gpus might be an issue but as far as I am aware the motherboard one is off.

Cheers

---

### Post by majed on 2007-08-05
Try ALT+F2 to get the launcher window, then run x-terminal-emulator from there.

You can also try running xterm from there.. if either work, u know the problem is something in the configuration of the menu or the default apps.

---

### Post by sandys on 2007-08-05
Cheers,

Just thought of running an xterm myself, obvious really :lol:

It seems I have a problem with gnome-terminal as I get the following error trying to launch one.

gnome-terminal: error while loading shared libraries: unexpected PLT reloc type 0x00

Any ideas how I fix that.

---

### Post by majed on 2007-08-05
This is usually a  build problem. u can reinstall the terminal using synaptic.

---

### Post by sandys on 2007-08-05
:cool:

Yup thats fixed it, thanks for your help.

I'm slowly learning.

Cheers.

---

