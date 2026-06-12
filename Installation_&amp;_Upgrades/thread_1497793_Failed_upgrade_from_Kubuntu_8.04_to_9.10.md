---
title: "Failed upgrade from Kubuntu 8.04 to 9.10"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by johnzbesko on 2010-05-31
I have an Proliant DL380 that I use as a home server/router that I attempted to upgrade to Lucid. The gui upgrader first attempted to upgrade to 9.10 (as expected.)

I believe grub was incorrectly installed/updated. Not quite sure if grub2 was installed. The machine boots to a maintenance prompt. The partitions seem to be mounted read-only because of errors. The grub menu only shows an 8.04 kernel choice, even though all 9.10 packages were downloaded and, I believe, installed. The gui upgrader did fail with an error right before the "cleaning-up" stage. After "messing around" with it, the upgrader said I needed to reboot. So, I did and my problems started.

I tried booting the 9.10 Kubuntu cdrom and also a Knoppix 6 CD, but neither one would boot properly (gave me a BusyBox prompt.) So, I guess they don't like the Smart Array 6.

Any ideas about what I could try to fix and upgrade to 10.04? I really don't want to lose my configuration files (dhcp, firestarter rules, apache, squirrelmail, NFS, etc.)

Any help is greatly appreciated.

---

### Post by dino99 on 2010-05-31
dist-upgrades can be done from:

-previous to next
- LTS to LTS

uncheck non genuine repo before, and a clean system will help

---

### Post by johnzbesko on 2010-05-31
Apparently, Kubuntu 8.04 LTS does not upgrade to 10.04 LTS in one step. (Ubuntu does.) Hence the problem.

The fact that this DL380 G3 has a hardware RAID also seems to be giving me problems when booting, from CD, either 9.4 or Knoppix. That's why I'm stuck.

I don't know how to re-mount the partitions to be rw, now that they are first mounted as ro. I also do not know what options or drivers I need to boot a rescue disk.

Any help or links to similar posts is appreciated- my ability to search this forum or the internet is greatly diminished.

---

### Post by johnzbesko on 2010-05-31
Booting with Knoppix "failsafe" did the trick! I was able to see that grub's menu.lst had only two entries, even though the new 9.10 kernel had been installed. Once I manually added (edited) the 9.10 kernel option to menu.lst, the machine booted. 

My family is happy to get internet access back!

---

