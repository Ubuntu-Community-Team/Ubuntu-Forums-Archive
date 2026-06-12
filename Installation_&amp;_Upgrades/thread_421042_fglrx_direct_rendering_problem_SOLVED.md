---
title: "fglrx direct rendering problem SOLVED"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by jazzroy on 2007-04-24
Hi,
for all the people who's in struggle with fglrx drivers to work, I'll explain the VERY simple solution I've found.

If you have tried with envy script, or through Enable restricted drivers, or even through Synaptic, and everything seemed to work fine, but the fglrx command answered with the awful MESA drivers info, then probably you had the same problem I had.

So yesterday I accidentally opened the linux-restricted-modules-common file and discovered that fglrx was disabled! Commented it, and WOW direct rendering was on!

So, the instructions are:

sudo gedit /etc/default/linux-restricted-modules-common

search for a string like this:

DISABLED_MODULES="fglrx"

and comment it like this:

# DISABLED_MODULES="fglrx"

restart X and enjoy your card 3D acceleration :)

---

