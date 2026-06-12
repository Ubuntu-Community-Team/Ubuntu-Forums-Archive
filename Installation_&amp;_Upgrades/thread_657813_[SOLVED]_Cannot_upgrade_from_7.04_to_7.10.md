---
title: "[SOLVED] Cannot upgrade from 7.04 to 7.10"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by mcseifert on 2008-01-04
I have tried both network and the alternate upgrade methods. The end result of both is getting the following message:

"Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs"
 
I have tried sudo apt get update and sudo apt-cdrom, and enn in my cd-rom when upgrading, but it doed up with the same meromssage when I try to run update manager.I have put a copy of feisty fawn in my cd-rom, but the upgrade won't read the cdrom in the driive.

What am I doing wrong???

Any help would be greatly appreciated

---

### Post by ~LoKe on 2008-01-04
```
gksu gedit /etc/apt/sources.list
```
Comment out the CD rom line.
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

