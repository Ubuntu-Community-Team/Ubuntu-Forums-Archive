---
title: "x64 major install problems"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by madcap66 on 2007-10-16
Hi there

I built a new workstation with the following spec:

Tyan S2985 Thunder K8WE
2 x Opteron 275's
4Gb ECC Reg Ram
XFX Nvidia 8800GTS
3 x Hitachi 300Gb SATA HDD's
1 x Lite-On SATA DVD/CD Drive

I've installed XP pro 64 bit on the first hdd. Everything aok with that. I downloaded and verified the Ubuntu Feisty 64bit AND the Gutsy 64 bit cd. Popped the cd in and rebooted. I get the loader screen and then hit start install and then monitor goes blank. The CD drive is still working but nothing on the screen. If I leave it long enough sometimes I get the 'Busybox' prompt. Other times not and have to reboot the pc to get out of the blank screen.

I've read the forum for the past few days and tried adding the following:

break=top (to the options)
enter (and then at command prompt)
modprobe piix
exit

Still nothing.

Also tried adding 'all_generic_ide=1 (again to no avail).
Also tried adding 'acpi=off noapic (nothing again).

Finally tried alternative cd's and still the issue persists. Just as a test I downloaded the OpenSuse 10.3 64bit dvd and I got 'no repository found' issue.

Weird thing is that the 32bit Feisty Ubuntu runs fine and boots to the Live CD Desktop. I really want to use Ubuntu 64bit so I would really like some help in installing Ubuntu 64bit to the second hdd. Please can some 'expert' throw some of his/her expertise this way? 

Many thanks in advance.

UPDATE: Is anyone able to help???

---

### Post by madcap66 on 2007-10-18
Just to let you know that after being inundated with replies to the post - I managed to resolve the issue.

For what it's worth the resolution was to remove the floppy drive completely and install an IDE CD/DVD drive. Then ran Gutsy 64bit Live CD and a bit of patience to let the install do its job. Result = working and seems to be stable Ubuntu Gutsy with the Nvidia drivers installed via Envy.

---

