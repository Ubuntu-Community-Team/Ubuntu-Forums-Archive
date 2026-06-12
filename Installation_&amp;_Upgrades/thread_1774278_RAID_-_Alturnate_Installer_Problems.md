---
title: "RAID - Alturnate Installer Problems"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by ryannathans on 2011-06-03
Hey guys, I have been getting into a bit of Android development recently and needed a linux desktop.

Been using Windows 7 Professional 64bit until now, only reason I have not been using linux all this time is because no one seems to like making linux games.

I have tried Ubuntu (alternate installer of course), Debian, Fedora 15 and a few other distros.

The problem is simple. RAID.

I have a RAID0, three 1TB HDDs, with two RAID0 Drives made from them. A bootable 250GB For Windows' C: and / for Linux and a 2500GB 'Drive' for everything else D: (all my data) and /home (well, when I get Linux to install....)

- 2 Virtual Drives RAID0 over 3 HDDs

GA-P55a-UD5 Motherboard using onboard INTEL RAID. FAKERAID AFAIK.

On install there is an error when partitioning hard drives and after hiting back and next it partitions and seems to partition correctly, however install only gets as far as 'installing packages' and dies, with the big red screen and all. I can never retry installing packages, after the initial error 75% through on every retry it fails at the very start.

On another note Fedora 15 doesn't recognize the first 'drive' and always wipes it.

All other distros don't even recognise any HDDs.

This is amd64 11.04

I want to install ubuntu and dualboot with Windoze.

any suggestions?

EDIT: Currently using Fedora 15 after Ubuntu would not install after multiple tries, second time around Fedora worked, turns out it is detecting my drive after all but I installed the bootloader to the wrong partition, 15 minutes later here I am posting from Fedora, it warns that one of my hard drives is going to die soon, I will believe it when it happens :P I will head back to Windows and do some tests, hopefully I can get all the work I need to do done on Fedora instead. You guys needs to fix this! :P

---

