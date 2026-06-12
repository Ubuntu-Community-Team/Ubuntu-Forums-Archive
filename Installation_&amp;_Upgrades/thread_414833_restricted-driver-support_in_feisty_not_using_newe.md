---
title: "restricted-driver-support in feisty not using newest version...what it leads to"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by siman on 2007-04-20
imho feisty could have handled already installed nvidia-prop-drivers more smoothly. for me the new restricted-driver feature is counter productive. it's like this:

I had the newest nvidia driver installed (with .sh script) in edgy and made a lot of changes to my x.org-conf due to a strange dual-desktop environment and special 3d accel i wanted to use for gaming + beryl.

after installing feisty x.org was broken - I actually expected that, because I knew that I'd get a new kernel and everytime that happens, I have to reinstall the nvidia drivers (again sh - script). no biggy.

So I do install the nvidia drivers, restart X and after logon I see this new restricted-drivers popup. I click on it and it complains about a package "kernel-restricted-xxx-modules--something" missing - I install those, finally the popup works and I see this list of propietary drivers with my nvdia driver in it. alright, that's it I thought.

No: after restarting this morning X.org new complains about a version mis-match between the nvidia kernel-modul and something else (will dig up that error message - but I think it's gone since I restarted X madly after that). probably because the restricted-driver thingy expectds a different version - not the newest - version then the one I installed via the nvidia sh-script

Hm... so now I have to figure out how to either disable restricted-drivers-support by feisty without changing something I actually need or force the restricted-drivers-thing to support the newest version.

ps.: I wan't the newest driver :-) No way I settle for something else. Doing the quick "sh nvidia-blalblbla.run" everytimte kernel changes is acceptable.

---

