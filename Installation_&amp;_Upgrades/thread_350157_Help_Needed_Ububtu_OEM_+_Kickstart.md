---
title: "Help Needed *Ububtu OEM + Kickstart"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by rndinit0 on 2007-01-31
Here is the scenario:
I have 500 retired PC's that are going to be sold.

The challenge:
We cant install a commercial OS, cause that would cause licensing issues.
We need to have it completely automated
The PCs don't support PXE boot. (workaround floppy?CD?)
Some PCs have the bios locked (fallback to floppy, worst case reset bios)

What we are currently doing:
I have installed Xubuntu OEM, took an image of it using [G4U]("http://www.feyrer.de/g4u/"). 
Problem is when we restore the pc's it requires user input and a connected keyboard.

What we want to do:
Somehow someway, deploy 500 PCs, using an auto install OEM *Ubuntu CD/Floppy 
(I can set up a deployment server) 
The process would have to be completely automated, no input required. And preferably once the PC is deployed it would automatically shutdown.

Information about the retired PCs:

Their all the same hardware specs, with the exception of had-drive size ranging from 10gb -> 40gb.
They all have built-in NICs

Any Ideas?

---

