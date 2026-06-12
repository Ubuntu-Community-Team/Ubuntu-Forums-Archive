---
title: "**confused"
date: 2006-04-07
forum: Installation &amp; Upgrades
---

### Post by robTard on 2006-04-07
So I'm confused, I downloaded .iso of Dapper Drake 6.06 beta (or pre) regardless, and I installed Dapper.  Everything went fine...  Then when I rebooted my system no GUI launched (gnome was absent).  I was logged into dapper drake but there was no gui, is this supposed to be like this?

---

### Post by K.Mandla on 2006-04-07
Nope. Something's not right. Can you tell us more about your hardware? If no GUI came up, it might be some kind of video driver problem.

---

### Post by Sutekh on 2006-04-07
[QUOTE=robTard]So I'm confused, I downloaded .iso of Dapper Drake 6.06 beta (or pre) regardless, and I installed Dapper.  Everything went fine...  Then when I rebooted my system no GUI launched (gnome was absent).  I was logged into dapper drake but there was no gui, is this supposed to be like this?[/QUOTE]
Did you happen to perform a server installation (or an expert one)

If you can log into the command line, it kind of sounds like the installation was complete but didn't install the desktop environment (GNOME)

You can make sure that it is installed using the command```
sudo apt-get install ubuntu-desktop
``` - when asked for a password use the one for your user

If this installs, great.  If it says ubuntu-desktop already newest version also great.  If you get any errors please post them here.

Then use this code to start the GNOME Display Manager (GDM - controls how you login, etc)
```
sudo /etc/init.d/gdm restart
```

---

