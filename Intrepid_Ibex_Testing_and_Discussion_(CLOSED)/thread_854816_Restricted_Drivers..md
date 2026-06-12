---
title: "Restricted Drivers."
date: 2008-07-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jaytothepeah on 2008-07-09
When I goto the main menu and click on restricted drivers, I have no choices, it says there are no restricted drivers and no choice to enable them.

I want a driver for an ati radeon xpress 100 and a synaptics touchpad that has a "four way" where a scrollwheel would be on a mouse.

Of course the open source driver is sufficient for youtube, but I can't enable any advanced effects.

---

### Post by RAOF on 2008-07-09
This is because the restricted video drivers (fglrx, nvidia) are undergoing major packaging changes - they're being split from linux-restricted-modules, nvidia is getting renamed, etc.

They're not done yet.

Also, there *isn't* a restricted driver for Synaptics touchpads, is there?  I get all my synaptics options from the (GPL'd) xserver-xorg-input-synaptics.

---

### Post by jaytothepeah on 2008-07-09
> **RAOF said:**
> Also, there *isn't* a restricted driver for Synaptics touchpads, is there?  I get all my synaptics options from the (GPL'd) xserver-xorg-input-synaptics.

I actually have no clue, I assumed that there was a driver issue. How do I access xserver-xorg-input-synaptics? Do I have to install it? The mouse options in the preferences menu offers nothing to make that button work and I just remembered that you can't scroll by sliding down the right side.

EDIT: I also have no sound though I did have sound during the first boot. The main menu offers a ton of options as well.

I am wanting to get into bug reporting and triage but I can't really make heads or tails of the launchpad site. I installed 8.10 to try to find bugs and I have a stable OS for a backup, I just actually think helping test an OS is a fun way to spend my working time. I guess I'm trying to figure out if I have found bug or if this is operator error stuff.

Other than those things I haven't haven't had any crashes.

---

