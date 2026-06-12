---
title: "Recovering from a interrupted upgrade"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by Lord Erik on 2006-08-02
I need to find out if there is any way to recover from an upgrade that was interrupted.  The story:

Asus L3000H laptop
Upgrading from badger to drake.

I shut down all applications and then ran the update manager, dowloading from a 1.5Mbit internet connection (the laptop is using a wireless nic).

Came back several hours later to find it stuck on "Configuring tetex-base".

The mouse still moved (very sluggishly) but nothing else would respone.  Ended up rebooting and it brings up the gnome login screen, when I log in all I get is a blank brown screen.

From recovery mode I tried apt-get install -f (someone suggested that) and it gives an error and suggests running dpkg --configure -a.  Tried that at it seems to loop on a particular error, the text scrolls to fast to read but it seems to be the same message over and over again (pause key doesnt stop it).  If I try ctrl c it seg faults.

Is there any way to resume the upgrade or will I have to reformat and start from scratch?

Thanks,

Erik

---

