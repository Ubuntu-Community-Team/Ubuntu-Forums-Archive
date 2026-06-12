---
title: "Inadequate graphics capability for upgrade"
date: 2015-11-23
forum: Installation &amp; Upgrades
---

### Post by RetroProf on 2015-11-23
When I attempt to upgrade to version 12.04 the upgrade fails with a message stating that my graphics card is not adequate to the demands of this version of Ubuntu.  My graphics display adaptor is AMD760G, part of a basic chipset for the motherboard.  Just what capabilities do the versions of Ubuntu 12.04 and above require?  It appears that I may not be able simply to install a new graphics card in order to solve the problem, but if I can I need to know what to look for in a new card.

---

### Post by ajgreeny on 2015-11-24
As you are trying to upgrade to 12.04 (from what version?) it is likely that your current system runs gnome 2.
The unity desktop which is the default for 12.04 requires a very good 3D graphics card and can often run extremely well using the on-board graphics chips of modern systems, for example just about all recent Intel CPUs with integrated graphics will run unity with no problem.

I have no recent experience of AMD graphics so can't tell you anything useful about that AMD760G chip or if it can use the fglrx driver from AMD, but judging by the error message you see you should probably consider using one of the alternative DE systems such as Xubuntu, Lubuntu, or Ubuntu-Mate, itself a fork of gnome 2.

---

### Post by grahammechanical on 2015-11-24
Ubuntu with the Unity interface requires a graphic adapter that can do accelerated 3D rendering in its hardware. It should have its own memory chips of 256 MB minimum but I would say 512 MB or preferably 1GB.

What expansion slots does that motherboard have? PCI is better than AGP and PCI-Express is better still. You want to look for OpenGL support. The closer to OpenGL 3.1 the better. But you should really try out the alternatives to Ubuntu as recommended by ajgreeny.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Regards

---

### Post by tgalati4 on 2015-11-25
Or try installing Linux Mint MATE 17 based on 14.04 or the current version of Ubuntu MATE.

---

