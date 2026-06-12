---
title: "Can't get network manager to update. Any ideas?"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by purplefiona on 2008-10-06
Hi-
I'm trying to update my network manager in order to get my 3 dongle to work with my ubuntu-running eee, as recommended by a friend, here is what he said:


Try this...
 click on 'system'> administration> software sources
click third party software
Add (click the add button and then copy these lines in and click enter)
deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main

Restart your PC. Make sure you plugin your E160 before Ubuntu boots, otherwise the kernel will not fully detect the modem hardware.

open synaptic package manager and search for network manager, you have verion 0.6 you need version 0.7
at the top click mark all upgrades. then apply to install new software.
I'd restart again here but thats just me. always worth a go to clear memory.


Right click the network-manager applet and "Edit Connections". Click "Mobile Broadband". Click "Add". Ubuntu will prompt you to "Choos a Mobile Broadband Connection". Your E160 should be automatically detected (mine came up as an E620). Click "OK". Set the Connection name to "3netaccess". Set the APN to "3netaccess". Click "OK".

Now left click the network-manager applet and select the 3netaccess entry. Network Manager will now connect you to 3.

Right so I've done that, found synaptic and found network-manager but it doesn't want to update it, only either uninstall, completely remove, or re-install it. So I tried re-installing it but it doesn't do anything- and yes I did reboot the machine.

What is the big obvious thing I'm missing here?
I have to get the damn dongley thing working today as my time is up to return it if I can't!

aargh!
Yours, in increasing frustration
Purplefiona.

---

### Post by purplefiona on 2008-10-06
Right ok so I got the network manager updated after extended faffing but now the 3 dongle doesn't work.
It recognises it but won't connect to it-
I have tried everything (feels like) and even gave it to a proper Linux person for an hour. Even he gave up.

Any ideas?
Please help- I am about to be stuck paying £7.50 per month for a net connection that doesn't function.

---

