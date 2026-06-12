---
title: "problems installing netbook on old laptop"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by mikmikmikmik on 2011-09-24
im trying to install ubuntu 10.04(actually it might be 10.10) on an old laptop, booting from cd. It loads all the way up to right before the "try ubuntu" or "install ubuntu" screen. it comes up with a desktop background, top menu bar with 2 icons(i think) and a mouse that i am able to move. nothing else happens unless i force shut-down the computer. :(

help?

---

### Post by mikmikmikmik on 2011-09-24
im pretty sure its 10.10

---

### Post by ajgreeny on 2011-09-24
How old a laptop and what spec?

---

### Post by mikmikmikmik on 2011-09-24
gateway solo 5300
might be 10 years old

also hoping(more like needing) it to support netgear wn511b wireless adapter

um, 126mb ram might be part of the problem :(
old linux version that needs only 126mb?

---

### Post by oldos2er on 2011-09-24
What are the hardware specs? 

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by ajgreeny on 2011-09-24
You might just about get Lubuntu to run, but even that will be slow, I think.  Look also at Puppy Linux.

The netgear adapter may work, but depends on the chip it uses.  I have a WG511v2 with marvell chip which is good with ndiswrapper.  Run sudo lshw -C network to see the chipset of yours.

---

### Post by mikmikmikmik on 2011-09-24
thanks! ill try both

---

