---
title: "Hp Ml310 G2 &amp; Lsi Raid"
date: 2006-03-19
forum: Installation &amp; Upgrades
---

### Post by francismcphail on 2006-03-19
Hi all I'm in the process of attempting to install 5.10 to a HP ML310 G2.

The first part of the install runs ok, creating, and copying the inital base system to the disk (IDE), however upon removing the cd from the drive and rebooting I receive the following error.

Just wondering if anyone can advise on if a specific driver needs to be passed to the kernel on boot? (I can confirm /dev/hda1 (/boot) & /dev/hda2 (/) do exist (ext3).

> 
ALERT! /dev/hda2 does not exist. Dropping to a shell!

BusyBox ............ (more text here...)

/bin/sh: can't access tty; job control turned off


---

### Post by oucil on 2006-05-13
Precisely the same error and issue on a Compaq DL380 with the Smart Array. Anyone found any solution to this yet???

---

