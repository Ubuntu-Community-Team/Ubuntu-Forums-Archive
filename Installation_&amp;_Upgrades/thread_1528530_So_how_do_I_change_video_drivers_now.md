---
title: "So how do I change video drivers now"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by phil_hood on 2010-07-10
So ATI has dropped support for my card, and Radeon really doesn't meet my needs. So I need to try the alternatives.  I have an X86_64 system with an ATI X1550 family video card. I just upgraded to Lucid.  I installed the radeonhd package, but how do tell Lucid to use it?  The xorg.conf file is gone in Lucid, the hardware driver package only seems to be interested in proprietary drivers, not different open source drivers. How am I supposed to change this setting now?

---

### Post by phil_hood on 2010-07-11
So far as I can tell the only way to do this is to boot into single user mode, create an xorg.conf using X -configure, copy it to /etc/X11 where it belongs and edit it to use the desired driver. In my case unfortunately there does not appear to be a usable driver.  The default radeon driver works OK for simple things, but is badly crippled (no 3d, little acceleration).  The radeonhd driver seems to only support the HD cards (hence the name I take it).  Hand installing fglrx results in a driver that refuses to load because it "can't see any SUPORTED devices." My card is only 2 and a half years old, remind me to never buy an ATI card again.

---

