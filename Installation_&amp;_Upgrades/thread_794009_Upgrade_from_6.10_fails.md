---
title: "Upgrade from 6.10 fails"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by Jahoobie on 2008-05-14
I am a complete newb to the world of Ubuntu, but I am hooked...

However, I am trying to upgrade from 6.10 to 8.04 using the CLI on a server.  (No GUI installed).  Whenever I do a do-release-upgrade -d I starts to look, then errors out with:

Error during update
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/dists/edgy/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/dists/edgy/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

What I don't get is, when I do a lsb_release -a, I am on version 6.10, so why would it fail looking for 6.06.1 on a CDROM?  Is it possible to exclude the CDROM?  Or what exactly am I doing wrong?

I have also done apt-get install upgrade
apt-get install update
and apt-get install dist-upgrade.

Any help would be appreciated.

---

### Post by Partyboi2 on 2008-05-14
open up your sources.list
```
sudo nano /etc/apt/sources.list
``` and put a # infront of the line starting with deb cdrom....
Then after you have saved the changes
```
 sudo apt-get update
```

---

### Post by Jahoobie on 2008-05-14
EXCELLENT!  Thank you!

Nothing like easy answers for newbies!

---

