---
title: "version parameter isn't provided during update"
date: 2024-09-30
forum: Installation &amp; Upgrades
---

### Post by adry31 on 2024-09-30
dear all,

I have a preinstalled package of our software on Ubuntu 20.04.2 LTS.
The installed version is a 8.0.0-1440, when I try to install a new version 8.0.0-1489  with the following command "sudo apt install  mypackage_8.0.0-1489-amd64.deb"
the preinst script is launch, 2 parameters are correctly provided:
 $1 -> upgrade
$2 -> 8.0.0-1440

but when the postinst script is executed, only
 $1 -> configure

si provided and I don't have $2 parameter where I expected to get the new version for example 8.0.0-1489

anybody know why the version is not correctly provided ? (same thing with sudo apt upgrade)

And if I use " dpkg-deb -I mypackage_8.0.0-1489-amd64.deb"  the version is correctly set to 8.0.0-1489

Does anybody have an idea of the problem why the version isn't provided in the postinst script plz ?

bellow the screen

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294321&stc=1[/IMG]

bellow the calling in debug:
execve("/var/lib/dpkg/info/keycloak-mysoftware.postinst", ["/var/lib/dpkg/info/keycloak-mysof"..., "configure", ""], 0x55b6d12e1ae0 /* 23 vars */) = 0




113400 execve("/var/lib/dpkg/tmp.ci/preinst", ["/var/lib/dpkg/tmp.ci/preinst", "upgrade", "8.0.0-1440", "8.0.0-1489"], 0x55b6d1494fb0 /* 23 vars */) = 0

Thank a lot
 Adrien

---

