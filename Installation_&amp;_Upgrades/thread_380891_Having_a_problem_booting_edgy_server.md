---
title: "Having a problem booting edgy server"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by ScalarScience on 2007-03-10
A bit of help.  My *nix knowledge is limited to simple shell management of some of the various domains I interact with, and IRIX, HP/UX & OSF1 (VAX etc) from years & years ago (3d stuff).

So I'm trying to get 6.10 server to install off of cd (burned from iso) as a LAMP install.  The cd I burned verifies fine. The box is a really old AMD k6-2 (500 mhz) with 256Mb ram, and 2 IDE HDs (13Gb & 10Gb).  Basically built of spare parts.  The installation is successful (more than one time) and everything appears go.  But it will not boot.  After grub, it says 'starting up...' and then immediately reboots.

Ubuntu desktop (gnome) installed fine and booted, I was able to configure all hardware.  But I do not need all of the overhead of that release, I just want a box in the closet I can ssh into and use for web dev abuse. The hardware is fine, for what it is.

I have tried adding various noacpi parameters within grub (pci=noacpi noapic nolapic acpi=off) to no avail.  Any ideas?  I don't know how to troubleshoot a crash like that.  LiveCD then look for logs?

---

### Post by ScalarScience on 2007-03-10
Anyone?  I tried in IRC for a few hours with noone having any ideas beyond the noacpi stuff (which I googled for full syntax)...

---

