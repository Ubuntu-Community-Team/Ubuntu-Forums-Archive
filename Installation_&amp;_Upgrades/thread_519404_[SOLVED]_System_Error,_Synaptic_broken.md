---
title: "[SOLVED] System Error, Synaptic broken"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by WarholsGhost on 2007-08-07
Ubuntu Gave me this error, it occurs when i try to access the update manager and the synaptic package manager. 

"A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'"

I looked at another post that was very similar and i tried the following commands in the Terminal:

gregg@gregg-desktop:~$ dpkg -C
The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 virtualbox           

gregg@gregg-desktop:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

Help!

---

### Post by WarholsGhost on 2007-08-07
HA!

i fixed it by doing

gregg@gregg-desktop:~$ sudo dpkg --force-all -r virtualbox
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `virtualbox' missing, assuming package has no files currently installed.
140150 files and directories currently installed.)
Removing virtualbox ...

---

