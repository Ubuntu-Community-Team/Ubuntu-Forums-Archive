---
title: "Quick question about reinstall"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by raghav_p on 2005-10-16
When I installed Hoary many moons ago, I kept my home directory on another partition. My question is, if I should remove hoary and start with a fresh breezy, would **most** of the settings remain the same or would there be a lot of conflicts? I know that I installed the OpenOffice.org2 beta from the site using alien. Does anybody know if that would hurt compatability? And what about Firefox settings?

Thanks

---

### Post by adwait on 2005-10-16
Most of the user settings are in the /home/$USER folder, so if you retain that......MOST of your settings will be fine including Firefox.

---

### Post by azteech on 2005-10-16
[quote=raghav_p]When I installed Hoary many moons ago, I kept my home directory on another partition. My question is, if I should remove hoary and start with a fresh breezy, would **most** of the settings remain the same or would there be a lot of conflicts? I know that I installed the OpenOffice.org2 beta from the site using alien. Does anybody know if that would hurt compatability? And what about Firefox settings?

Thanks[/quote] 
IMHO, the path to follow (upgrade, or fresh install) depends on each individual(s) preference. One determining factor might depend on weither you have issues with Hoary which you want to correct. If you have issues, then I would recommend a clean install. If you do not, then recommend following the upgrade/dist-upgrade path.

As for conflicts, this also depends on what packages you have installed and, wheither there is a Breezy port made for those packages (some have not been updated/placed in the repositories as of yet). It also depends on your system. All you have to do is to look at this forum, to see that some have had problems, where others have not. 

I have two systems on which I am running Breezy. On one, I did a clean install - on the other I did a upgrade/dist-upgrade. Both went well. On the one system where I did a clean install, my choice was simply driven by the fact that I only had Hoary installed for a short period and felt I would not lose anything by doing a fresh install.

Regardless of the path you choose, if you have any data you want to preserve, or custom settings made to your system OS/installed packages, recommend doing a backup of your home directory at the least, and/or a full backup your system, just in case you run into problems.

---

