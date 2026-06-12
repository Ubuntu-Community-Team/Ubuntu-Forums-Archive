---
title: "Help with some upgrades/addons after Lubuntu install"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by Joe Ker1086 on 2011-01-06
Ok, Let me just start by saying that I did not have internet access when I loaded a fresh install of lubuntu on my laptop. Now, when I try to go to sites I am missing plugins and having other small problems that I know are related to not having an active internet connect5ion when I did the load. Is there an easy way to install/upgrade everything that should have/would have installed if I had an active internet connection?

---

### Post by tommcd on 2011-01-06
Not having an internet connection should not have any deleterious effects on installing L/Ubuntu. You will still get a full install. You will just need to get the updates after you finish the install and have an active internet connection.
To make sure your system is up to date, open a terminal and run:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
After the updates finish installing you will be fully up to date.
As for plugins for internet browsing, you may need to install flash, java, and the multimedia codecs. To get the *sun-java6* packages, enable the Canonical Partners repo in the Software Sources in Synaptic.
Write back if you need more help. I am also using Lubuntu 10.10 (which is much lighter and faster than a full on Ubuntu btw).

---

### Post by Joe Ker1086 on 2011-01-06
Thanks for the quick response! Yes I have noticed how much faster Lubuntu is in comparison to Ubuntu and I love the simplicity. I had it installed before but I reallllllllly was screwing with some files trying to get my vpn working and ended up causing some major issues. Easiest thing to do was reinstall everything :) I will get back to you if I have any problems.

---

### Post by tommcd on 2011-01-06
> **Joe Ker1086 said:**
>  I had it installed before but I reallllllllly was screwing with some files trying to get my vpn working and ended up causing some major issues. ...
You really should backup any configuration files before you end up "*screwing with some files*". This will save you a lot of grief if you ever need to undo the problems that you have caused. I *always* backup any configuration file before I edit them. I also never screw with configuration files unless I know *exactly* what I am doing. 
This is how I avoid problems.

---

