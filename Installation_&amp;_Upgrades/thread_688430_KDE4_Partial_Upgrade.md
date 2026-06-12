---
title: "KDE4 Partial Upgrade"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by 7llusion on 2008-02-05
I know what a partial upgrade is but the problem is that I installed kde4 tot test it.
Now update manager tells me that KDE 4.0.1 is out, but since the 
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main
repo doesn't have any gpg key, the upgrade fails.
Any way around this, or is there actually a hidden gpg key somewhere?

---

### Post by craigo_69 on 2008-02-29
Had exactly the same problem after installing KDE4 on Ubuntu 7.10 too. 

I used the command line:
    apt-get dist-upgrade

It warned me that "The following packages cannot be authenticated!", and then the update completed successfully.

Cheers,
Craig

---

