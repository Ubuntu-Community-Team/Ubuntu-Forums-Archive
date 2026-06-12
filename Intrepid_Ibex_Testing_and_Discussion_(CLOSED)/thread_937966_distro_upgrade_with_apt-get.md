---
title: "distro upgrade with apt-get?"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rkleemann on 2008-10-04
Hi,

I'm currently running Ubuntu 8.0.4 and I see that Intrepid 8.10 is not too far from release.

Is there an easy way to do a version upgrade?

The apt-get manpage isn't quite clear about the dist-upgrade command. Is that meant to be used for upgrading to a new distro version, or only upgrades within the current version?

Is this type of upgrade only doable via booting with the cdrom?

---

### Post by ww711 on 2008-10-04
'easy way' - via Internet.

In order to update the repositories, use this command:
sudo apt-get update

Use this command if you want to upgrade the packages of the currently installed version:
sudo apt-get upgrade

If you want to upgrade to the newest version of Ubuntu, use this command:
sudo apt-get dist-upgrade

---

### Post by rkleemann on 2008-10-04
> **ww711 said:**
> 'easy way' - via Internet.

In order to update the repositories, use this command:
sudo apt-get update

Use this command if you want to upgrade the packages of the currently installed version:
sudo apt-get upgrade

If you want to upgrade to the newest version of Ubuntu, use this command:
sudo apt-get dist-upgrade

Thanks.

So dist-upgrade actually does perform a full distro version upgrade?

Is it safe to use in a production server?

---

### Post by bodhi.zazen on 2008-10-04
See this thread for upgrading :

[http://ubuntuforums.org/showthread.php?t=936696](http://ubuntuforums.org/showthread.php?t=936696)

Also please keep in mind it 8.10 is still in Beta , so there are no guarantees this will work.

---

