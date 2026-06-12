---
title: "[ Nvidia riva/tnt geforce &amp; Nvidia current &amp; nouveau ]"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ethoxyethaan on 2010-03-13
On my install all of the following are installed:

Nvidia riva/tnt geforce (indicated by jockey)
Nvidia current (indicated by jockey)
Nvidia nouveau (indicated by synaptics)

when i check Nvidia current and nvidia riva/tnt in jockey it says the drivers are install but not currently in use...

well... i have 3D acceleration but the thing is Quake Runs extremely slow after 10 minutes of gameplay. 

how do i remove Nouveau, i want to use the Nvidia drivers. (free as in freedom of choice)

when i select nouveau for uninstallation it says "removing xserver-xorg-video-all

My Video card goes up to 74C and its not even overclocked so i hold my heart for the people who will install ubuntu in a few months with the new nouveau xorg module.

help appreciated

---

### Post by lidex on 2010-03-13
Go ahead and remove it. I did. Removing xserver-xorg-video-all doesn't take out the individual xorg packages as it's a metapackage.

---

### Post by CylnZ on 2010-03-14
Ok, so I removed it, and used the gui to activate the current driver.

restart

this driver is enabled but not currently in use.

so, that wasnt a worthwhile answer.

---

### Post by PARO on 2010-03-14
How did you get the nvidia tnt drivers to work? They're the only ones not included in the repos so I thought they must be currently incompatible or need a patch or something.

---

### Post by lidex on 2010-03-14
> **CylnZ said:**
> Ok, so I removed it, and used the gui to activate the current driver.

restart

this driver is enabled but not currently in use.

so, that wasnt a worthwhile answer.

I get the same thing in jockey, however graphics seem to work fine - including compiz. *[COLOR="RoyalBlue"]BTW, are you the OP?[/COLOR]*

---

### Post by FrancoNero on 2010-03-14
man I'm so looking forward to doing a fresh install of Lucid once we get close to RC :) mine's all funked

---

### Post by cariboo on 2010-03-15
> **PARO said:**
> How did you get the nvidia tnt drivers to work? They're the only ones not included in the repos so I thought they must be currently incompatible or need a patch or something.

The Nvidia TNT drivers in this case are the nouveau drivers, they have nothing to do with the closed source drivers.

---

