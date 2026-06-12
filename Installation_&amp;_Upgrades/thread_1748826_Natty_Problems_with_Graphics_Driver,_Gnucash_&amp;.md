---
title: "Natty Problems with Graphics Driver, Gnucash &amp; Shutdown"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by rozen on 2011-05-04
Hi,

I just did an install of Natty into a separate partition and incurred several problems.  I have a Dell-DXP061 with 4 GB of memory and an Nvidia GForce 7300LE and a Dell 27in. monitor at a resolution of 1920x1200. 

Initially it booted in to Ubuntu Classic as expected due to needing a proprietary video driver. So the first thing I did was to install the recommended Nvidia  driver and attempted to reboot. It would not start either Unity or Classic.  So I did a re-installation and then selected the experimental open 3D driver and was then able to bring up the system in both Unity and Ubuntu Classic. I installed a number of programs including cairo-dock, which I really like, emacs23, and gnucash.  I have used gnucash for years and consider it a necessity.  However, the Natty version will not display correctly the "gnucash-data" file I created with version 2.2.9 that I have been running on 10.10. This is almost a show stopper for me.

When I try to do a restart, the screen goes black, "Ubuntu" appears with the little dots, three of the dots change color and the system hangs.  The system only stops when I hold the power button to effect a complete power outage.  Interestingly the LiveCD did not seem to have a problem with restart.

I can see how a causal user might like the Unity interface, but I don't think that I am interested. I guess I will stick to gnome for a while, at least until Gnome3 and then I am not sure where I will go.

I am writing this on 10.10 using a proprietary video driver with my Dell 27 inch monitor and am not sure that Natty is a keeper.  I would have to find my way around the problems noted above. I can find a gnucash forum, I will post a question there.

I would certainly appreciate any suggestions about solving these problems.

Thanks in Advance,
Don

---

### Post by dino99 on 2011-05-04
some users have found that "black" screen is related to "splash" not used on boot line.

if you dont like unity: remove/purge ubuntu-desktop & unity

often xorg.conf give errors, so remove it

and check driver activation first

---

### Post by dusie on 2011-05-08
The gnucash problem seem to have been solved:
[https://bugs.launchpad.net/ubuntu/+source/overlay-scrollbar/+bug/770304](https://bugs.launchpad.net/ubuntu/+source/overlay-scrollbar/+bug/770304)

The updated overlay file solved the problem for me. :)

---

