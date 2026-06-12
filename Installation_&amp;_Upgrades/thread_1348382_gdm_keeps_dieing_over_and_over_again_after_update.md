---
title: "gdm keeps dieing over and over again after update"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by anontrol on 2009-12-07
I performed the requested synamptic update a few days ago and gdm keeps starting, dieing and then restarting over and over again.

My desktop in unusable.

Platform is an Atom Ion based box with the Nvidia kernel mods.

I've tried recompiling the Nvidia kernel mods (as I've done on several update prior to this one) and have disabled compvis, but still no luck).

Any ideas on how to fix this problem?

---

### Post by squaregoldfish on 2009-12-07
I believe the problem is that the nVidia drivers have got themselves out of sync with the kernel version.

I can't remember exactly what I did to fix this, but it went something along these lines:


[LIST=1]
[*]Remove all trace of any nVidia drivers from your system (i.e. purge all nVidia packages), and temporarily move your xorg.conf file somewhere safe.
[*]Perform a complete system update to ensure you have the latest kernel, and remove any old kernel versions that are left lying around.
[*]Install the approriate nVidia drivers package for your card. This should now pick up the correct kernel and recompile the drivers correctly.
[/LIST]

Of course, if you can't use the desktop at all, you may well have to use a LiveCD to get into your machine's hard drive and disable GDM - there's advice on how to do this elsewhere (I forget how it's done for the moment). (If you happen to have installed an ssh server, this will still be working, so you could log in remotely instead of using the LiveCD.)

Hope this helps,
Steve.

---

