---
title: "Serious Feisty probs (alt-cd not working)"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by ZephyrQ on 2007-07-13
I have tried the alt-cd install (text installer), all the flags (noapic, etc.), and even disabled the mounting of a volume that I thought might be hosed (hdd).

This time it froze on "Validating console-terminus".

To Recap:
I tried to install the Feisty cd after messing up the system (Dapper) when I used Gparted to make room for backups...

I have done multiple installs, but they all freeze.  This time, disabling the drive that I believe might be a problem, the installer actually made it past the partitioning/formatting stage.

My drive layout is as follows: hda (60g)--several partitions, 3 of which I have to retain/save.
hdb (8g)--backup partition (which has to be saved--contains work stuff) and swap
hdd (30g)--I deleted a partition with Gparted on this drive and is what started the whole mess.  I suspect this drive my be fubar'd.

Help please?

---

### Post by ZephyrQ on 2007-07-14
Just to add to the info, I have twice run into this:

atkbd.c: Spurious ACK on isa0060/serio0

What is this and is this why I can't install?

Thanxs.

---

