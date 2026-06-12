---
title: "Recovering MBR after a win XP installation"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by linkxs on 2008-04-05
i used to ahve a nice dual boot, 10gb win xp, 10gb linux(ubuntu 7.04). then, i ahd to reainstall windows, and apparently forgot that MBR will get destroyed. now i have just windows, but with access to my raiser fs linux partition. can someone help please?

---

### Post by tamoneya on 2008-04-05
pop in the ubuntu live cd and reinstall grub into the MBR with ```
sudo grub
```.  Then once you are back in ubuntu go to work editing your /boot.grub/menu.lst file as necessary.

---

### Post by zvacet on 2008-04-05
[Here](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

