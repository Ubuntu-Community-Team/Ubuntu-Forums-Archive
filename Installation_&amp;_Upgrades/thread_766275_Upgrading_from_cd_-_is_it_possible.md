---
title: "Upgrading from cd - is it possible?"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Sepp1 on 2008-04-25
I put my trusty Acer laptop to upgrade to Hardy last night (Europe time), and went to bed, hoping for at new and better world in the morning.
The computer however had crashed sometime during the upgrade process, so the system was pretty much toast.
Several times during startup it said "fail" instead of "OK" in the boxes on the right. I can´t remember witch.
Several setting are gone (no wallpaper, wrong theme, missing icons on desktop.
I can log on.
After i log on it says "Failed to initialize HAL!"
I can browse the disks
I can´t run a browser
I can´t run the upgrading tool

I have downloaded the Hardy iso-image on another computer, so i have an installdisk at hand.
Can I run the install from that CD and fix the system that way?

Thx in advance

---

### Post by ptcbus on 2008-04-25
Do you have the alternate install CD? See [http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")

---

### Post by tormod on 2008-04-25
> **Sepp1 said:**
> Can I run the install from that CD and fix the system that way?

The Desktop CD is only for installation, not upgrading.

Try fixing the upgrade using the command tools: ```
sudo apt-get upgrade
``` and then ```
sudo apt-get dist-upgrade
```

---

