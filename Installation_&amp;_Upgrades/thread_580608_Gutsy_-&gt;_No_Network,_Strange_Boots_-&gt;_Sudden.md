---
title: "Gutsy -&gt; No Network, Strange Boots -&gt; Suddenly OK"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by bmartin on 2007-10-18
I don't know why this happened; it suddenly went away. I've been using Linux for years and I'm at a loss to explain this.

I upgraded to Gutsy using the Update Manager and restarted my computer. After boot, Network Manager wouldn't allow me to connect to my wireless network (or any network). I proceeded to install WICD, which led to the same results. I didn't have a wired connection available, so there wasn't much I could do.

Upon successive rebooting, my keyboard sometimes didn't work at all (I could select my kernel in GRUB, but after that, all keystrokes were futile). The wireless kept failing. When I ran WICD from the command line, it spat out a message about DBUS not responding (or something like that). I tried restarting DBUS and HAL, but nothing worked... until I booted an older kernel in recovery mode, then loaded up DBUS and GDM manually. I tried doing the same steps again, but it didn't work. Different versions of the kernel didn't work.

After about ten reboots, everything went back to normal. I couldn't have installed anything, as I had no internet connection the whole time. My wireless network connection, which had been detecting networks all along but wouldn't retrieve an IP address, started working, and my keyboard behaved as normal.

I've heard that sometimes computers can overheat, but mine has never displayed the symptoms before and I have no reason to believe it was overheating at the time. In between boots, I loaded up Windows and the networking worked fine. That was about halfway through my rebooting spree.

Do you have any idea why this might occur? I can't imagine it having nothing to do with the upgrade, as nothing like this has ever happened before.

---

### Post by MatthewPlanchard on 2007-10-18
The Potrieck Computer Gnomes

---

### Post by bmartin on 2007-10-19
> **MatthewPlanchard said:**
> The Potrieck Computer Gnomes
Google amazes me... so I search Google for "Potrieck", and this page came up (it's the only hit). It's indexed already... because of you. You broke the Internets.

But seriously, that's the weirdest problem I ever had with Linux. It's very weird to have many outcomes during boot... I thought computers were deterministic.

---

### Post by hoodlum on 2007-10-19
i have that problem to, i click on the Network Manager icon and it doesn't show me any wifi networks.I had to manually  type in the SSID of my network.

---

### Post by bmartin on 2007-10-19
> **hoodlum said:**
> i have that problem to, i click on the Network Manager icon and it doesn't show me any wifi networks.I had to manually  type in the SSID of my network.
I know what you're talking about, but that's not the problem I had. I could see the networks; I simply couldn't get an IP address right after the upgrade, but the effect seemed to wear off. I just restarted and it worked fine.

---

### Post by shouravv on 2007-10-20
I had the same problem at first, but then once I activated my network connection from System > Administration > Network , it started working just fine.

The weird thing is after installation Gutsy would not automatically enable the network connection available. I drove me nuts.

---

### Post by MatthewPlanchard on 2007-10-21
> **bmartin said:**
> Google amazes me... so I search Google for "Potrieck", and this page came up (it's the only hit). It's indexed already... because of you. You broke the Internets.

But seriously, that's the weirdest problem I ever had with Linux. It's very weird to have many outcomes during boot... I thought computers were deterministic.

wow...just.//wow

---

