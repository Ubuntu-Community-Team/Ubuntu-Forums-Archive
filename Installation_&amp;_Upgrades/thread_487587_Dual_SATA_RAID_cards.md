---
title: "Dual SATA RAID cards"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by iamplasma on 2007-06-29
Hi all,

I'm in a bit of a pickle, and really don't know where to ask this.  I'm setting up a new home file server running Ubuntu 7.04 server, which is going to have 8x500gb Samsung hard drives.  In order to run these drives, I'm using two SIL3114-based SATA RAID cards, each of which can host four SATA drives.

The big problem I'm having, however, isn't on the ubuntu side, but rather the hardware side (it seems).  The computer seems to vary the number of SATA cards it can see on a purely random basis.

In short, one moment the system will only recognise there being one card installed.  No number of reboots will change this.  I can then swap one card from one slot to another and it might appear, or it might not.  I had the computer consistently recognising both cards, and so all eight drives, but immediately after moving it from one room to another (without making any hardware changes), it's back to only seeing one.

For the avoidance of doubt, I should make it clear, I've swapped in an entirely different mobo/cpu for the system, and it STILL has these problems, so I don't believe it is a problem with faulty hardware.  I changed from an Athlon 1Ghz to a Duron 1.1Ghz, so admittedly somewhat similar setups, but I can't see that being relevant.

Has anyone else here any experience with this sort of thing?  I'm really stuck for ideas here.

TIA

---

### Post by negated on 2007-07-04
Make sure you have the latest BIOS for the new motherboard you've installed the cards into, and you've updated the BIOS/firmware for each card.

Also, according to Samsung's documentation, if you have SATA300 drives (which I am assuming you have if they are 500GB drives) they may have trouble connecting to SATA150-only cards (like the SIL3114 based cards), and they provide a utility at [www.samsunghdd.com](www.samsunghdd.com) so you can change their drives to work in SATA150 mode. 

Good luck!

-S

---

### Post by t4thfavor on 2007-07-06
Certain sata cards will only allow one card per pci bus. In short if your card does not explicitly say that it can live in peace with another raid card, it most likely will not. Promise cards have a few models that say they can live side by side without conflicts. 

I have a primise fastTrak TX4310 that has 4 ports and can have a max of two cards per system. It retails on newegg for about 109.00 USD.

---

