---
title: "Package manager says program running?"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by justinclark on 2007-11-18
Ok so I have ubuntu 7.10.  Im trying to install some programs but when the package installer opens it says Only one synaptic allowed to run at one time please close other app.    The prob is I cant find an open one.  Any help?

---

### Post by jfinkels on 2007-11-18
Make sure you have closed "Add/Remove Applications", "Synaptic", all instances of a terminal using "aptitude" or "apt-get", etc. To find out if an instance of Synaptic or aptitude is running, open a terminal ("Applications > Accessories > Terminal") and type the following:```
ps ax | grep apt
```This will show you a list of running processes with the string "apt" in the name. To kill a running process (for example, if it is frozen or if you can't find it), type ```
kill -9 *###*
``` where *###* is the number of the process, as given by the previous command.

---

### Post by kyphi on 2007-11-19
If you have a little orange asterisk symbol on your top panel near your loudspeaker icon then Synaptic Update Manager is running.

Download your updates and then resume your downloading activities in Synaptic.

---

### Post by Benses on 2007-11-19
Another quick way of fixing this issue it to reboot/logout.

---

