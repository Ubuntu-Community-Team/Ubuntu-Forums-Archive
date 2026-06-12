---
title: "ubuntu 9.04 patches upgraded now unable to boot"
date: 2008-12-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lalitgaur on 2008-12-16
Hi 
I had upgraded successfully to 9.04 alpha 1 from 8.10 under wubi and it was running fine for a month or so.
Suddenly after a bunch of package upgrades and there were a lot of package removals day before yesterday I am unable to boot into Ubuntu at all
All it gives me a string of messages upto Checking battery OK and 
then an error comes
b44: eth0: Bug timeout waiting for bit 00000002 of register 42
quite similar to this bug below

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/112290](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/112290)


Is there any way I can boot Ubuntu maybe by disabling b44 etc while booting.
If so can the steps be detailed

---

### Post by jfernyhough on 2008-12-16
Welcome to the wonderful world of alpha-alpha testing. :D

Sounds like the easiest way out is a reinstall, and next time just do a safe-upgrade or pick the updates manually via synaptic.

---

### Post by Triggerhapp on 2008-12-16
Edit : Disregard- my brain didnt register :0

---

