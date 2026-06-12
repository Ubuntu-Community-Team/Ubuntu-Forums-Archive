---
title: "Linux-Headers not updating"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by SailingCyclops on 2010-11-24
Hi:

I am running 32 bit 2.6.32-26-generic-pae #47-Ubuntu SMP Wed Nov 17 16:14:46 UTC 2010 i686 GNU/Linux

Every time Update Manager updates the Kernel, the kernel and it's associated source code is upgraded, but the LINUX-HEADERS for the associated kernel are not updated. 

This is a problem because without the updated linux-headers, my Nvidia drivers fail to recompile and load. A PIA. I then have to go to Synaptic Package Manager, find the appropriate linux-headers for the new kernel version, install it, reboot, and then Nvidia drivers load and function again. 

Something is obviously messed up here. I likely caused the problem thus:

On first install of Ubuntu 10.04 LTS on this machine, it installed with the generic kernel. It saw/found the Nvidia drivers and loaded them OK (I may have had to do some Nvidia installs via Synaptic; I don't recall). My machine has more than 4GB ram, and I noticed it was not using nearly all of it. I researched and found the solution was to switch to the PAE kernel, which I did. Ever since then at every kernel upgrade, the Linux-headers fail to update, and have to be updated manually for Nvidia to function.

Now that I know what the issue is, it's not a big deal. However, Update Manager should know I need the Linux-Headers and upgrade them at every kernel update. How can I insure this happens auto-magically like the rest of this fine and beautiful KickAss OS?

---

### Post by carl4926 on 2010-11-24
Did you leave the generic kernel in place.
ie; do you have them both?

---

### Post by SailingCyclops on 2010-11-24
> **carl4926 said:**
> Did you leave the generic kernel in place.
ie; do you have them both?

Well, yes and no. At first, when Nvidia didn't work, I deleted the non-pae kernel, then re-installed it when deleting it made no difference. Now, after a few updates, I have not messed with the older kernels nor with the older non-pae kernel. 

What is consistently happening is the new pae kernel and the new kernel are being updated along with their associated source files, but the Linux-Headers are not. I am fairly certain I messed this up a while ago (I have been using Linux since 0.097 kernel, when lots of hacking/fudging/altering was required to get things right; so I poke and screw around a lot). How can I insure all remains in sync in this totally new GUI environment? I love it and I hate it at the same time. Weird huh? Like where is the text file? What are the appropriate parameters? 

I am sure the auto-magic GUI did not account for old-time blokes like me.

---

### Post by carl4926 on 2010-11-24
I'm more or less a part time Ubuntu user, and I can't say I have experienced this. It really should be the case that they should all upgrade.
You probably need someone more experience in apt than me.

Thought I have a work project this month which will mean I need to use it most of the time.

---

### Post by wojox on 2010-11-24
Try

```
sudo apt-get update; sudo apt-get upgrade; sudo apt-get dist-upgrade
```

---

### Post by SailingCyclops on 2010-11-29
> **carl4926 said:**
>  It really should be the case that they should all upgrade.

Do you use Nvidia Drivers?

---

