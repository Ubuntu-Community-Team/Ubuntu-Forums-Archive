---
title: "Can't install kubuntu-desktop prior to dist-upgrade"
date: 2006-09-17
forum: Installation &amp; Upgrades
---

### Post by pressman57 on 2006-09-17
Hi, I'm following a guide to upgrading from breezy to dapper, but when I try " sudo aptitude install kubuntu-desktop" it spits out:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: kaddressbook but it is not installable
                   Depends: kdepim-wizards but it is not installable
                   Depends: kmail but it is not installable
                   Depends: kontact but it is not installable
                   Depends: korganizer but it is not installable

I thought at first it could be my sources.list so I replaced it with a "clean" list I got off of [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php). Same error.

Any help would be most welcome. I've searched and searched....

---

### Post by aysiu on 2006-09-17
After you updated your sources.list, did you run this command ```
sudo aptitude update
``` before doing ```
sudo aptitude install kubuntu-desktop
```?

---

### Post by pressman57 on 2006-09-17
Yep I did that - also "apt-get install -f" I found somewhere. Will this problem break kde after the upgrade or should I just do it?
 Thanks for the reply

---

### Post by aysiu on 2006-09-17
I think if you're having a problem now, the upgrade will make it only worse.

So *sudo apt-get -f install* didn't fix the broken package. This problem may be way out of my league...

---

