---
title: "Ubutnu 7.04 x64 doesn't install with remap feature enabled by bios."
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by sonnet on 2007-05-18
As per title I'm having problems to install ubuntu 7.04 x64bit version if I have "memory remap" feature enabled by bios.
The fact is that I have a Conroe cpu with an Asus P5B deluxe wifi (mounting a p965 intel chipset) and 4 modules of 1gb of ram,so a total of 4GB of ram.
I need to have memory remap enables because is the only way the system will see all the 4GB of ram.
If I disabled memory remap the system will see only 3gb of ram,wasting 1gb to address it to pci device .
Does anyone have any clue tips or help to sort out this problem?

---

### Post by ©TriMoon® on 2007-05-18
Try do the memtest from the install menu of your CD and see how much it "sees" when you disable memory remap.
It could well be that linux doesnt need this option to see the full memory as opposed to windows OS...

---

### Post by sonnet on 2007-05-18
If I disable the remap function the system only see 3gb.
Is a problem already discussed.
I can't diable remap function as it's the only way Windows Vista 64 can see the 4gb of ram.
As I have it also installed, I need to keep memory remap enabled.

---

