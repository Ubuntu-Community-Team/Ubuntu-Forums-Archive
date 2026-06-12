---
title: "xschem not starting after Ubuntu update to 24.10"
date: 2024-10-20
forum: Installation &amp; Upgrades
---

### Post by clros2 on 2024-10-20
Good morning everyone,


[this is one of my first posts, I hope I'm in the correct forum section]


I've been using Linux Ubuntu in WSL under Windows for a while now.
I use it mainly for development with GCC and Rust but lately to do some experiments with the Open-PDK tools for creating VLSI projects.
The Open-PDK package also includes XSCHEM for creating schematics ([https://xschem.sourceforge.io/stefan/index.html](https://xschem.sourceforge.io/stefan/index.html))
I used it regularly but, after updating to Ubuntu 24.10, it no longer starts in graphical mode but only in text mode.
Reading on various forms I tried to give:


sudo systemctl reboot


WSL resets, I restart it and then I can use Xschem in graphical mode, but only for a few minutes because suddenly... it closes and also exits WSL.


What could be the cause?
Any suggestions?


Thanks everyone.

---

