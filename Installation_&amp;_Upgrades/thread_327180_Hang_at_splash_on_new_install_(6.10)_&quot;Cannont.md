---
title: "Hang at splash on new install (6.10) &quot;Cannont access tty&quot;"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by phatlip on 2006-12-28
Scenario:

- Used alternate install i386 CD and ran through installer with no problems.
- Restarted machine and waited for boot.
- Reached Ubuntu splash screen, loading bar went about 1mm in - then hangs.
- Screen changes to flashing underscore in the top left hand corner.
- About 2 minutes later i am given the error message: error: "Cannont access tty; stopping job control"
- I'm then presented with a console where i can basically do nothing.
- alt+ctrl+f1 returns the error: /dev/hda1 does not exists! (however, ubuntu should know perfectly well that its installed onto /dev/sda1)

System:

- AMD64 939 3000+
- 2GB of DDR (OCZ) Ram
- Gigabyte K8NS-pro nForce4 chipset.
- PCI-X nvidia 7600GT gfx card.
- 80GB SATA HDD
- Phillips 190S 19" LCD
- Antec 550W PSU


This is my first try at using ubuntu, before this i have been using openSUSE, so i'm probably doing something wrong. The hard-drive is good because i had an OS running fine that i formatted to install ubuntu.

Any help is appreciated - i have a handle on the cli and editing various config files. i can get into the recovery console too, just have no idea what to do to fix it.

---

### Post by phatlip on 2006-12-28
perhaps someone could just tell me what boot options i could use to get to a CLI?

---

### Post by phatlip on 2006-12-29
Well, after much googling and post and asking and waiting - i realised there are so many people with this or similar problems with bugs being reported all over, so as much as i'd like to run the latest Ubuntu - it simply doesn't work for me, with my semi-limited amount of knowledge.

Fixed by installing dapper, not a problem to be had.

---

