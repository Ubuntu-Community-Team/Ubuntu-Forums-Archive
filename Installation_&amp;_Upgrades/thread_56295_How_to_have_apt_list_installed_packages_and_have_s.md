---
title: "How to have apt list installed packages and have some logging"
date: 2005-08-12
forum: Installation &amp; Upgrades
---

### Post by nonutopia on 2005-08-12
apt-get is the main reason i changed my distro from slackware to ubuntu.. Think its just great. Only when i'm too maintain any installation of ubuntu I need to find out what kind of crap i installed on my once clean OS. So my question is how can apt tell me what packages are installed? 
And also can i configure apt that it will log installed or updated packages? this will really help when moving to an auto update construction on my sarge dmz server. 

Thanks in advance!

EDIT: aptitute is the way to go it seems. it does log. it probably updates just a nicely then apt-get. And its console based allowing me to use it on my server. And I can play minesweeper when im bored :)
But I keep having the problem that i want to compare a list of installed packages with a list of packages from an out of the box installation so I can see what i can remove to get a cleaner disk. So is there anyway to export the list of apt? Or is there a nice list of packages somewhere in /var orso?

---

### Post by blind0wl on 2005-08-12
Id have to look into it more for the logging of installation but you can type in a console:

```
apt-cache pkgnames
```

This will list all packages installed on the system

*EDIT - Typo

---

### Post by nonutopia on 2005-08-12
apt-cache.. right I should have guessed that :)  thanks a lot!

edit: man apt-cache to the rescue.. small typo it should be 'apt-cache pkgnames' and it works great! thnx again.

---

### Post by blind0wl on 2005-08-12
Opps...your right...

---

