---
title: "Error after 10.04 upgrade"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Bearna on 2010-05-02
Hi
I am not a technical linux user and have benn using ubuntu in a home environment.
I have an isseu that I dont seem to be able to resolve

I have upgraded to 10.04 in the last few days. After completing the upgrade I got a message to say that rhythmbox was not installed. If I go into the update manager now it lists rhythmbox-plugins (new install) and rss-glx as outstanding. However when I go in install it says. "You have 1 broken package on your system! Use the "broken" filter to locate it". 

After attempting the install the following error message appears:

E: /var/cache/apt/archives/rhythmbox-plugins_0.12.8-0ubuntu3_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/rhythmbox/plugins/generic-player/libgeneric-player.so')
E: /var/cache/apt/archives/rss-glx_0.9.0-2ubuntu4_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/xscreensaver/colorfire')

The red warning icon appears for synaptic manager and when you open that it says "You have 1 broken package on your system! Use the "broken" filter to locate it". If I search for broken packages one comes up as broken rhythmbox-ubuntuone-music-store.If i selct that and go edit / fix broken packages - i get a message that says successfully fixed dependency problems. But if I try to exit synaptic I am told there are still amrked changes that have not been applied. They will get lost if you choose to quit Synaptic.

Can anyone suggest a fix here to complete the installation

Thanks

---

