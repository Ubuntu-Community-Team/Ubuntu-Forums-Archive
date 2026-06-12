---
title: "Successful fresh install of Hardy Heron with ATi Radeon X1600, Big Desktop and Compiz"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by svenni on 2008-05-23
I thought it would be worth announcing that I made it on the first try this time, without having to mess around with the xorg.conf. I now have two screens with different resolutions running with "Extra" desktop effects. This is on a ATI Radeon X1600 card running on Ubuntu Hardy with EnvyNG installed.

The resolution is 1600x1200 on the right monitor and 1280x1024 on the left one. Big Desktop is setup with 3200x1200, but it works like a dream anyways, and nothing ends up "outside" of the screens

This is what I did to make it work:
[LIST=1]
[*]Fresh install of Ubuntu Hardy Heron
[*]Once installed, accepted notice of installation of properietary drivers
[*]Installed EnvyNG with the command: apt-get envyng-gtk
[*]Started EnvyNG by choosing Programs > System tools > EnvyNG
[*]Installed with automatic detection
[*]Rebooted when prompted to do so
[*]Started the ATI Catalyst Control Center by choosing Programs > Other > ATI Catalyst Control Center
[*]Chose Display Manager
[*]Under Display Modes, selected Big Desktop
[*]Adjusted the screens properly (left / right orientation)
[*]Reeboted
[/LIST]

Everything is now up and running :D 

The last time I tried this was when I was using Gutsty Gibbon, but I was unable to make it, even after two weeks of messing around. I'm really glad to see that it was a lot easier this time, almost without using any terminal commands, and at least without having to edit configuration files.

A great thank you to Alberto Milone (who made EnvyNG), the Ubuntu contributors and the ATI driver developers!

Btw: I'm not sure if EnvyNG needs to be installed, but I could not find the ATI Catalyst Control Panel otherwise...

---

