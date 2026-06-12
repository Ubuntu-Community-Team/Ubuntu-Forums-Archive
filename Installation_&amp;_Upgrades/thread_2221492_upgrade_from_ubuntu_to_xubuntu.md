---
title: "upgrade from ubuntu to xubuntu"
date: 2014-05-02
forum: Installation &amp; Upgrades
---

### Post by cmcanulty on 2014-05-02
I am running ubuntu classic 12.04 and would like to install xubuntu 14.04 from the DVD and keep my current home as I have a lot of tweaks (it is on a separate partition). Will this work and if so should I do anything special before the upgrade? Thanks

---

### Post by ajgreeny on 2014-05-02
It should work OK without too many difficulties.  Just be on your guard for a few minor version and DE difficulties when you go from gnome in 12.04 (I presume) to xfce4 in Xubuntu 14.04, and a clean install is called for rather than an upgrade online as you can not upgrade to a different DE.

You may need to remove a config folder or two that relate to the classic desktop in your old /home partition, but I suspect it will all work fine.

Choose "Something else" at the partitioning stage of installing, reuse your old root partition as ext4, make / as mountpoint for the new root partition and select the format box.
Also reuse the old /home partition selecting ext4 with /home as themountpoint, but this time DO NOT SELECT the format box or all your files and folders will be gone.  You should always backup everything anyway, just in case.

Make sure you have the same username and you should then have no problems with permissions or ownership of your /home files and folders.

---

### Post by cmcanulty on 2014-05-02
OK  thanks I understand all the partitioning aspects but not sure how to locate the proper config files to remove

---

### Post by ajgreeny on 2014-05-02
I would start by just going ahead and trying without removing any configs from home. I suspect there will be no real problems between gnome classic and xfce4, both gtk based, and I think many users have both DEs on their machines without a problem.

---

