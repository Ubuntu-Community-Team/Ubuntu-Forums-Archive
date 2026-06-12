---
title: "Where do I find older package versions?"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by chlechte on 2008-06-24
Hi, the recent upgrade of the xserver broke something on my hardy system. 

I'll describe the problem below, but my real question is, how can I downgrade to previous versions of the x11 packages, so that I can continue to work? I do not have the old .debs in my cache anymore.

The problem is the following: the whole x server crashes when a certain software (IDL by ITT Visual Inforamtion Solutions) tries to open any x11 window. This only happens when I use the NVIDIA legacy drivers (downloaded directly from NVIDIA, not the official Ubuntu package) for my video card. Before the June upgrade, everything worked fine.

Regards, Carsten.

---

### Post by chlechte on 2008-06-24
Update: the solution for my original problem was that the update seems to have overwritten a special libglx from the NVIDIA drivers.

But my main question remains: how can I get back to an old version of a package that is not listed in e.g. synaptic's Properties->Versions list anymore?

Do I need to keep everything locally in my apt cache if I want the ability to go back a few versions? Or are there official "historical" servers?



Regards, Carsten.

---

