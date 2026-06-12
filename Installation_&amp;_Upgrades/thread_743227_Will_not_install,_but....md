---
title: "Will not install, but..."
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by babyfoxx on 2008-04-02
Ok , I have tried to install Gusty on a Compaq Evo 500 Series, 512mb Ram  many different ways. I keep getting an error at 60% (dirty cd or bad drive). I have checked the disk on  two other PCs, and it's fine; I have changed out the CD drive with a newer one, and I still can not install. I have 2 Compaq Evo 500 Series, and it installed fine on one, but not the other, both spec are identical except for the video cards(Nvidia 5200 & problem PC is Nvidia ??later model 64mb ). I am trying to have a dual boot system (Windows & Ubuntu).

Can I install Ubuntu on a separate hard drive (via another PC), and install that hard drive into the (problem) PC? Then I would need to manually set up a GRUB file???
:confused:

TIA

---

### Post by ridgeland on 2008-04-03
I would try it.
A couple of things that might work.
Some PCs can boot from drive 1 or drive 2.
During install you might be able to tell it to install GRUB to drive2.

If you're playing with the drives just take the drive from Problem PC and put in the Trusted PC as the only drive and install there.  If they are identical except for nVidia then it should be fine.  Restriced nVidia drivers are always installed after first boot.  They get a very generic driver "nv" first which should work for both displays.  If not a minor tweak to /etc/X11/xorg.conf will probably fix it.

---

