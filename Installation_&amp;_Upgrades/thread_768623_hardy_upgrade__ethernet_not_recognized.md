---
title: "hardy upgrade : ethernet not recognized"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by piusvelte on 2008-04-26
**RESOLVED**
Not sure which did it, but I renamed /etc/network/interfaces so that a new a new one would be created, also I removed a custom file, /etc/modprobe.d/network. The custom file contained 'option 3c59x global_wol_enable=1', or something like that in an attempt to get wake on lan working.
***

I just upgraded my box to hardy and the nic isn't recognized by the network manager. This box was fully functional when it started on feisty, and after the internet upgrade to gutsy. The hardy upgrade was also via internet. When I run lshw or lspci, I can see the card , 3com 3c905c, but the network manager only shows the 56k modem as an option. I noticed that after the initial restart, the nic lights were out. These normally remain regardless of the machine state, as long as the machine has power. I tried moving the card to a different slot, adding power, and the lights were back on! I tried booting up and the lights went out and the card was still unrecognized. That almost seems like a bios issue, but the card worked perfectly before the hardy upgrade.

What are the chances that I can fix this without an internet connection? Is anyone else having problems with this card? Any help would be appreciated, thank you!

Note: This is a different machine from the one that I'm posting about with boot problems after the hardy upgrade.

---

