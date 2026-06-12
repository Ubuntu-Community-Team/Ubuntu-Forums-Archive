---
title: "Resume Upgrade From Console"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by Gibran on 2007-04-25
Hello everyone. When I was upgrading to Feisty there was a power failure and now X server will not boot, but I still have access to the console. I was wondering if there is a way to resume the upgrade/repair the system from the console so that I won't have to do a clean install. Thanks!

---

### Post by zvacet on 2007-04-26
```
sudo aptitude  dist-upgrade
```

---

### Post by Gibran on 2007-04-26
Aw, shucks! Well, I made a clean install...which might not be a bad thing considering I had Ubuntu Ultimate and it was rather bloated with apps I don't need. Thank you!

---

### Post by Death_Sargent on 2007-04-26
Resumming a Distro upgrade is almost always a great way to make a very broken install

I find that its best to plan the hell out of the upgrade.

Make sure the weather is decent, make sure your not going to be running into the time of night where drunks are driving, make sure that your wired as wireless can sometimes fail or transmit bad packets. and finally make scripts or programs that will allow for you to use the command line to update.

I did this once from the console

Ctrl+alt+f1 and as root i launched the nm-applet

Ctrl+alt+f2 and as another root login I began repairs with a working WIFI net connection.

However that was just because gnome, gdm, kde and kdm, had all become corrupted so i had to install xfce to get a graphical login from where i reinstalled gnome. 

Also you may wan't to look into removing dash now that you have upgraded as Feisty automatically reinstalls it

---

