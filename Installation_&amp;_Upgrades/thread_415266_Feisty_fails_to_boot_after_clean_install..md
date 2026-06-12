---
title: "Feisty fails to boot after clean install."
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by MCGrunge on 2007-04-20
I've been dual booting Vista and Edgy on and Optiplex 745, here's my specs:

Intel Core Duo E600
2GB ram
ATI x1300 256MB video card
Dual 19" Ultrasharps, connected via DVI

Yesterday I burned a Feisty final alternate cd, and proceeded to do a clean install.  The install completed without a hitch, however when I attempt to boot the machine into Feisty, I run into a strange problem:

- The splash screen comes up and the progress bar fills as normal.
- When the progress bar fills completely, both monitors enter low power state, and the machine will sit idle.
- Pressing the power button on the machine will cause the monitors to power back up, the splash screen is now gone, and the machine begins shutdown.

Before the machine shuts down completely I'm able to see a string of similar errors messages:

KDSETKEYCODE:  No such device:  failed to set scancode 90 to keycode 166.

This will followed by several more errors with different "keycode" numbers.

So far I've been unable to get past this point.  Any help would be much appreciated, thank you in advance.

---

### Post by MCGrunge on 2007-04-20
Sorry for the bump, has anyone seen this before?

---

### Post by ph0neman on 2007-05-02
I had a similair problem.. 

I installed the FF 7.04 Final.  When the progress bar completes... I can hear the startup music, and see the initial screens but Nautilus and the rest do not load it just sits at the startup screen.  I reboot and it does the same thing.  Something wrong with the xorg.conf is my guess but I dont know what. 

I tried to load the ATI drivers with ENVY and that didnt seem to phase it but when I removed those same drivers with ENVY i started to get another error message saying **[COLOR="Red"]no screens found[/COLOR]**.

---

