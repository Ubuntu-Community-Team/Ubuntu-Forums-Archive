---
title: "LiveUSB Graphics Corruption and updating."
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by Gideon on 2011-06-01
I've been trying to run the 11.04 liveusb on my laptop (not installing yet, just trying to get the thing to run) and things have been failing pretty miserably.

The essentials. Presario v6000, Turion 64 dual core, 4gb ram, Geforce 7150M/nforce 630M, using ubuntu 11.04 amd64. Screen native res 1280x800.


So far, if I boot straight in, I get obnoxiously massive graphics corruption, which appears to be something to do with nouveau (as has been posted in other threads.) using nomodeset or nouveau.blacklist lets me boot into gnome 2 at 1024x768 (which doesn't suit my needs as what I was wanting was to do a full on unity test without having to completely reinstall the laptop.)

What I'm basically looking for here is either a nouveau fix, or some detailed instructions for adding other nvidia drivers to the liveusb, or forcing the system to use them rather than nouveau (if I blacklist nouveau, it can't even detect there's an nvidia gpu there.) I did try a full system update, but it fell over due to lack of space (which I assume is a mounting issue as the stick itself has buckets of free space)

---

