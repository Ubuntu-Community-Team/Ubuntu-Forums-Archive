---
title: "Can I Upgrade Both Gnome &amp; KDE with Alternate CDs on the One System?"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by OzzyFrank on 2008-04-29
OK, I'm quite familiar with upgrading Ubuntu with the Alternate CD, and of adding discs to Software Sources to be used as repositories. However, now that I have both Gnome and KDE on the one system, when I go to upgrade with either disc, the other 500-600Mb starts being downloaded. I've added both discs as software sources but they are both overlooked when hitting the Upgrade button in Update Manager, which I didn't expect. When I insert an Alternate CD and select to start the package manager, that works, but the other disc is still overlooked.

So how can I get both Ubuntu/Gnome and Kubuntu/KDE updated with both the Ubuntu and Kubuntu Alternate CDs, to save all that needless downloading (since I already have all the files)?

Cheers

---

### Post by lemming465 on 2008-05-05
I had the same situation.   I just copied all of the .deb files off the CD's into /var/cache/apt/archives, and that prevented the extraneous downloads.  Something like
```
find /media/cdrom -type f -name "*.deb" -exec cp "{}" /var/cache/apt/archive/ \;
``` did it.

---

### Post by aysiu on 2008-05-05
Paste these commands into the terminal: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.online
sudo apt-cdrom add
sudo apt-get update
sudo apt-get dist-upgrade
sudo mv /etc/apt/sources.list /etc/apt/sources.list.firstcd
sudo apt-cdrom add
sudo apt-get update
sudo apt-get dist-upgrade
sudo mv /etc/apt/sources.list /etc/apt/sources.list.secondcd
sudo mv /etc/apt/sources.list.online /etc/apt/sources.list
sudo apt-get update
```

---

