---
title: "Trio64V+ Video Driver Install"
date: 2019-04-25
forum: Installation &amp; Upgrades
---

### Post by electrosteam on 2019-04-25
18.04.2 LTS

I have installed a new (to me) PCI video card with a Trio64V+ chip on an old HP ML110 server tower
This is a test to see if I can improve video performance compared to the current ATI Rage 3 (XL) chip on the mainboard.

Searched and found launchpad.net listed  'xserver-xorg-video-s3_0.6.5-0ubuntu4_i386' as the likely driver.
This package is listed against Trusty (14.04), so it is a few years old.

Tried to install with GDebi: 'Error: Dependency is not satisfiable: xorg-video-abi-15'.

Back on Launchpad, it shows 3 dependencies, 2 are downloadable, but the offender is shown in black font and is not downloadable.

Searched for  'xorg-video-abi-15' and found a  'xserver-xorg-core_1.15.1-0ubuntu2_i386.deb' on 'pkgs.org' that appears to contain it.
But the package is also listed as 'Xorg X server - core server', within a table titled 'Ubuntu 14.04 LTS (Trusty Tahr).

I am reluctant to proceed along this line because of risk of breaking my system.
All my package installs so far were with Synaptic, so this is new territory.

Advice and suggestions welcomed,
John

---

### Post by mörgæs on 2019-04-26
I also like recycling old hardware but to me the Trio64V is too old. I would look for something else.

Does the server have any connectors in addition to the PCI? AGP, PCI-express, ... ?

---

### Post by electrosteam on 2019-04-26
Morgaes,
Good advice, thanks for taking the interest.

The tower has standard PCI and longer higher speed PCI, no PCI Express.

The on-board ATI Rage chip works 'good enough' for all the work I do.

I will return this card (borrowed) and investigate the alternatives.

John

---

