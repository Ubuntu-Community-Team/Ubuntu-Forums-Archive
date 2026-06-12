---
title: "Trouble installing upgrades"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by d25436 on 2008-10-11
I frequently get this message while trying to install anything(even a simple adobe plug-in):(


[FONT="System"][COLOR="Navy"]A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Unable to parse package file /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_universe_binary-i386_Packages (1), E:The package lists or status file could not be parsed or opened.'[/COLOR][/FONT]

---

### Post by Partyboi2 on 2008-10-11
remove the file in question
```
sudo rm /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_hardy-updates_universe_binary-i386_Packages
```
Then re down the list by 
```
sudo apt-get update
``` this will regenerate the list.

---

### Post by weird_c00kie on 2008-11-26
Thank you so much for that. I had that problem for a VERY long time but I never had the time to look into it. I'm really glad the solution was so easy to find and even easier to implement. Thanks a bunch partyboi dude!

---

