---
title: "Video Card question"
date: 2005-04-21
forum: Installation &amp; Upgrades
---

### Post by dcahrakos on 2005-04-21
I have an ATI Radeon 9250, and I can get ubuntu to install, and run, but it gets stuck at "Starting Hotplug Subsystem" and I bypassed it with ctrl+C and the sound and stuff didnt work, and at first my onboard video didnt work, so I just configured Xserver to use my onboard, but it still conflicts with my Radeon and hangs the hotplug still, someone else had the same problem, just took out his nvidia(different video card, but same concept) and it worked fine...so im wondering, since the internet and sound dont work on it, is it possible to download the ATI drivers on my windows XP, burn it, and install it on ubuntu? will it possibly work that way?

---

### Post by diebels on 2005-04-21
So you're sure the ati card is causing hotplug to hang? Try recovery mode to see more messages. There's many possible methods to get the drivers installed, apt-get install, dpkg -i. You don't have network running on the ubuntu machine, and you think it is caused by the ati card? Have you tried physically taking out your card?

---

