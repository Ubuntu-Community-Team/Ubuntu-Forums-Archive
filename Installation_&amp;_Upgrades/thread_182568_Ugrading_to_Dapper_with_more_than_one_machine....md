---
title: "Ugrading to Dapper with more than one machine..."
date: 2006-05-26
forum: Installation &amp; Upgrades
---

### Post by cabbage on 2006-05-26
Dear all,

I have a couple of machines at home running Breezy. I've read the wiki article on upgrading and thats all fine for a single box, but as I only have slow Internet access is there a clever or easy way to download Dapper just once, and upgrade both machines?

On a related theme, is the upgrade process sufficiently tried and tested that a fresh install is no longer recommended?


Thanks...

---

### Post by aysiu on 2006-05-26
The closer your Ubuntu installation is to a default configuration, the more likely the upgrade will be flawless. At the very least, you should have the appropriate metapackage installed before you upgrade.

For example, if you are using Gnome, you should have *ubuntu-desktop* installed before you upgrade. If you're using KDE, *kubuntu-desktop*; XFCE, *xubuntu-desktop*.

You can have combinations, too. For example, if you have both Gnome and KDE, you should do this **before** you upgrade to Dapper: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop ubuntu-desktop
```

The best way to get Dapper only once is to download and burn the Dapper Text-Mode Installer CD (**not** the live/installer CD, which cannot be used for upgrades). Then go to Synaptic Package Manager > Edit > Add CD-ROM, then Settings > Repositories and uncheck all the online repository sources so that the CD-ROM is the only source available.

To make it more likely that your upgrade is successful, log out of your session, press Control-Alt-F1, log in, and type ```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/kdm stop
sudo aptitude update
sudo aptitude dist-upgrade
sudo reboot
```

---

