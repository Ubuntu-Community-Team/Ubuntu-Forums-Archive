---
title: "[SOLVED] Fesity to Gutsy upgrade will upgrade &amp;quot;built-in&amp;quot; wireless"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2007-07-19
I have a desktop Dell Dimension 4100. It runs Fesity well, if slowly (733Mhz CPU and 256Meg RAM).  I can't get a D-Link card to be recognized on the pci bus. 

lspci shows not such card.

fshw -C network shows no such card

I have installed, uninstalled and re-installed via synaptic pkg mgr. every package connected with madwifi. e.g., restricted 2.6.20-16-386 with and without low-latency, etc.

The card is brand new. When installed the green power led blinks every few seconds, so I guess the card could be good.

If I upgrade to alpha tribe 2 Gutsy, will it have the madwifi and ancillary 'drivers' built in?

---

### Post by Mark_in_Hollywood on 2007-07-20
The hardware was bad. installed another. lspci shows it is there as does lshw -C network

thanks

---

