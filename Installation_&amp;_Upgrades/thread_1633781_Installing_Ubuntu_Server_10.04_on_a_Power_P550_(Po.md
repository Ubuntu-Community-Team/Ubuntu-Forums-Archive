---
title: "Installing Ubuntu Server 10.04 on a Power P550 (Power5 based)"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by metelo on 2010-11-29
Hi there.

I've been using Ubuntu for a while (since v 7.04) in x86 environments.

Recently got my hands on a Power550 server from IBM, and I've been trying to install the server version (10.04).

All documentation seems to indicate that I should have in the CD iso a module called ide-scsi that should solve the problem of not finding the CD-Rom during the install (if fails both in virtual optical mode and with the physical DVD driver dedicated to the lpar).

It seems to be a common issue on the Mac installs, but the module is not listed when doing a modprobe -l

Anybody has experience with the setup on this machine?

Thanks in advance, and sorry if duplicated (I really couldn't find any other threads covering this issue - it seems that on the mac the modprobe ide-scsi solves the crdom not found).
Andre

---

