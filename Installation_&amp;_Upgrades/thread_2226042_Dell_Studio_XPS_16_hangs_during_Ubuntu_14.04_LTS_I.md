---
title: "Dell Studio XPS 16 hangs during Ubuntu 14.04 LTS Installation"
date: 2014-05-24
forum: Installation &amp; Upgrades
---

### Post by Manan_Gandhi on 2014-05-24
Hello everyone,

I am brand new to both Linux and Ubuntu, but have decided to dive in to learn something new for university. 

The system details are:

Dell Studio XPS 1640
Windows 7 Home Premium (came preinstalled with the computer)
Intel Core2 Duo T9600 @ 2.8 Ghz
6 GB RAM

System has just been restored to original settings, Windows 7 was fully updated, disk was completed wiped. (I do this on occasion just to keep my computer clean and running well)

Anyways, my issue is that I am trying to install Ubuntu  14.04 LTS onto my this Dell, but the installation hangs a black screen that shows

[ 0.708003] Call Trace:
[ 0.708003] [<ffffffff81715a64>] dump_stack+0x45/0x56
[ 0.708003] [<ffffffff8170ec65>] panic+0xc8/0x1d7

...a bunch more of this stuff, then finally ending with

[ 0.708003] [<ffffffff81703f40>] ? rest_init+0x80/0x80

A picture should be attached showing the full screen.

[ATTACH=CONFIG]253429[/ATTACH]

The steps I have taken so far are as follows

1) Disabled quickboot from the BIOS
2) Ensured that AHCI mode is enabled on the SATA mode selection in the BIOS
3) Shrunk my existing partition and have an unallocated sector available.

EDIT: I saw the Laptop Compatibility thread, and another user with my same hardware installing using Ubuntu 11.04 (Narwhal) which does not seem to be available anymore. Should I try an older version of Ubuntu?

At this point, as someone new to Ubuntu I am quite unsure of where to go next. The guides that I have located mention something about EFI and UEFI installations that I don't think apply to my configuration.

Any help is appreciated!

---

### Post by burstmode on 2014-06-28
I'm facing the same problem during the install & its blocking me from using 14.04

I've been running 12.04 LTS for years on this same laptop (Dell Precision M6600)... just burned a 14.04 Desktop 64-bit  DVD & went to boot from it.  

I get the same error listed above shortly after booting from the DVD. 

I thought perhaps I had an issue with the ISO, so I re-downloaded it, compared MD5's... same as before.

Burned a second DVD... same issue.

Update - also tried upgrading to latest bios (A15) to see if maybe there was an issue.  Same result.   Arrrgghhh!

---

