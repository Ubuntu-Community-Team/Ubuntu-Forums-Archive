---
title: "The Subiquity installer for Ubuntu 20.04 server edition keeps crashing"
date: 2021-07-23
forum: Installation &amp; Upgrades
---

### Post by patrickgoetz on 2021-07-23
I've attempted to install Ubuntu 20.04 server edition on 3 machines and the installer crashes more often than not. On two previous server installations I suffered through 6-8 installer crashes before some magical combination of configuration elements resulted in an fully installed system, although the installer never seems to terminate cleanly; there's always an endlessly running curtin process.

 On the server I'm trying to install now (rackmount, SuperMicro, SATA SSD drives) I am simply unable to get through an install. I've tried around a dozen times already, using various configuration selections. I can install Arch Linux on this system in a matter of minutes, so I don't think it's the hardware.  I thought the crashes might be associated with pre-defining disk partitions or setting up a software raid for the / partition, but in my last attempt I tried to do a UEFI install on a single SSD disk (select boot device, allocate all remaining space to / -- literally the simplest thing you can do) and the installer still crashed. I went through the install log and found the python error log (see attached image), but the reason for the crash is opaque.  In previous installs I assigned a static IP address to the active network interface, and on this server the networking people want me to configure it with DHCP and then have them reserve the assigned IP address; maybe that's the problem. But that shouldn't be a problem, of course.

Can we go back to the old, reliable Alternative installer that was available for 18.04?  It's insane that I can install a roll-your-own distro like Arch on a server from scratch in 1/10 of the time it takes to use the subiquity installer.  That's a total and complete fail.

---

### Post by MAFoElffen on 2021-07-23
I'm on a SuperMicro Server Board with SSD's right now...And I can verify that I have no problems with... There's nothing special about the hardware that relates to the installer. I probably make at least  2-5 installs a day to VM's in both BIOS and UEFI and have no problems, with differing LVM and mdadm configurations to test and verify... And I didn't have a problem when I installed to this host clean and migrated to. I feel your pain...

Looking at your "Error 9" pointing to "a bad file descriptor"... (hint) Did you check the SHA of your installation media? It is saying that you have a problem with that. Looks like specifically when it is trying to unpack packages in the image'es on-disk repo... I am guessing that you are using the 20.04 Server LiveCD image right?

I see that you tried different things... except that you didn't say that you tried a different copy or form of installation media... I would suspect that you have a corrupted / bad image.

---

