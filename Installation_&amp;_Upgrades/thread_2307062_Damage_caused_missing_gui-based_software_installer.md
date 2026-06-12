---
title: "Damage caused missing gui-based software installer"
date: 2015-12-21
forum: Installation &amp; Upgrades
---

### Post by SimonHGR on 2015-12-21
Greetings all,

Something odd happened to me (well, my system) earlier today. The result is that several programs were unloaded from my system. Most notably, the GUI based software installer. I don't, unfortunately, remember its name, but it used to have an icon that looked like an orange shopping bag (carrier bag, grocery bag) with a white "A" on it. This installer used to let me install .deb packages (such as the Oracle originated VirtualBox) and would do so directly from a browser download.

However, this is now gone, and I'm assuming / hoping that I can get it back with an "apt-get install" operation, but I don't know what it was called, or what package it was part of.

Can anyone help?

(And if anyone cares, the original problem was very odd, I clumsily tried to install a 32bit version (oops, I have a 64bit machine) of the latest (version 5.something) Virtualbox, direct from Oracle) and the aforementioned now-missing software said it couldn't install it because it conflicted with the existing (version 4.something) verison of Virtualbox. So, I told it to remove the existing VB. That promptly removed VB, along with (at least) the installer GUI program, and gnome-terminal! I managed to get gnome-terminal and virtualbox back from apt-get, but can't find what the GUI tool is...

TIA,
Simon

---

### Post by grahammechanical on 2015-12-21
It is called Ubuntu Software Centre & the package name is software-center. 

Regards.

---

### Post by SimonHGR on 2015-12-21
Thanks! Very odd how it got messed up, but that's great, it's back where it belongs now :)
cheers,
Simon

---

