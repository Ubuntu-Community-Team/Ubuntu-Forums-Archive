---
title: "Ubuntu amd64 install problem"
date: 2005-06-13
forum: Installation &amp; Upgrades
---

### Post by Sureshot324 on 2005-06-13
I booted from the cd, went through the partitioning and setup, got to the point where it ejected my cd and asked me to restart, choses amd64 default from the grub boot loader, it went through installing a bunch of packages, and then it just started scrolling a lot of text extremely fast (seemed like mostly gibberish but i couldn't really read it).  I left it like this for about 15 minutes but it was still doing it.

Is this a normal part of the installation?  If not, any ideas on how to fix it?

---

### Post by flower.Hercules on 2005-06-26
Exact same problem, am trying a reinstall now ](*,) 

AMD 64 3200+, by any chance?

---

### Post by flower.Hercules on 2005-06-26
I think it all went downhill right around the time it reads the dependency tree, after which - it installs new packages and such that were held back during install.

If you used the generic DEFAULT kernel, try reinstalling and selecting just the generic kernel for your first boot after stage 1 install. That worked for me. I also must note, I changed a hotplugged device between stage 1 and stage 2 of the install process.

HTH :)

---

### Post by superchode on 2006-11-28
just had the exact same problem while trying to install on my 4400+ system.

flower, could you re-phrase your fix? i'm not really understanding what exactly you did to allow it to install properly.

after the install stalls, i am actually able to get into the OS... and patch a few things to get the system working... but updating to 6.06 or 6.10 fails completely and X is unusable after that. i don't have the skills to fix the system so i'm looking for a way to get it to install properly in the first place.

---

